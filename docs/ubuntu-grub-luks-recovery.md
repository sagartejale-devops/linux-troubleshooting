# Ubuntu GRUB + LUKS + LVM Recovery

## Issue

System booted into GRUB shell after reboot.

## Symptoms

- GRUB rescue prompt
- Unable to boot Ubuntu
- Password expiry issue
- initramfs errors

## Environment

- Ubuntu 24.04
- LUKS Encryption
- LVM Partitioning

## Troubleshooting Steps

### 1. Identified partitions
```bash
ls
ls (hd0,gpt2)
```

### 2. Booted using Live USB

### 3. Opened encrypted partition

```bash
sudo cryptsetup luksOpen /dev/nvme0n1p3 cryptroot
```

### 4. Activated LVM

```bash
sudo vgscan
sudo vgchange -ay
```

### 5. Mounted partitions

```bash
sudo mount /dev/ubuntu-vg/ubuntu-lv /mnt
```

## Root Cause

GRUB and boot partition inconsistency along with expired account password.

## Resolution

- Password reset
- GRUB update
- Boot partition correction
- EFI mount correction

## Learning Outcome

- Better understanding of:
  - GRUB
  - LUKS
  - LVM
  - chroot recovery
  - EFI boot process
