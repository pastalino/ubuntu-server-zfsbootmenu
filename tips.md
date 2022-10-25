# tips to script

## zfs mirror 2 disk
vir-manager kvm vm

won't boot to refind
it'll boot to efi shell

### efi shell
`map` listing all devices
`fs0:` switching to device fs0
`EFI\refind\refind_x64.efi` boot to refind

### efibootmgr
`sudo efibootmgr --verbose` list all entries verbosely
`sudo efibootmgr -c -d /dev/disk/by-id/virtio-zfs-mirror-disk2-part1 -l "\EFI\refind\refind_x64.efi" -L "rEFInd-disk2"`
+ create new entry to efiboot
+ for device /dev/disk/by-id/virtio-zfs-mirror-disk2-part1
+ path to efi must be in windows path notation ("\") "\EFI\refind\refind_x64.efi" even though it is located in /boot/efi/EFI/refind/refind_x64.efi
+ label entry "rEFInd-disk2"
`sudo efibootmgr -B -b 0002` delete entry 0002
`sudo efibootmgr -o 2,1,3,0,4` change boot oder to 2,1,3,0,4
+ Boot0000: UiApp
+ Boot0001: UEFI Misc Device
+ Boot0002: rEFInd-disk2
+ Boot0003: UEFI Misc Device 2
+ Boot0004: EFI Internal Shell

## links

### zfsbootmenu
- https://github.com/zbm-dev/zfsbootmenu/wiki/Void-Linux----Single-disk-syslinux-MBR
- https://zfsbootmenu.org/

### dracut
- https://github.com/dracutdevs/dracut

### ubuntu-server-zfsbootmenu
- https://github.com/Sithuk/ubuntu-server-zfsbootmenu
