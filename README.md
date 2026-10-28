# Media Server Linux kernel builder

Reproducible GitHub Actions builder for a **generic x86_64 kernel intended for the family media server** . It builds upstream Linux 7.3 as Debian packages, using the server's Ubuntu HWE 7.0 configuration as the baseline.

## Important

- This is **not** an Ubuntu-supported kernel. It is an upstream kernel packaged as `.deb` files.
- The workflow does not install anything automatically. Download and inspect the artifacts, then install alongside the existing Ubuntu kernels.
- The Ubuntu kernels remain the rollback path.
- Kernel modules that depend on the exact Ubuntu ABI may need DKMS rebuilding after installation.
- The checked-in config contains hardware/features, not credentials. Never add `/etc`, SSH keys, provider credentials, or `.env` files.

## Build

1. Open **Actions → Build Linux kernel → Run workflow**.
2. Use the default `7.3` or enter another upstream tag.
3. Download the `.deb` artifacts from the completed run.
4. Verify checksums and inspect the package contents before installing.

The workflow builds:

- kernel image
- kernel headers
- kernel modules
- debug image package

## Target baseline

- Target: generic x86_64 media server
- Architecture: x86_64
- Baseline config: Ubuntu `7.0.0-42-generic`
- Intended uses: Docker/overlayfs, mergerfs/FUSE, Tailscale, ZeroTier, WireGuard/TUN, DKMS, media hardware acceleration, ext4, btrfs, and common networking/storage drivers.
