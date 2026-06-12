---
title: "Problems with sd card reader laptop."
date: 2011-05-28
forum: New to Ubuntu
---

### Post by guilleme on 2011-05-28
Hi all. I've got a little problem. I have two laptop computers with ubuntu installed, and on neither I can use the integrated card reader. The first one is a AOD255 acerbic netbook. The second one is a Dell xps 1250 notebook. They both have ubu. 10.10 installed. I can use both card readers when booting into windows, but none work at all in ubuntu. 
Thanks if anyone can help.

---

### Post by webofunni on 2011-05-28
are you able to see the reader in 

```

hwinfo

```

?

---

### Post by guilleme on 2011-05-28
I believe not, unless I'm missing something. 
I will upload the results from hwinfo as a text-file along with this post. 
I can't see the device on the "device manager" program either. 
Thanks for the time.

---

### Post by guilleme on 2011-05-28
Done uploading :).

---

### Post by webofunni on 2011-05-29
where is it. Put the result in \[CODE\] tag

---

### Post by MoebusNet on 2011-05-29
> **guilleme said:**
> Hi all. I've got a little problem. I have two laptop computers with ubuntu installed, and on neither I can use the integrated card reader. The first one is a AOD255 acerbic netbook. The second one is a Dell xps 1250 notebook. They both have ubu. 10.10 installed. I can use both card readers when booting into windows, but none work at all in ubuntu. 
Thanks if anyone can help.

I don't know about the Dell, but my Acer Aspire One D255-2301 needs a kernel 2.6.37.7 or newer to be able to recognize my SD card reader. Lubuntu 11.04 recognizes my card reader perfectly. You might want to download a version of 11.04, put it on a flash drive as a Live-USB, boot it up, and see if your card reader works. If so, you may want to consider a newer version of Ubuntu. It works for me (I'm not going to do an hdd install).

---

### Post by guilleme on 2011-05-29
> **webofunni said:**
> where is it. Put the result in \[CODE\] tag

Sorry, closed the window I was using before I sent the reply... My bad.
```
============ start debug info ============
libhd version 16.0u (ia32)
using /var/lib/hardware
kernel version is 2.6
----- /proc/cmdline -----
  BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=58682f5c-0155-4154-adff-b3bdd58cc626 ro quiet splash
----- /proc/cmdline end -----
debug = 0xff7ffff7
probe = 0x00138fc4aa17fcf9fffe (+memory +pci +isapnp +net +floppy +misc +misc.serial +misc.par +misc.floppy +serial +cpu +bios +monitor +mouse +scsi +usb -usb.mods +modem +modem.usb +parallel +parallel.lp +parallel.zip -isa -isa.isdn +isdn +kbd +prom +sbus +int +braille +braille.alva +braille.fhp +braille.ht -ignx11 +sys -bios.vbe -isapnp.old -isapnp.new -isapnp.mod +braille.baum -manual +fb +pppoe -scan +pcmcia -fork -parallel.imm +s390 -cpuemu -sysfs -s390disks +udev +block +block.cdrom +block.part +edd +edd.mod -bios.ddc -bios.fb -bios.mode +input +block.mods +bios.vesa -cpuemu.debug -scsi.noserial +wlan -bios.crc -hal -bios.vram -bios.acpi -bios.ddc.ports -modules.pata -net.eeprom -x86emu -max -lxrc)
shm: attached segment 23166995 at 0xb77f3000
>> hal.1: read hal data
  hal: connected to: :1.124
----- hal device list -----
  0: udi = '/org/freedesktop/Hal/devices/volume_uuid_0A728F44728F340B'
  volume.mount_point = ''
  volume.is_mounted = false
  volume.is_mounted_read_only = false
  volume.linux.is_device_mapper = false
  block.major = 8 (0x8)
  block.minor = 3 (0x3)
  block.is_volume = true
  volume.partition.number = 3 (0x3)
  linux.hotplug_type = 3 (0x3)
  volume.num_blocks = 220000000ull (0xd1cef00ull)
  volume.block_size = 512 (0x200)
  volume.is_partition = true
  volume.size = 112640000000ull (0x1a39de0000ull)
  volume.partition.start = 14064549888ull (0x346500000ull)
  volume.partition.media_size = 250059350016ull (0x3a38b2e000ull)
  volume.ignore = false
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' }
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' }
  block.device = '/dev/sda3'
  info.product = 'Acer'
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_0A728F44728F340B'
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' }
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' }
  volume.mount.valid_options = { 'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detach', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover' }
  volume.unmount.valid_options = { 'lazy' }
  volume.is_disc = false
  volume.mount.ntfs.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8' }
  volume.unmount.ntfs.valid_options = { 'lazy' }
  volume.policy.mount_filesystem = 'ntfs-3g'
  volume.fstype.alternative = 'ntfs'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda3'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB'
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' }
  info.category = 'volume'
  info.capabilities = { 'volume', 'block' }
  volume.fstype = 'ntfs-3g'
  volume.fsusage = 'filesystem'
  volume.fsversion = ''
  volume.uuid = '0A728F44728F340B'
  volume.label = 'Acer'

  1: udi = '/org/freedesktop/Hal/devices/volume_uuid_b6a0eae2_ce1c_4ce0_9831_085826248369'
  volume.mount_point = '/home'
  volume.is_mounted = true
  volume.is_mounted_read_only = false
  volume.linux.is_device_mapper = false
  block.major = 8 (0x8)
  block.minor = 4 (0x4)
  block.is_volume = true
  volume.partition.number = 4 (0x4)
  linux.hotplug_type = 3 (0x3)
  volume.num_blocks = 238280704ull (0xe33e000ull)
  volume.block_size = 512 (0x200)
  volume.is_partition = true
  volume.size = 121999720448ull (0x1c67c00000ull)
  volume.partition.start = 126704680960ull (0x1d80300000ull)
  volume.partition.media_size = 250059350016ull (0x3a38b2e000ull)
  volume.ignore = false
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' }
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' }
  block.device = '/dev/sda4'
  info.product = 'Volume (ext3)'
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_b6a0eae2_ce1c_4ce0_9831_085826248369'
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' }
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' }
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'acl', 'user_xattr', 'data=' }
  volume.unmount.valid_options = { 'lazy' }
  volume.is_disc = false
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda4'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB'
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' }
  info.category = 'volume'
  info.capabilities = { 'volume', 'block' }
  volume.fstype = 'ext3'
  volume.fsusage = 'filesystem'
  volume.fsversion = '1.0'
  volume.uuid = 'b6a0eae2-ce1c-4ce0-9831-085826248369'
  volume.label = ''

  2: udi = '/org/freedesktop/Hal/devices/volume_uuid_d7a9a922_eb3e_4c30_88d4_d026e9cb1c67'
  block.major = 8 (0x8)
  block.minor = 2 (0x2)
  block.is_volume = true
  linux.hotplug_type = 3 (0x3)
  volume.partition.number = 2 (0x2)
  volume.block_size = 512 (0x200)
  volume.is_partition = true
  volume.linux.is_device_mapper = false
  volume.partition.start = 248705449984ull (0x39e8000000ull)
  volume.num_blocks = 2643968ull (0x285800ull)
  volume.size = 1353711616ull (0x50b00000ull)
  info.category = 'volume'
  info.capabilities = { 'volume', 'block' }
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_d7a9a922_eb3e_4c30_88d4_d026e9cb1c67'
  volume.partition.media_size = 250059350016ull (0x3a38b2e000ull)
  info.product = 'Volume (swap)'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB'
  volume.fstype = 'swap'
  volume.fsusage = 'other'
  volume.fsversion = '2'
  volume.uuid = 'd7a9a922-eb3e-4c30-88d4-d026e9cb1c67'
  volume.label = ''
  volume.mount_point = ''
  volume.is_mounted = false
  volume.is_mounted_read_only = false
  block.device = '/dev/sda2'
  volume.is_disc = false

  3: udi = '/org/freedesktop/Hal/devices/volume_uuid_58682f5c_0155_4154_adff_b3bdd58cc626'
  volume.mount_point = '/'
  volume.is_mounted = true
  volume.is_mounted_read_only = false
  volume.linux.is_device_mapper = false
  block.major = 8 (0x8)
  block.minor = 1 (0x1)
  block.is_volume = true
  volume.partition.number = 1 (0x1)
  linux.hotplug_type = 3 (0x3)
  volume.num_blocks = 27467776ull (0x1a32000ull)
  volume.block_size = 512 (0x200)
  volume.is_partition = true
  volume.size = 14063501312ull (0x346400000ull)
  volume.partition.start = 1048576ull (0x100000ull)
  volume.partition.media_size = 250059350016ull (0x3a38b2e000ull)
  volume.ignore = false
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' }
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' }
  block.device = '/dev/sda1'
  info.product = 'Volume (ext3)'
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_58682f5c_0155_4154_adff_b3bdd58cc626'
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' }
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' }
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'acl', 'user_xattr', 'data=' }
  volume.unmount.valid_options = { 'lazy' }
  volume.is_disc = false
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB'
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' }
  info.category = 'volume'
  info.capabilities = { 'volume', 'block' }
  volume.fstype = 'ext3'
  volume.fsusage = 'filesystem'
  volume.fsversion = '1.0'
  volume.uuid = '58682f5c-0155-4154-adff-b3bdd58cc626'
  volume.label = ''

  4: udi = '/org/freedesktop/Hal/devices/computer'
  power_management.is_powersave_set = false
  info.callouts.add = { 'hal-storage-cleanup-all-mountpoints' }
  info.addons = { 'hald-addon-cpufreq', 'hald-addon-acpi' }
  info.capabilities = { 'cpufreq_control' }
  info.subsystem = 'unknown'
  info.product = 'Computer'
  info.udi = '/org/freedesktop/Hal/devices/computer'
  org.freedesktop.Hal.version = '0.5.14'
  org.freedesktop.Hal.version.major = 0 (0x0)
  org.freedesktop.Hal.version.minor = 5 (0x5)
  org.freedesktop.Hal.version.micro = 14 (0xe)
  system.kernel.name = 'Linux'
  system.kernel.version = '2.6.35-28-generic'
  system.kernel.version.major = 2 (0x2)
  system.kernel.version.minor = 6 (0x6)
  system.kernel.version.micro = 35 (0x23)
  system.kernel.machine = 'i686'
  power_management.can_suspend = true
  power_management.can_suspend_hybrid = true
  power_management.can_hibernate = true
  system.hardware.primary_video.vendor = 32902 (0x8086)
  system.hardware.primary_video.product = 40977 (0xa011)
  system.hardware.serial = 'LUSEY0D0441023D40C1601'
  system.hardware.uuid = '9CE64E36-829C-B19C-2111-1C7508BA166C'
  system.board.serial = 'Base Board Serial Number'
  system.firmware.vendor = 'Acer'
  system.firmware.version = 'V3.13(DDR3)'
  system.firmware.release_date = '12/23/2010'
  system.hardware.vendor = 'Acer'
  system.hardware.product = 'AOD255E'
  system.hardware.version = 'V3.13(DDR3)'
  system.chassis.manufacturer = 'Acer'
  system.board.product = 'JE02_PT'
  system.board.version = 'V3.13(DDR3)'
  system.board.vendor = 'Acer'
  system.chassis.type = 'Notebook'
  system.formfactor = 'laptop'
  power_management.quirk.dpms_on = true
  power_management.quirk.vbestate_restore = true
  power_management.quirk.vbemode_restore = true
  power_management.type = 'acpi'
  power_management.acpi.linux.version = '20100428'
  power_management.quirk.vbe_post = true
  info.interfaces = { 'org.freedesktop.Hal.Device.SystemPowerManagement', 'org.freedesktop.Hal.Device.CPUFreq' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = { 'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = { 'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save' }
  power_management.quirk.dpms_suspend = true
  power_management.quirk.vga_mode_3 = true
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = { 'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = { 'i', 'i', '', '', '', 'b' }

  5: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'
  linux.hotplug_type = 2 (0x2)
  button.state.value = false
  linux.subsystem = 'input'
  input.device = '/dev/input/event2'
  input.product = 'Lid Switch'
  button.has_state = true
  button.type = 'lid'
  info.addons.singleton = { 'hald-addon-input' }
  info.subsystem = 'input'
  info.product = 'Lid Switch'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2/event2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'
  info.category = 'input'
  info.capabilities = { 'input', 'input.switch', 'button' }
  linux.device_file = '/dev/input/event2'

  6: udi = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if0_video4linux'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'video4linux'
  info.subsystem = 'video4linux'
  info.product = '1.3M WebCam'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/video4linux/video0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if0'
  video4linux.version = '2'
  info.category = 'video4linux'
  info.capabilities = { 'video4linux', 'video4linux.video_capture' }
  info.udi = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if0_video4linux'
  linux.device_file = '/dev/video0'
  video4linux.device = '/dev/video0'

  7: udi = '/org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB'
  info.vendor = 'ATA'
  block.device = '/dev/sda'
  block.major = 8 (0x8)
  block.minor = 0 (0x0)
  block.is_volume = false
  storage.bus = 'pci'
  linux.hotplug_type = 3 (0x3)
  storage.no_partitions_hint = false
  storage.media_check_enabled = false
  storage.automount_enabled_hint = true
  storage.drive_type = 'disk'
  storage.model = 'TOSHIBA MK2565GS'
  storage.vendor = 'ATA'
  storage.serial = 'TOSHIBA_MK2565GSX_Z0A1B2BCB'
  storage.firmware_version = 'GJ002J'
  storage.lun = 0 (0x0)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'
  storage.removable.media_available = true
  storage.removable = false
  storage.size = 250059350016ull (0x3a38b2e000ull)
  info.product = 'TOSHIBA MK2565GS'
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB'
  storage.hotpluggable = false
  storage.requires_eject = false
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_scsi_device_lun0'
  storage.partitioning_scheme = 'mbr'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB'
  info.category = 'storage'
  info.capabilities = { 'storage', 'block' }
  storage.removable.media_size = 250059350016ull (0x3a38b2e000ull)

  8: udi = '/org/freedesktop/Hal/devices/acpi_FAN'
  linux.hotplug_type = 4 (0x4)
  linux.acpi_path = '/proc/acpi/fan/FAN'
  linux.acpi_type = 2 (0x2)
  fan.enabled = true
  info.product = 'Fan'
  info.udi = '/org/freedesktop/Hal/devices/acpi_FAN'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'fan'
  info.capabilities = { 'fan' }

  9: udi = '/org/freedesktop/Hal/devices/acpi_CPU0'
  linux.hotplug_type = 4 (0x4)
  linux.acpi_path = '/proc/acpi/processor/CPU0'
  linux.acpi_type = 1 (0x1)
  processor.number = 0 (0x0)
  processor.can_throttle = false
  info.product = 'Intel(R) Atom(TM) CPU N455   @ 1.66GHz'
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'processor'
  info.capabilities = { 'processor' }

  10: udi = '/org/freedesktop/Hal/devices/acpi_CPU1'
  linux.hotplug_type = 4 (0x4)
  linux.acpi_path = '/proc/acpi/processor/CPU1'
  linux.acpi_type = 1 (0x1)
  processor.number = 1 (0x1)
  processor.can_throttle = false
  info.product = 'Intel(R) Atom(TM) CPU N455   @ 1.66GHz'
  info.udi = '/org/freedesktop/Hal/devices/acpi_CPU1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'processor'
  info.capabilities = { 'processor' }

  11: udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/timer'
  alsa.type = 'timer'
  info.subsystem = 'sound'
  info.product = 'ALSA Timer Device'
  linux.sysfs_path = '/sys/devices/virtual/sound/timer'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  linux.device_file = '/dev/snd/timer'

  12: udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/seq'
  alsa.type = 'sequencer'
  info.subsystem = 'sound'
  info.product = 'ALSA Sequencer Device'
  linux.sysfs_path = '/sys/devices/virtual/sound/seq'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  linux.device_file = '/dev/snd/seq'

  13: udi = '/org/freedesktop/Hal/devices/net_0a_00_27_00_00_00'
  info.subsystem = 'net'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'net'
  info.interfaces = { 'org.freedesktop.Hal.Device.WakeOnLan' }
  net.originating_device = '/org/freedesktop/Hal/devices/computer'
  net.interface = 'vboxnet0'
  net.address = '0a:00:27:00:00:00'
  linux.sysfs_path = '/sys/devices/virtual/net/vboxnet0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  net.arp_proto_hw_id = 1 (0x1)
  net.linux.ifindex = 4 (0x4)
  info.category = 'net.80203'
  info.capabilities = { 'net', 'net.80203', 'wake_on_lan' }
  info.udi = '/org/freedesktop/Hal/devices/net_0a_00_27_00_00_00'
  org.freedesktop.Hal.Device.WakeOnLan.method_names = { 'GetSupported', 'GetEnabled', 'SetEnabled' }
  net.80203.mac_address = 10995770589184ull (0xa0027000000ull)
  info.product = 'Networking Interface'
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = { 'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable' }
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = { '', '', 'b' }
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = { '', '', 'enable' }

  14: udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'net'
  net.originating_device = '/org/freedesktop/Hal/devices/computer'
  net.interface = 'lo'
  net.address = '00:00:00:00:00:00'
  linux.sysfs_path = '/sys/devices/virtual/net/lo'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  net.arp_proto_hw_id = 772 (0x304)
  net.linux.ifindex = 1 (0x1)
  info.category = 'net.loopback'
  info.capabilities = { 'net', 'net.loopback' }
  info.udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  info.subsystem = 'net'
  info.product = 'Loopback device Interface'

  15: udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.interfaces = { 'org.freedesktop.Hal.Device.LaptopPanel' }
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'backlight'
  info.subsystem = 'backlight'
  info.product = 'Generic Backlight Device'
  linux.sysfs_path = '/sys/devices/virtual/backlight/acpi_video0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.category = 'laptop_panel'
  info.capabilities = { 'laptop_panel' }
  laptop_panel.access_method = 'general'
  laptop_panel.brightness_in_hardware = true
  laptop_panel.num_levels = 10 (0xa)
  info.addons = { 'hald-addon-generic-backlight' }

  16: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event6'
  input.product = 'SynPS/2 Synaptics TouchPad'
  info.subsystem = 'input'
  info.product = 'SynPS/2 Synaptics TouchPad'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input6/event6'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  info.category = 'input'
  info.capabilities = { 'input', 'input.touchpad' }
  linux.device_file = '/dev/input/event6'
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'

  17: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event4'
  input.product = 'AT Translated Set 2 keyboard'
  info.addons.singleton = { 'hald-addon-input' }
  info.subsystem = 'input'
  info.product = 'AT Translated Set 2 keyboard'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0/input/input4/event4'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  input.keymap.data = { 'e025:help', 'e026:setup', 'e027:battery', 'e029:switchvideomode', 'e033:euro', 'e034:dollar', 'e04e:brightnessup', 'e054:bluetooth', 'e055:wlan', 'e056:wlan', 'e057:bluetooth', 'e058:bluetooth', 'e059:brightnessup', 'e06e:brightnessup', 'e06f:brightnessdown', 'e071:f22', 'e072:f22', 'e073:prog2', 'e074:prog1', 'e075:presentation', 'e078:fn', 'e079:f23' }
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'
  info.category = 'input'
  info.capabilities = { 'input', 'input.keyboard', 'input.keypad', 'input.keys', 'input.keymap', 'button' }
  linux.device_file = '/dev/input/event4'
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'

  18: udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_2'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c1'
  scsi_host.host = 3 (0x3)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_2'

  19: udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c1'
  scsi_host.host = 2 (0x2)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_1'

  20: udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c1'
  scsi_host.host = 1 (0x1)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_0'

  21: udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_scsi_device_lun0_scsi_generic'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_generic'
  info.subsystem = 'scsi_generic'
  info.product = 'SCSI Generic Interface'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_scsi_device_lun0'
  scsi_generic.device = '/dev/sg0'
  info.category = 'scsi_generic'
  info.capabilities = { 'scsi_generic' }
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_scsi_device_lun0_scsi_generic'
  linux.device_file = '/dev/sg0'

  22: udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host'
  scsi_host.host = 0 (0x0)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_scsi_host'

  23: udi = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if0_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event5'
  input.product = '1.3M WebCam'
  button.has_state = false
  info.addons.singleton = { 'hald-addon-input' }
  info.subsystem = 'input'
  info.product = '1.3M WebCam'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5/event5'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if0'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if0_logicaldev_input'
  info.category = 'input'
  info.capabilities = { 'input', 'button', 'input.keys' }
  linux.device_file = '/dev/input/event5'
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if0'

  24: udi = '/org/freedesktop/Hal/devices/net_88_9f_fa_1c_24_3b'
  info.subsystem = 'net'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'net'
  net.originating_device = '/org/freedesktop/Hal/devices/pci_14e4_4727'
  net.interface = 'eth1'
  net.address = '88:9f:fa:1c:24:3b'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth1'
  info.parent = '/org/freedesktop/Hal/devices/pci_14e4_4727'
  net.arp_proto_hw_id = 1 (0x1)
  net.linux.ifindex = 3 (0x3)
  info.category = 'net.80211'
  info.capabilities = { 'net', 'net.80211' }
  info.udi = '/org/freedesktop/Hal/devices/net_88_9f_fa_1c_24_3b'
  net.80211.mac_address = 150220677325883ull (0x889ffa1c243bull)
  info.product = 'WLAN Interface'

  25: udi = '/org/freedesktop/Hal/devices/net_1c_75_08_ba_16_6c'
  info.subsystem = 'net'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'net'
  info.interfaces = { 'org.freedesktop.Hal.Device.WakeOnLan' }
  net.originating_device = '/org/freedesktop/Hal/devices/pci_1969_2060'
  net.interface = 'eth0'
  net.address = '1c:75:08:ba:16:6c'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0'
  info.parent = '/org/freedesktop/Hal/devices/pci_1969_2060'
  net.arp_proto_hw_id = 1 (0x1)
  net.linux.ifindex = 2 (0x2)
  info.category = 'net.80203'
  info.capabilities = { 'net', 'net.80203', 'wake_on_lan' }
  info.udi = '/org/freedesktop/Hal/devices/net_1c_75_08_ba_16_6c'
  org.freedesktop.Hal.Device.WakeOnLan.method_names = { 'GetSupported', 'GetEnabled', 'SetEnabled' }
  net.80203.mac_address = 31288983164524ull (0x1c7508ba166cull)
  info.product = 'Networking Interface'
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = { 'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable' }
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = { '', '', 'b' }
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = { '', '', 'enable' }

  26: udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/pcmC0D0p'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  alsa.card = 0 (0x0)
  alsa.type = 'playback'
  alsa.card_id = 'HDA Intel'
  alsa.device = 0 (0x0)
  alsa.pcm_class = 'generic'
  alsa.device_id = 'ALC272X Analog'
  info.subsystem = 'sound'
  info.product = 'ALC272X Analog ALSA Playback Device'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_0'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  linux.device_file = '/dev/snd/pcmC0D0p'

  27: udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_capture_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/pcmC0D0c'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  alsa.card = 0 (0x0)
  alsa.type = 'capture'
  alsa.card_id = 'HDA Intel'
  alsa.device = 0 (0x0)
  alsa.pcm_class = 'generic'
  alsa.device_id = 'ALC272X Analog'
  info.subsystem = 'sound'
  info.product = 'ALC272X Analog ALSA Capture Device'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_capture_0'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  linux.device_file = '/dev/snd/pcmC0D0c'

  28: udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_hw_specific_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/hwC0D0'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  alsa.card = 0 (0x0)
  alsa.type = 'hw_specific'
  alsa.card_id = 'HDA Intel'
  alsa.device = 0 (0x0)
  info.subsystem = 'sound'
  info.product = 'HDA Intel ALSA hardware specific Device'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_hw_specific_0'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  linux.device_file = '/dev/snd/hwC0D0'

  29: udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/controlC0'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  alsa.card = 0 (0x0)
  alsa.type = 'control'
  alsa.card_id = 'HDA Intel'
  info.subsystem = 'sound'
  info.product = 'HDA Intel ALSA Control Device'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  linux.device_file = '/dev/snd/controlC0'

  30: udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8'
  sound.card = 0 (0x0)
  sound.card_id = 'HDA Intel'
  info.subsystem = 'sound'
  info.product = 'HDA Intel Sound Card'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  info.category = 'sound'
  info.capabilities = { 'sound' }

  31: udi = '/org/freedesktop/Hal/devices/pci_8086_a011_drm__null__controlD64'
  info.vendor = 'Intel Corporation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'drm'
  info.subsystem = 'drm'
  info.product = 'Direct Rendering Manager Device'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/drm/controlD64'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_a011'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_a011_drm__null__controlD64'
  info.category = 'drm'
  info.capabilities = { 'drm' }
  linux.device_file = '/dev/dri/controlD64'

  32: udi = '/org/freedesktop/Hal/devices/pci_8086_a011_drm__null__card0_drm__null__card0_VGA_1'
  info.vendor = 'Intel Corporation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'drm'
  info.subsystem = 'drm'
  info.product = 'Direct Rendering Manager Device'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_a011_drm__null__card0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_a011_drm__null__card0_drm__null__card0_VGA_1'
  info.category = 'drm'
  info.capabilities = { 'drm' }
  linux.device_file = ''

  33: udi = '/org/freedesktop/Hal/devices/pci_8086_a011_drm__null__card0_drm__null__card0_LVDS_1'
  info.vendor = 'Intel Corporation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'drm'
  info.subsystem = 'drm'
  info.product = 'Direct Rendering Manager Device'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_a011_drm__null__card0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_a011_drm__null__card0_drm__null__card0_LVDS_1'
  info.category = 'drm'
  info.capabilities = { 'drm' }
  linux.device_file = ''

  34: udi = '/org/freedesktop/Hal/devices/pci_8086_a011_drm__null__card0'
  info.vendor = 'Intel Corporation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'drm'
  info.subsystem = 'drm'
  info.product = 'Direct Rendering Manager Device'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/drm/card0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_a011'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_a011_drm__null__card0'
  info.category = 'drm'
  info.capabilities = { 'drm' }
  linux.device_file = '/dev/dri/card0'

  35: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event1'
  input.product = 'Sleep Button'
  button.has_state = false
  button.type = 'sleep'
  info.addons.singleton = { 'hald-addon-input' }
  info.subsystem = 'input'
  info.product = 'Sleep Button'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'
  info.category = 'input'
  info.capabilities = { 'input', 'button', 'input.keys' }
  linux.device_file = '/dev/input/event1'

  36: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event0'
  input.product = 'Power Button'
  button.has_state = false
  button.type = 'power'
  info.addons.singleton = { 'hald-addon-input' }
  info.subsystem = 'input'
  info.product = 'Power Button'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  info.category = 'input'
  info.capabilities = { 'input', 'button', 'input.keys' }
  linux.device_file = '/dev/input/event0'

  37: udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'power_supply'
  battery.type = 'primary'
  battery.reporting.technology = 'Li-ion'
  battery.technology = 'lithium-ion'
  info.subsystem = 'power_supply'
  battery.model = 'AL10A31'
  battery.vendor = 'SANYO'
  battery.voltage.design = 11100 (0x2b5c)
  info.product = 'AL10A31'
  battery.reporting.design = 2200 (0x898)
  battery.voltage.unit = 'mV'
  battery.serial = ''
  battery.present = true
  battery.reporting.rate = 0 (0x0)
  battery.is_rechargeable = true
  battery.rechargeable.is_charging = true
  battery.rechargeable.is_discharging = false
  battery.reporting.current = 1258 (0x4ea)
  battery.reporting.last_full = 2132 (0x854)
  battery.charge_level.current = 13963 (0x368b)
  battery.charge_level.last_full = 23665 (0x5c71)
  battery.charge_level.design = 24420 (0x5f64)
  battery.charge_level.rate = 0 (0x0)
  battery.charge_level.percentage = 59 (0x3b)
  battery.reporting.unit = 'mAh'
  battery.voltage.current = 11965 (0x2ebd)
  battery.remaining_time = 4996 (0x1384)
  info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'battery'
  info.capabilities = { 'battery' }

  38: udi = '/org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'power_supply'
  ac_adapter.present = true
  info.subsystem = 'power_supply'
  info.product = 'Generic AC Adapter Device'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/ACPI0003:00/power_supply/AC'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC'
  info.category = 'ac_adapter'
  info.capabilities = { 'ac_adapter' }

  39: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event7'
  input.product = 'Video Bus'
  info.addons.singleton = { 'hald-addon-input' }
  info.subsystem = 'input'
  info.product = 'Video Bus'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7/event7'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  info.category = 'input'
  info.capabilities = { 'input', 'input.keys', 'button' }
  linux.device_file = '/dev/input/event7'

  40: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.device = '/dev/input/event3'
  input.product = 'Power Button'
  button.has_state = false
  button.type = 'power'
  info.addons.singleton = { 'hald-addon-input' }
  info.subsystem = 'input'
  info.product = 'Power Button'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  info.category = 'input'
  info.capabilities = { 'input', 'button', 'input.keys' }
  linux.device_file = '/dev/input/event3'

  41: udi = '/org/freedesktop/Hal/devices/pnp_SYN1b1c'
  linux.hotplug_type = 2 (0x2)
  pnp.id = 'SYN1b1c'
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'PnP Device (SYN1b1c)'
  linux.sysfs_path = '/sys/devices/pnp0/00:08'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.linux.driver = 'i8042 aux'
  info.udi = '/org/freedesktop/Hal/devices/pnp_SYN1b1c'

  42: udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'
  linux.hotplug_type = 2 (0x2)
  pnp.id = 'PNP0303'
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'
  linux.sysfs_path = '/sys/devices/pnp0/00:07'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.linux.driver = 'i8042 kbd'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'

  43: udi = '/org/freedesktop/Hal/devices/pnp_INT0800'
  linux.hotplug_type = 2 (0x2)
  pnp.id = 'INT0800'
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'PnP Device (INT0800)'
  linux.sysfs_path = '/sys/devices/pnp0/00:06'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/pnp_INT0800'

  44: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  linux.hotplug_type = 2 (0x2)
  pnp.id = 'PNP0c04'
  pnp.description = 'Math Coprocessor'
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'Math Coprocessor'
  linux.sysfs_path = '/sys/devices/pnp0/00:05'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'

  45: udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'
  linux.hotplug_type = 2 (0x2)
  pnp.id = 'PNP0103'
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'PnP Device (PNP0103)'
  linux.sysfs_path = '/sys/devices/pnp0/00:04'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'

  46: udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  linux.hotplug_type = 2 (0x2)
  pnp.id = 'PNP0b00'
  pnp.description = 'AT Real-Time Clock'
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'AT Real-Time Clock'
  linux.sysfs_path = '/sys/devices/pnp0/00:03'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.linux.driver = 'rtc_cmos'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'

  47: udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  linux.hotplug_type = 2 (0x2)
  pnp.id = 'PNP0200'
  pnp.description = 'AT DMA Controller'
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'AT DMA Controller'
  linux.sysfs_path = '/sys/devices/pnp0/00:02'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'

  48: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  linux.hotplug_type = 2 (0x2)
  pnp.id = 'PNP0c02'
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  linux.sysfs_path = '/sys/devices/pnp0/00:01'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.linux.driver = 'system'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'

  49: udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'
  linux.hotplug_type = 2 (0x2)
  pnp.id = 'PNP0a08'
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'PnP Device (PNP0a08)'
  linux.sysfs_path = '/sys/devices/pnp0/00:00'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'

  50: udi = '/org/freedesktop/Hal/devices/platform_vboxdrv_0'
  platform.id = 'vboxdrv.0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  info.subsystem = 'platform'
  info.product = 'Platform Device (vboxdrv.0)'
  linux.sysfs_path = '/sys/devices/platform/vboxdrv.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.linux.driver = 'vboxdrv'
  info.udi = '/org/freedesktop/Hal/devices/platform_vboxdrv_0'

  51: udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  platform.id = 'serial8250'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  info.subsystem = 'platform'
  info.product = 'Platform Device (serial8250)'
  linux.sysfs_path = '/sys/devices/platform/serial8250'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.linux.driver = 'serial8250'
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'

  52: udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  platform.id = 'pcspkr'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  info.subsystem = 'platform'
  info.product = 'Platform Device (pcspkr)'
  linux.sysfs_path = '/sys/devices/platform/pcspkr'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'

  53: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  serio.id = 'serio1'
  serio.description = 'i8042 AUX port'
  linux.subsystem = 'serio'
  linux.hotplug_type = 2 (0x2)
  info.subsystem = 'serio'
  info.product = 'i8042 AUX port'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'
  info.linux.driver = 'psmouse'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'

  54: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  serio.id = 'serio0'
  serio.description = 'i8042 KBD port'
  linux.subsystem = 'serio'
  linux.hotplug_type = 2 (0x2)
  info.subsystem = 'serio'
  info.product = 'i8042 KBD port'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'
  info.linux.driver = 'atkbd'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'

  55: udi = '/org/freedesktop/Hal/devices/platform_i8042'
  platform.id = 'i8042'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  info.subsystem = 'platform'
  info.product = 'Platform Device (i8042)'
  linux.sysfs_path = '/sys/devices/platform/i8042'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.linux.driver = 'i8042'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'

  56: udi = '/org/freedesktop/Hal/devices/platform_eisa_0'
  platform.id = 'eisa.0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  info.subsystem = 'platform'
  info.product = 'Platform Device (eisa.0)'
  linux.sysfs_path = '/sys/devices/platform/eisa.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/platform_eisa_0'

  57: udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'
  platform.id = 'Fixed MDIO bus.0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  info.subsystem = 'platform'
  info.product = 'Platform Device (Fixed MDIO bus.0)'
  linux.sysfs_path = '/sys/devices/platform/Fixed MDIO bus.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'

  58: udi = '/org/freedesktop/Hal/devices/pci_8086_27da'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10/ICH 7 Family SMBus Controller'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.subsystem = 'pci'
  info.product = 'N10/ICH 7 Family SMBus Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.3'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.3'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27da'
  pci.product_id = 10202 (0x27da)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 5 (0x5)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

  59: udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_scsi_device_lun0'
  scsi.type = 'disk'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host_scsi_device_lun0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi'
  info.subsystem = 'scsi'
  info.product = 'SCSI Device'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host'
  info.linux.driver = 'sd'
  scsi.host = 0 (0x0)
  scsi.bus = 0 (0x0)
  scsi.target = 0 (0x0)
  scsi.lun = 0 (0x0)
  scsi.model = 'TOSHIBA MK2565GS'
  scsi.vendor = 'ATA'

  60: udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2/host0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c1'
  scsi_host.host = 0 (0x0)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c1_scsi_host'

  61: udi = '/org/freedesktop/Hal/devices/pci_8086_27c1'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10/ICH7 Family SATA AHCI Controller'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c1'
  info.subsystem = 'pci'
  info.product = 'N10/ICH7 Family SATA AHCI Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.2'
  info.linux.driver = 'ahci'
  pci.product_id = 10177 (0x27c1)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 1 (0x1)
  pci.device_subclass = 6 (0x6)
  pci.device_protocol = 1 (0x1)
  pci.vendor = 'Intel Corporation'

  62: udi = '/org/freedesktop/Hal/devices/pci_8086_27bc'
  info.vendor = 'Intel Corporation'
  pci.product = 'NM10 Family LPC Controller'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.subsystem = 'pci'
  info.product = 'NM10 Family LPC Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27bc'
  pci.product_id = 10172 (0x27bc)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 1 (0x1)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

  63: udi = '/org/freedesktop/Hal/devices/pci_8086_2448'
  info.vendor = 'Intel Corporation'
  pci.product = '82801 Mobile PCI Bridge'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.subsystem = 'pci'
  info.product = '82801 Mobile PCI Bridge'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_2448'
  pci.product_id = 9288 (0x2448)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 1 (0x1)
  pci.vendor = 'Intel Corporation'

  64: udi = '/org/freedesktop/Hal/devices/usb_device_cf2_6250_606569746801_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB Vendor Specific Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_cf2_6250_606569746801_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 0 (0x0)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 3314 (0xcf2)
  usb.product_id = 25168 (0x6250)
  usb.vendor = 'ENE Technology, Inc.'
  usb.product = 'USB Vendor Specific Interface'
  usb.device_revision_bcd = 256 (0x100)
  usb.num_ports = 0 (0x0)
  usb.speed = 480.000
  usb.linux.device_number = 3 (0x3)
  usb.max_power = 498 (0x1f2)
  usb.can_wake_up = false
  usb.version = 2.00000
  usb.serial = '606569746801'
  usb.bus_number = 1 (0x1)
  usb.is_self_powered = false
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_cf2_6250_606569746801'
  usb.interface.subclass = 6 (0x6)
  usb.interface.class = 255 (0xff)
  usb.interface.protocol = 80 (0x50)

  65: udi = '/org/freedesktop/Hal/devices/usb_device_cf2_6250_606569746801'
  info.vendor = 'ENE Technology, Inc.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 0 (0x0)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 3314 (0xcf2)
  usb_device.product_id = 25168 (0x6250)
  usb_device.vendor = 'ENE Technology, Inc.'
  usb_device.product = 'UB6250'
  usb_device.device_revision_bcd = 256 (0x100)
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_cf2_6250_606569746801'
  usb_device.num_ports = 0 (0x0)
  info.product = 'UB6250'
  usb_device.speed = 480.000
  usb_device.linux.device_number = 3 (0x3)
  usb_device.max_power = 498 (0x1f2)
  usb_device.can_wake_up = false
  usb_device.version = 2.00000
  usb_device.serial = '606569746801'
  linux.device_file = '/dev/bus/usb/001/003'
  usb_device.bus_number = 1 (0x1)
  usb_device.is_self_powered = false
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'
  info.linux.driver = 'usb'

  66: udi = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB Video Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if1'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.1'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 2 (0x2)
  usb.device_class = 239 (0xef)
  usb.device_subclass = 2 (0x2)
  usb.device_protocol = 1 (0x1)
  usb.vendor_id = 1614 (0x64e)
  usb.product_id = 41497 (0xa219)
  usb.vendor = 'Suyin Corp.'
  usb.product = 'USB Video Interface'
  usb.device_revision_bcd = 533 (0x215)
  usb.num_ports = 0 (0x0)
  usb.speed = 480.000
  usb.linux.device_number = 2 (0x2)
  usb.max_power = 500 (0x1f4)
  usb.can_wake_up = false
  usb.version = 2.00000
  usb.serial = 'HF1315-S32B-OV01-VA-R02.01.05'
  usb.bus_number = 1 (0x1)
  usb.is_self_powered = false
  usb.interface.number = 1 (0x1)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.1'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05'
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 14 (0xe)
  info.linux.driver = 'uvcvideo'
  usb.interface.description = '1.3M WebCam'
  usb.interface.subclass = 2 (0x2)

  67: udi = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB Video Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 2 (0x2)
  usb.device_class = 239 (0xef)
  usb.device_subclass = 2 (0x2)
  usb.device_protocol = 1 (0x1)
  usb.vendor_id = 1614 (0x64e)
  usb.product_id = 41497 (0xa219)
  usb.vendor = 'Suyin Corp.'
  usb.product = 'USB Video Interface'
  usb.device_revision_bcd = 533 (0x215)
  usb.num_ports = 0 (0x0)
  usb.speed = 480.000
  usb.linux.device_number = 2 (0x2)
  usb.max_power = 500 (0x1f4)
  usb.can_wake_up = false
  usb.version = 2.00000
  usb.serial = 'HF1315-S32B-OV01-VA-R02.01.05'
  usb.bus_number = 1 (0x1)
  usb.is_self_powered = false
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05'
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 14 (0xe)
  info.linux.driver = 'uvcvideo'
  usb.interface.description = '1.3M WebCam'
  usb.interface.subclass = 1 (0x1)

  68: udi = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05'
  info.vendor = 'Suyin Corp.'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 2 (0x2)
  usb_device.device_class = 239 (0xef)
  usb_device.device_subclass = 2 (0x2)
  usb_device.device_protocol = 1 (0x1)
  usb_device.vendor_id = 1614 (0x64e)
  usb_device.product_id = 41497 (0xa219)
  usb_device.vendor = 'Suyin Corp.'
  usb_device.product = '1.3M WebCam'
  usb_device.device_revision_bcd = 533 (0x215)
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05'
  usb_device.num_ports = 0 (0x0)
  info.product = '1.3M WebCam'
  usb_device.speed = 480.000
  usb_device.linux.device_number = 2 (0x2)
  usb_device.max_power = 500 (0x1f4)
  usb_device.can_wake_up = false
  usb_device.version = 2.00000
  usb_device.serial = 'HF1315-S32B-OV01-VA-R02.01.05'
  linux.device_file = '/dev/bus/usb/001/002'
  usb_device.bus_number = 1 (0x1)
  usb_device.is_self_powered = false
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'
  info.linux.driver = 'usb'

  69: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 7531 (0x1d6b)
  usb.product_id = 2 (0x2)
  usb.vendor = 'Linux Foundation'
  usb.product = 'USB Hub Interface'
  usb.device_revision_bcd = 518 (0x206)
  usb.num_ports = 8 (0x8)
  usb.speed = 480.000
  usb.linux.device_number = 1 (0x1)
  usb.max_power = 0 (0x0)
  usb.can_wake_up = true
  usb.version = 2.00000
  usb.serial = '0000:00:1d.7'
  usb.bus_number = 1 (0x1)
  usb.is_self_powered = true
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 9 (0x9)
  info.linux.driver = 'hub'
  usb.interface.subclass = 0 (0x0)

  70: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'
  info.vendor = 'Linux Foundation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product_id = 2 (0x2)
  usb_device.vendor = 'Linux Foundation'
  usb_device.product = '2.0 root hub'
  usb_device.device_revision_bcd = 518 (0x206)
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7'
  usb_device.num_ports = 8 (0x8)
  info.product = '2.0 root hub'
  usb_device.speed = 480.000
  usb_device.linux.device_number = 1 (0x1)
  usb_device.max_power = 0 (0x0)
  usb_device.can_wake_up = true
  usb_device.version = 2.00000
  usb_device.serial = '0000:00:1d.7'
  linux.device_file = '/dev/bus/usb/001/001'
  usb_device.bus_number = 1 (0x1)
  usb_device.is_self_powered = true
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27cc'
  info.linux.driver = 'usb'

  71: udi = '/org/freedesktop/Hal/devices/pci_8086_27cc'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10/ICH 7 Family USB2 EHCI Controller'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27cc'
  info.subsystem = 'pci'
  info.product = 'N10/ICH 7 Family USB2 EHCI Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7'
  info.linux.driver = 'ehci_hcd'
  pci.product_id = 10188 (0x27cc)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 32 (0x20)
  pci.vendor = 'Intel Corporation'

  72: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 7531 (0x1d6b)
  usb.product_id = 1 (0x1)
  usb.vendor = 'Linux Foundation'
  usb.product = 'USB Hub Interface'
  usb.device_revision_bcd = 518 (0x206)
  usb.num_ports = 2 (0x2)
  usb.speed = 12.0000
  usb.linux.device_number = 1 (0x1)
  usb.max_power = 0 (0x0)
  usb.can_wake_up = true
  usb.version = 1.10000
  usb.serial = '0000:00:1d.3'
  usb.bus_number = 5 (0x5)
  usb.is_self_powered = true
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 9 (0x9)
  info.linux.driver = 'hub'
  usb.interface.subclass = 0 (0x0)

  73: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'
  info.vendor = 'Linux Foundation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product_id = 1 (0x1)
  usb_device.vendor = 'Linux Foundation'
  usb_device.product = '1.1 root hub'
  usb_device.device_revision_bcd = 518 (0x206)
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'
  usb_device.num_ports = 2 (0x2)
  info.product = '1.1 root hub'
  usb_device.speed = 12.0000
  usb_device.linux.device_number = 1 (0x1)
  usb_device.max_power = 0 (0x0)
  usb_device.can_wake_up = true
  usb_device.version = 1.10000
  usb_device.serial = '0000:00:1d.3'
  linux.device_file = '/dev/bus/usb/005/001'
  usb_device.bus_number = 5 (0x5)
  usb_device.is_self_powered = true
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb5'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27cb'
  info.linux.driver = 'usb'

  74: udi = '/org/freedesktop/Hal/devices/pci_8086_27cb'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10/ICH 7 Family USB UHCI Controller #4'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27cb'
  info.subsystem = 'pci'
  info.product = 'N10/ICH 7 Family USB UHCI Controller #4'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3'
  info.linux.driver = 'uhci_hcd'
  pci.product_id = 10187 (0x27cb)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

  75: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 7531 (0x1d6b)
  usb.product_id = 1 (0x1)
  usb.vendor = 'Linux Foundation'
  usb.product = 'USB Hub Interface'
  usb.device_revision_bcd = 518 (0x206)
  usb.num_ports = 2 (0x2)
  usb.speed = 12.0000
  usb.linux.device_number = 1 (0x1)
  usb.max_power = 0 (0x0)
  usb.can_wake_up = true
  usb.version = 1.10000
  usb.serial = '0000:00:1d.2'
  usb.bus_number = 4 (0x4)
  usb.is_self_powered = true
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 9 (0x9)
  info.linux.driver = 'hub'
  usb.interface.subclass = 0 (0x0)

  76: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'
  info.vendor = 'Linux Foundation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product_id = 1 (0x1)
  usb_device.vendor = 'Linux Foundation'
  usb_device.product = '1.1 root hub'
  usb_device.device_revision_bcd = 518 (0x206)
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2'
  usb_device.num_ports = 2 (0x2)
  info.product = '1.1 root hub'
  usb_device.speed = 12.0000
  usb_device.linux.device_number = 1 (0x1)
  usb_device.max_power = 0 (0x0)
  usb_device.can_wake_up = true
  usb_device.version = 1.10000
  usb_device.serial = '0000:00:1d.2'
  linux.device_file = '/dev/bus/usb/004/001'
  usb_device.bus_number = 4 (0x4)
  usb_device.is_self_powered = true
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb4'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27ca'
  info.linux.driver = 'usb'

  77: udi = '/org/freedesktop/Hal/devices/pci_8086_27ca'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10/ICH 7 Family USB UHCI Controller #3'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27ca'
  info.subsystem = 'pci'
  info.product = 'N10/ICH 7 Family USB UHCI Controller #3'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2'
  info.linux.driver = 'uhci_hcd'
  pci.product_id = 10186 (0x27ca)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

  78: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 7531 (0x1d6b)
  usb.product_id = 1 (0x1)
  usb.vendor = 'Linux Foundation'
  usb.product = 'USB Hub Interface'
  usb.device_revision_bcd = 518 (0x206)
  usb.num_ports = 2 (0x2)
  usb.speed = 12.0000
  usb.linux.device_number = 1 (0x1)
  usb.max_power = 0 (0x0)
  usb.can_wake_up = true
  usb.version = 1.10000
  usb.serial = '0000:00:1d.1'
  usb.bus_number = 3 (0x3)
  usb.is_self_powered = true
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 9 (0x9)
  info.linux.driver = 'hub'
  usb.interface.subclass = 0 (0x0)

  79: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'
  info.vendor = 'Linux Foundation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product_id = 1 (0x1)
  usb_device.vendor = 'Linux Foundation'
  usb_device.product = '1.1 root hub'
  usb_device.device_revision_bcd = 518 (0x206)
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'
  usb_device.num_ports = 2 (0x2)
  info.product = '1.1 root hub'
  usb_device.speed = 12.0000
  usb_device.linux.device_number = 1 (0x1)
  usb_device.max_power = 0 (0x0)
  usb_device.can_wake_up = true
  usb_device.version = 1.10000
  usb_device.serial = '0000:00:1d.1'
  linux.device_file = '/dev/bus/usb/003/001'
  usb_device.bus_number = 3 (0x3)
  usb_device.is_self_powered = true
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c9'
  info.linux.driver = 'usb'

  80: udi = '/org/freedesktop/Hal/devices/pci_8086_27c9'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10/ICH 7 Family USB UHCI Controller #2'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c9'
  info.subsystem = 'pci'
  info.product = 'N10/ICH 7 Family USB UHCI Controller #2'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1'
  info.linux.driver = 'uhci_hcd'
  pci.product_id = 10185 (0x27c9)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

  81: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 7531 (0x1d6b)
  usb.product_id = 1 (0x1)
  usb.vendor = 'Linux Foundation'
  usb.product = 'USB Hub Interface'
  usb.device_revision_bcd = 518 (0x206)
  usb.num_ports = 2 (0x2)
  usb.speed = 12.0000
  usb.linux.device_number = 1 (0x1)
  usb.max_power = 0 (0x0)
  usb.can_wake_up = true
  usb.version = 1.10000
  usb.serial = '0000:00:1d.0'
  usb.bus_number = 2 (0x2)
  usb.is_self_powered = true
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'
  usb.interface.protocol = 0 (0x0)
  usb.interface.class = 9 (0x9)
  info.linux.driver = 'hub'
  usb.interface.subclass = 0 (0x0)

  82: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'
  info.vendor = 'Linux Foundation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product_id = 1 (0x1)
  usb_device.vendor = 'Linux Foundation'
  usb_device.product = '1.1 root hub'
  usb_device.device_revision_bcd = 518 (0x206)
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'
  usb_device.num_ports = 2 (0x2)
  info.product = '1.1 root hub'
  usb_device.speed = 12.0000
  usb_device.linux.device_number = 1 (0x1)
  usb_device.max_power = 0 (0x0)
  usb_device.can_wake_up = true
  usb_device.version = 1.10000
  usb_device.serial = '0000:00:1d.0'
  linux.device_file = '/dev/bus/usb/002/001'
  usb_device.bus_number = 2 (0x2)
  usb_device.is_self_powered = true
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27c8'
  info.linux.driver = 'usb'

  83: udi = '/org/freedesktop/Hal/devices/pci_8086_27c8'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10/ICH 7 Family USB UHCI Controller #1'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27c8'
  info.subsystem = 'pci'
  info.product = 'N10/ICH 7 Family USB UHCI Controller #1'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0'
  info.linux.driver = 'uhci_hcd'
  pci.product_id = 10184 (0x27c8)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

  84: udi = '/org/freedesktop/Hal/devices/pci_14e4_4727'
  info.vendor = 'Broadcom Corporation'
  pci.product = 'BCM4313 802.11b/g LP-PHY'
  pci.subsys_vendor = 'Broadcom Corporation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_14e4_4727'
  info.subsystem = 'pci'
  info.product = 'BCM4313 802.11b/g LP-PHY'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d2'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0'
  info.linux.driver = 'wl'
  pci.product_id = 18215 (0x4727)
  pci.vendor_id = 5348 (0x14e4)
  pci.subsys_product_id = 1296 (0x510)
  pci.subsys_vendor_id = 5348 (0x14e4)
  pci.device_class = 2 (0x2)
  pci.device_subclass = 128 (0x80)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Broadcom Corporation'

  85: udi = '/org/freedesktop/Hal/devices/pci_8086_27d2'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10/ICH 7 Family PCI Express Port 2'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d2'
  info.subsystem = 'pci'
  info.product = 'N10/ICH 7 Family PCI Express Port 2'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1'
  info.linux.driver = 'pcieport'
  pci.product_id = 10194 (0x27d2)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

  86: udi = '/org/freedesktop/Hal/devices/pci_1969_2060'
  info.vendor = 'Atheros Communications'
  pci.product = 'AR8152 v1.1 Fast Ethernet'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_1969_2060'
  info.subsystem = 'pci'
  info.product = 'AR8152 v1.1 Fast Ethernet'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0'
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d0'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0'
  info.linux.driver = 'atl1c'
  pci.product_id = 8288 (0x2060)
  pci.vendor_id = 6505 (0x1969)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 2 (0x2)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Atheros Communications'

  87: udi = '/org/freedesktop/Hal/devices/pci_8086_27d0'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10/ICH 7 Family PCI Express Port 1'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d0'
  info.subsystem = 'pci'
  info.product = 'N10/ICH 7 Family PCI Express Port 1'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'
  info.linux.driver = 'pcieport'
  pci.product_id = 10192 (0x27d0)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

  88: udi = '/org/freedesktop/Hal/devices/pci_8086_27d8'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10/ICH 7 Family High Definition Audio Controller'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8'
  info.subsystem = 'pci'
  info.product = 'N10/ICH 7 Family High Definition Audio Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0'
  info.linux.driver = 'HDA Intel'
  pci.product_id = 10200 (0x27d8)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 4 (0x4)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

  89: udi = '/org/freedesktop/Hal/devices/pci_8086_a012'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10 Family Integrated Graphics Controller'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.subsystem = 'pci'
  info.product = 'N10 Family Integrated Graphics Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_a012'
  pci.product_id = 40978 (0xa012)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 3 (0x3)
  pci.device_subclass = 128 (0x80)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

  90: udi = '/org/freedesktop/Hal/devices/pci_8086_a011'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10 Family Integrated Graphics Controller'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_a011'
  info.subsystem = 'pci'
  info.product = 'N10 Family Integrated Graphics Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'
  info.linux.driver = 'i915'
  pci.product_id = 40977 (0xa011)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 3 (0x3)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'

  91: udi = '/org/freedesktop/Hal/devices/pci_8086_a010'
  info.vendor = 'Intel Corporation'
  pci.product = 'N10 Family DMI Bridge'
  pci.subsys_vendor = 'Acer Incorporated [ALI]'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_a010'
  info.subsystem = 'pci'
  info.product = 'N10 Family DMI Bridge'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'
  info.linux.driver = 'agpgart-intel'
  pci.product_id = 40976 (0xa010)
  pci.vendor_id = 32902 (0x8086)
  pci.subsys_product_id = 841 (0x349)
  pci.subsys_vendor_id = 4133 (0x1025)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Intel Corporation'
----- hal device list end -----
>> floppy.1: get nvram
>> floppy.2: klog info
>> bios.1: cmdline
>> bios.1.1: apm
>> bios.2: ram
  bios: 0 disks
>> bios.2: rom
>> bios.3: smp
----- BIOS data 0x00400 - 0x004ff -----
  400  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  410  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  420  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  430  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  440  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  450  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  460  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  470  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  480  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  490  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4a0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4b0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4c0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4d0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4e0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4f0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
----- BIOS data end -----
>> bios.4: vbe
VBE: Could not init Int10
>> bios.5: 32
>> bios.6: acpi
>> sys.1: cpu
  vm check: vm_1 = 0, vm_2 = -1
  is_vmware = 0, has_vmware_mouse = 0
>> misc.9: kernel log
----- kernel log -----
  <7>[ 7265.160571] eth1: no IPv6 routers present
  <6>[10054.052671] Skipping EDID probe due to cached edid
  <3>[11856.805882] ata1.00: exception Emask 0x10 SAct 0x1 SErr 0x50000 action 0xe frozen
  <3>[11856.805895] ata1.00: irq_stat 0x00400000, PHY RDY changed
  <3>[11856.805904] ata1: SError: { PHYRdyChg CommWake }
  <3>[11856.805913] ata1.00: failed command: READ FPDMA QUEUED
  <3>[11856.805931] ata1.00: cmd 60/08:00:58:08:9c/00:00:00:00:00/40 tag 0 ncq 4096 in
  <3>[11856.805934]          res 40/00:00:58:08:9c/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
  <3>[11856.805943] ata1.00: status: { DRDY }
  <6>[11856.805956] ata1: hard resetting link
  <6>[11857.700103] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
  <4>[11857.700762] ata1.00: unexpected _GTF length (4)
  <4>[11857.752264] ata1.00: unexpected _GTF length (4)
  <6>[11857.752484] ata1.00: configured for UDMA/100
  <6>[11857.752506] ata1: EH complete
  <7>[11862.243375] PM: Marking nosave pages: 0000000000002000 - 0000000000010000
  <7>[11862.243387] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
  <7>[11862.243398] PM: Basic memory bitmaps created
  <6>[11862.243403] PM: Syncing filesystems ... done.
  <4>[11862.257543] Freezing user space processes ... (elapsed 0.01 seconds) done.
  <4>[11862.272164] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
  <6>[11862.288229] PM: Preallocating image memory... done (allocated 128943 pages)
  <6>[11869.212111] PM: Allocated 515772 kbytes in 6.92 seconds (74.53 MB/s)
  <4>[11869.212117] Suspending console(s) (use no_console_suspend to debug)
  <6>[11869.213875] wl 0000:02:00.0: PCI INT A disabled
  <6>[11869.316428] HDA Intel 0000:00:1b.0: PCI INT A disabled
  <6>[11869.332051] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 117.576 msecs
  <5>[11869.824043] sd 0:0:0:0: [sda] Synchronizing SCSI cache
  <6>[11869.824165] PM: freeze of drv:sd dev:0:0:0:0 complete after 611.473 msecs
  <6>[11869.824201] PM: freeze of drv:scsi dev:target0:0:0 complete after 611.459 msecs
  <6>[11869.824229] PM: freeze of drv:scsi dev:host0 complete after 611.338 msecs
  <6>[11869.856788] PM: freeze of drv:ahci dev:0000:00:1f.2 complete after 642.762 msecs
  <6>[11869.856815] PM: freeze of drv: dev:pci0000:00 complete after 641.869 msecs
  <6>[11869.856842] PM: freeze of devices complete after 644.508 msecs
  <6>[11869.857903] PM: late freeze of devices complete after 1.052 msecs
  <6>[11869.857956] ACPI: Preparing to enter system sleep state S4
  <6>[11869.885482] PM: Saving platform NVS memory
  <4>[11869.900820] Disabling non-boot CPUs ...
  <4>[11869.916746] Broke affinity for irq 20
  <4>[11869.916761] Broke affinity for irq 22
  <6>[11870.020060] CPU 1 is now offline
  <6>[11870.020069] SMP alternatives: switching to UP code
  <6>[11870.025926] PM: Creating hibernation image:
  <6>[11870.028028] PM: Need to copy 128281 pages
  <7>[11870.028028] PM: Normal pages needed: 115316 + 1024, available pages: 118073
  <6>[11870.028028] PM: Restoring platform NVS memory
  <4>[11870.028028] Enabling non-boot CPUs ...
  <6>[11870.028028] SMP alternatives: switching to SMP code
  <6>[11870.031267] Booting Node 0 Processor 1 APIC 0x1
  <6>[11870.025139] Initializing CPU#1
  <4>[11870.140053] CPU1 is up
  <6>[11870.140553] ACPI: Waking up from system sleep state S4
  <7>[11870.240807] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
  <7>[11870.240892] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
  <7>[11870.241397] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00403, writing 0x2b00407)
  <7>[11870.241528] atl1c 0000:01:00.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
  <6>[11870.242134] PM: early restore of devices complete after 1.491 msecs
  <7>[11870.325502] i915 0000:00:02.0: setting latency timer to 64
  <3>[11870.327679] render error detected, EIR: 0x00000010
  <3>[11870.327685] page table error
  <3>[11870.327689]   PGTBL_ER: 0x00000003
  <3>[11870.327696] [drm:i915_report_and_clear_eir] *ERROR* EIR stuck: 0x00000010, masking
  <3>[11870.327728] render error detected, EIR: 0x00000010
  <3>[11870.327733] page table error
  <3>[11870.327736]   PGTBL_ER: 0x00000003
  <6>[11870.332570] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
  <7>[11870.332585] HDA Intel 0000:00:1b.0: setting latency timer to 64
  <7>[11870.332657] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
  <7>[11870.332732] uhci_hcd 0000:00:1d.0: setting latency timer to 64
  <4>[11870.332783] usb usb2: root hub lost power or was reset
  <7>[11870.332815] uhci_hcd 0000:00:1d.1: setting latency timer to 64
  <4>[11870.332862] usb usb3: root hub lost power or was reset
  <7>[11870.332891] uhci_hcd 0000:00:1d.2: setting latency timer to 64
  <4>[11870.332938] usb usb4: root hub lost power or was reset
  <7>[11870.332967] uhci_hcd 0000:00:1d.3: setting latency timer to 64
  <4>[11870.333015] usb usb5: root hub lost power or was reset
  <7>[11870.333044] ehci_hcd 0000:00:1d.7: setting latency timer to 64
  <4>[11870.333078] usb usb1: root hub lost power or was reset
  <7>[11870.336985] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
  <7>[11870.337027] ahci 0000:00:1f.2: setting latency timer to 64
  <6>[11870.337228] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
  <7>[11870.337239] wl 0000:02:00.0: setting latency timer to 64
  <7>[11870.390471] pci 0000:00:1e.0: setting latency timer to 64
  <5>[11870.391196] sd 0:0:0:0: [sda] Starting disk
  <6>[11870.444076] PM: restore of drv:atl1c dev:0000:01:00.0 complete after 106.994 msecs
  <6>[11870.532070] PM: restore of drv:usb dev:usb2 complete after 141.580 msecs
  <6>[11870.532149] PM: restore of drv:usb dev:usb5 complete after 141.275 msecs
  <6>[11870.532168] PM: restore of drv:hub dev:2-0:1.0 complete after 141.503 msecs
  <6>[11870.532182] PM: restore of drv:hub dev:5-0:1.0 complete after 141.265 msecs
  <6>[11870.624074] PM: restore of drv:usb dev:usb1 complete after 233.655 msecs
  <6>[11870.624106] PM: restore of drv:hub dev:1-0:1.0 complete after 233.651 msecs
  <6>[11870.636073] PM: restore of drv:usb dev:usb3 complete after 245.363 msecs
  <6>[11870.636103] PM: restore of drv:usb dev:usb4 complete after 245.313 msecs
  <6>[11870.636111] PM: restore of drv:hub dev:3-0:1.0 complete after 245.354 msecs
  <6>[11870.636123] PM: restore of drv:hub dev:4-0:1.0 complete after 245.289 msecs
  <6>[11870.700563] ata2: SATA link down (SStatus 0 SControl 300)
  <6>[11870.736550] usb 1-5: reset high speed USB device using ehci_hcd and address 3
  <6>[11870.869422] PM: restore of drv:usb dev:1-5 complete after 478.343 msecs
  <6>[11870.869443] PM: restore of drv:usb dev:1-5:1.0 complete after 478.327 msecs
  <6>[11870.872552] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
  <4>[11870.873488] ata1.00: unexpected _GTF length (4)
  <4>[11870.913702] ata1.00: unexpected _GTF length (4)
  <6>[11870.913929] ata1.00: configured for UDMA/100
  <6>[11870.977083] PM: restore of drv:sd dev:0:0:0:0 complete after 585.881 msecs
  <6>[11870.977124] PM: restore of drv:scsi_device dev:0:0:0:0 complete after 585.848 msecs
  <6>[11870.980571] usb 1-4: reset high speed USB device using ehci_hcd and address 2
  <6>[11870.984795] PM: restore of drv:battery dev:PNP0C0A:00 complete after 592.914 msecs
  <6>[11871.024585] PM: restore of drv:i915 dev:0000:00:02.0 complete after 699.086 msecs
  <6>[11871.149934] PM: restore of drv:usb dev:1-4 complete after 758.973 msecs
  <6>[11871.149966] PM: restore of drv:uvcvideo dev:1-4:1.0 complete after 758.970 msecs
  <6>[11871.149974] PM: restore of drv:uvcvideo dev:1-4:1.1 complete after 758.937 msecs
  <6>[11871.150179] PM: restore of devices complete after 824.895 msecs
  <7>[11871.151021] PM: Image restored successfully.
  <4>[11871.151026] Restarting tasks ... done.
  <7>[11871.158218] PM: Basic memory bitmaps freed
  <6>[11871.158233] video LNXVIDEO:00: Restoring backlight state
  <3>[11872.622886] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
  <6>[11872.680064] Skipping EDID probe due to cached edid
  <7>[11902.178933] atl1c 0000:01:00.0: irq 45 for MSI/MSI-X
  <6>[11902.179726] ADDRCONF(NETDEV_UP): eth0: link is not ready
  <7>[11912.752548] eth1: no IPv6 routers present
----- kernel log end -----
>> misc.1: misc data
>> misc.1.1: open serial
>> misc.1.2: open parallel
----- exec: "/sbin/rmmod lp" -----
  ERROR: Removing 'lp': Operation not permitted
----- return code: ? -----
----- exec: "/sbin/rmmod parport_pc" -----
  ERROR: Removing 'parport_pc': Operation not permitted
----- return code: ? -----
----- exec: "/sbin/rmmod parport" -----
  ERROR: Module parport is in use by parport_pc,ppdev,lp
----- return code: ? -----
>> misc.2.1: io
>> misc.2.2: dma
>> misc.2.3: irq
----- /proc/ioports -----
  0000-0cf7 : PCI Bus 0000:00
    0000-001f : dma1
    0020-0021 : pic1
    0040-0043 : timer0
    0050-0053 : timer1
    0060-0060 : keyboard
    0064-0064 : keyboard
    0070-0077 : rtc0
    0080-008f : dma page reg
    00a0-00a1 : pic2
    00c0-00df : dma2
    00f0-00ff : fpu
    03c0-03df : vga+
    0400-047f : pnp 00:01
      0400-0403 : ACPI PM1a_EVT_BLK
      0404-0405 : ACPI PM1a_CNT_BLK
      0408-040b : ACPI PM_TMR
      0410-0415 : ACPI CPU throttle
      0420-0420 : ACPI PM2_CNT_BLK
      0428-042f : ACPI GPE0_BLK
    0500-053f : pnp 00:01
    0600-060f : pnp 00:01
    0610-0610 : pnp 00:01
    0800-080f : pnp 00:01
    0810-0817 : pnp 00:01
  0cf8-0cff : PCI conf1
  0d00-ffff : PCI Bus 0000:00
    164e-164f : pnp 00:01
    4000-4fff : PCI Bus 0000:02
    5000-5fff : PCI Bus 0000:01
      5000-507f : 0000:01:00.0
        5000-507f : atl1c
    6000-601f : 0000:00:1f.3
    6020-603f : 0000:00:1d.3
      6020-603f : uhci_hcd
    6040-605f : 0000:00:1d.2
      6040-605f : uhci_hcd
    6060-607f : 0000:00:1d.1
      6060-607f : uhci_hcd
    6080-609f : 0000:00:1d.0
      6080-609f : uhci_hcd
    60a0-60af : 0000:00:1f.2
      60a0-60af : ahci
    60b0-60b7 : 0000:00:1f.2
      60b0-60b7 : ahci
    60b8-60bf : 0000:00:1f.2
      60b8-60bf : ahci
    60c0-60c7 : 0000:00:02.0
    60c8-60cb : 0000:00:1f.2
      60c8-60cb : ahci
    60cc-60cf : 0000:00:1f.2
      60cc-60cf : ahci
    ff2c-ff2f : pnp 00:01
----- /proc/ioports end -----
----- /proc/interrupts -----
    0:    5865539    3166244   IO-APIC-edge      timer
    1:       5486         22   IO-APIC-edge      i8042
    8:          0          1   IO-APIC-edge      rtc0
    9:      19953      19872   IO-APIC-fasteoi   acpi
   12:    1489652        345   IO-APIC-edge      i8042
   17:     206816     204316   IO-APIC-fasteoi   eth1
   18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
   20:          2          0   IO-APIC-fasteoi   uhci_hcd:usb3
   21:          2          0   IO-APIC-fasteoi   uhci_hcd:usb4
   22:         46         48   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5
   42:     125557       2682   PCI-MSI-edge      ahci
   43:     187295         30   PCI-MSI-edge      i915@pci:0000:00:02.0
   44:        114       1378   PCI-MSI-edge      hda_intel
   45:          0          0   PCI-MSI-edge      eth0
  NMI:          0          0   Non-maskable interrupts
  LOC:    6024730    7328843   Local timer interrupts
  SPU:          0          0   Spurious interrupts
  PMI:          0          0   Performance monitoring interrupts
  PND:          0          0   Performance pending work
  RES:     525697     582038   Rescheduling interrupts
  CAL:         59       2069   Function call interrupts
  TLB:      14425      17559   TLB shootdowns
  TRM:          0          0   Thermal event interrupts
  THR:          0          0   Threshold APIC interrupts
  MCE:          0          0   Machine check exceptions
  MCP:         47         47   Machine check polls
  ERR:          5
  MIS:          0
----- /proc/interrupts end -----
----- /proc/dma -----
   4: cascade
----- /proc/dma end -----
>> misc.3: FPU
>> misc.3.1: DMA
>> misc.3.2: PIC
>> misc.3.3: timer
>> misc.3.4: RTC
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 28
  model name	: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
  stepping	: 10
  cpu MHz		: 1000.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 2
  core id		: 0
  cpu cores	: 1
  apicid		: 0
  initial apicid	: 0
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 10
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
  bogomips	: 3324.37
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 32 bits physical, 48 bits virtual
  power management:
  
  processor	: 1
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 28
  model name	: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
  stepping	: 10
  cpu MHz		: 1000.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 2
  core id		: 0
  cpu cores	: 1
  apicid		: 1
  initial apicid	: 1
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 10
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
  bogomips	: 3325.08
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 32 bits physical, 48 bits virtual
  power management:
  
----- /proc/cpuinfo end -----
>> memory.1: main memory size
  kcore mem:  0x3f7fe000
  klog mem 0: 0x0
  klog mem 1: 0x0
  klog mem:   0x0
  bios mem:   0x0
  meminfo:    0x3df1f000
>> pci.1: sysfs drivers
----- sysfs driver list (id 0xfd5c4c8b8bf4dd6c) -----
      serial8250: /devices/platform/serial8250
           i8042: /devices/platform/i8042
      parport_pc: module = parport_pc
         vboxdrv: /devices/platform/vboxdrv.0
        pcieport: /devices/pci0000:00/0000:00:1c.0
        pcieport: /devices/pci0000:00/0000:00:1c.1
        ehci_hcd: /devices/pci0000:00/0000:00:1d.7
        ehci_hcd: module = ehci_hcd
        uhci_hcd: /devices/pci0000:00/0000:00:1d.0
        uhci_hcd: /devices/pci0000:00/0000:00:1d.1
        uhci_hcd: /devices/pci0000:00/0000:00:1d.2
        uhci_hcd: /devices/pci0000:00/0000:00:1d.3
        uhci_hcd: module = uhci_hcd
           atl1c: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
           atl1c: module = atl1c
            ahci: /devices/pci0000:00/0000:00:1f.2
            ahci: module = ahci
   agpgart-intel: /devices/pci0000:00/0000:00:00.0
   agpgart-intel: module = intel_agp
              wl: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
              wl: module = wl
            i915: /devices/pci0000:00/0000:00:02.0
            i915: module = drm
       HDA Intel: /devices/pci0000:00/0000:00:1b.0
       HDA Intel: module = snd_hda_intel
      parport_pc: module = parport_pc
              ec: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C09:00
           power: /devices/LNXSYSTM:00/LNXTHERM:00/LNXPOWER:00
        pci_root: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:00
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:01
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:02
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:03
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:04
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:05
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:06
        pci_link: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:07
             wmi: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C14:00
              ac: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/ACPI0003:00
          button: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00
          button: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00
          button: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00
          button: /devices/LNXSYSTM:00/LNXPWRBN:00
             fan: /devices/LNXSYSTM:00/LNXTHERM:00/PNP0C0B:00
       processor: /devices/LNXSYSTM:00/LNXCPU:00
       processor: /devices/LNXSYSTM:00/LNXCPU:01
       processor: /devices/LNXSYSTM:00/LNXCPU:02
       processor: /devices/LNXSYSTM:00/LNXCPU:03
         thermal: /devices/LNXSYSTM:00/LNXTHERM:00/LNXTHERM:01
         battery: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00
           video: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00
          system: /devices/pnp0/00:01
       i8042 kbd: /devices/pnp0/00:07
       i8042 aux: /devices/pnp0/00:08
        rtc_cmos: /devices/pnp0/00:03
              sd: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
           usbfs: module = usbcore
             hub: module = usbcore
             hub: /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
             hub: /devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
             usb: /devices/pci0000:00/0000:00:1d.7/usb1
             usb: /devices/pci0000:00/0000:00:1d.0/usb2
             usb: /devices/pci0000:00/0000:00:1d.1/usb3
             usb: /devices/pci0000:00/0000:00:1d.2/usb4
             usb: /devices/pci0000:00/0000:00:1d.3/usb5
             usb: /devices/pci0000:00/0000:00:1d.7/usb1/1-4
             usb: /devices/pci0000:00/0000:00:1d.7/usb1/1-5
        uvcvideo: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0
        uvcvideo: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.1
        uvcvideo: module = uvcvideo
           atkbd: /devices/platform/i8042/serio0
       serio_raw: module = serio_raw
         psmouse: module = psmouse
         psmouse: /devices/platform/i8042/serio1
----- sysfs driver list end -----
>> pci.2: get sysfs pci data
  pci device: name = 0000:00:00.0
    path = /devices/pci0000:00/0000:00:00.0
    modalias = "pci:v00008086d0000A010sv00001025sd00000349bc06sc00i00"
    class = 0x60000
    vendor = 0x8086
    device = 0xa010
    subvendor = 0x1025
    subdevice = 0x349
    irq = 0
    config[64]
  pci device: name = 0000:00:02.0
    path = /devices/pci0000:00/0000:00:02.0
    modalias = "pci:v00008086d0000A011sv00001025sd00000349bc03sc00i00"
    class = 0x30000
    vendor = 0x8086
    device = 0xa011
    subvendor = 0x1025
    subdevice = 0x349
    irq = 43
    res[0] = 0x58180000 0x581fffff 0x40200
    res[1] = 0x60c0 0x60c7 0x40101
    res[2] = 0x40000000 0x4fffffff 0x42208
    res[3] = 0x58000000 0x580fffff 0x40200
    config[64]
  pci device: name = 0000:00:02.1
    path = /devices/pci0000:00/0000:00:02.1
    modalias = "pci:v00008086d0000A012sv00001025sd00000349bc03sc80i00"
    class = 0x38000
    vendor = 0x8086
    device = 0xa012
    subvendor = 0x1025
    subdevice = 0x349
    irq = 0
    res[0] = 0x58100000 0x5817ffff 0x40200
    config[64]
  pci device: name = 0000:00:1b.0
    path = /devices/pci0000:00/0000:00:1b.0
    modalias = "pci:v00008086d000027D8sv00001025sd00000349bc04sc03i00"
    class = 0x40300
    vendor = 0x8086
    device = 0x27d8
    subvendor = 0x1025
    subdevice = 0x349
    irq = 44
    res[0] = 0x58200000 0x58203fff 0x140204
    config[64]
  pci device: name = 0000:00:1c.0
    path = /devices/pci0000:00/0000:00:1c.0
    modalias = "pci:v00008086d000027D0sv00001025sd00000349bc06sc04i00"
    class = 0x60400
    vendor = 0x8086
    device = 0x27d0
    subvendor = 0x1025
    subdevice = 0x349
    irq = 40
    config[64]
  pci device: name = 0000:00:1c.1
    path = /devices/pci0000:00/0000:00:1c.1
    modalias = "pci:v00008086d000027D2sv00001025sd00000349bc06sc04i00"
    class = 0x60400
    vendor = 0x8086
    device = 0x27d2
    subvendor = 0x1025
    subdevice = 0x349
    irq = 41
    config[64]
  pci device: name = 0000:00:1d.0
    path = /devices/pci0000:00/0000:00:1d.0
    modalias = "pci:v00008086d000027C8sv00001025sd00000349bc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x27c8
    subvendor = 0x1025
    subdevice = 0x349
    irq = 18
    res[4] = 0x6080 0x609f 0x40101
    config[64]
  pci device: name = 0000:00:1d.1
    path = /devices/pci0000:00/0000:00:1d.1
    modalias = "pci:v00008086d000027C9sv00001025sd00000349bc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x27c9
    subvendor = 0x1025
    subdevice = 0x349
    irq = 20
    res[4] = 0x6060 0x607f 0x40101
    config[64]
  pci device: name = 0000:00:1d.2
    path = /devices/pci0000:00/0000:00:1d.2
    modalias = "pci:v00008086d000027CAsv00001025sd00000349bc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x27ca
    subvendor = 0x1025
    subdevice = 0x349
    irq = 21
    res[4] = 0x6040 0x605f 0x40101
    config[64]
  pci device: name = 0000:00:1d.3
    path = /devices/pci0000:00/0000:00:1d.3
    modalias = "pci:v00008086d000027CBsv00001025sd00000349bc0Csc03i00"
    class = 0xc0300
    vendor = 0x8086
    device = 0x27cb
    subvendor = 0x1025
    subdevice = 0x349
    irq = 22
    res[4] = 0x6020 0x603f 0x40101
    config[64]
  pci device: name = 0000:00:1d.7
    path = /devices/pci0000:00/0000:00:1d.7
    modalias = "pci:v00008086d000027CCsv00001025sd00000349bc0Csc03i20"
    class = 0xc0320
    vendor = 0x8086
    device = 0x27cc
    subvendor = 0x1025
    subdevice = 0x349
    irq = 22
    res[0] = 0x58204400 0x582047ff 0x40200
    config[64]
  pci device: name = 0000:00:1e.0
    path = /devices/pci0000:00/0000:00:1e.0
    modalias = "pci:v00008086d00002448sv00001025sd00000349bc06sc04i01"
    class = 0x60401
    vendor = 0x8086
    device = 0x2448
    subvendor = 0x1025
    subdevice = 0x349
    irq = 0
    config[64]
  pci device: name = 0000:00:1f.0
    path = /devices/pci0000:00/0000:00:1f.0
    modalias = "pci:v00008086d000027BCsv00001025sd00000349bc06sc01i00"
    class = 0x60100
    vendor = 0x8086
    device = 0x27bc
    subvendor = 0x1025
    subdevice = 0x349
    irq = 0
    config[64]
  pci device: name = 0000:00:1f.2
    path = /devices/pci0000:00/0000:00:1f.2
    modalias = "pci:v00008086d000027C1sv00001025sd00000349bc01sc06i01"
    class = 0x10601
    vendor = 0x8086
    device = 0x27c1
    subvendor = 0x1025
    subdevice = 0x349
    irq = 42
    res[0] = 0x60b8 0x60bf 0x40101
    res[1] = 0x60cc 0x60cf 0x40101
    res[2] = 0x60b0 0x60b7 0x40101
    res[3] = 0x60c8 0x60cb 0x40101
    res[4] = 0x60a0 0x60af 0x40101
    res[5] = 0x58204000 0x582043ff 0x40200
    config[64]
  pci device: name = 0000:00:1f.3
    path = /devices/pci0000:00/0000:00:1f.3
    modalias = "pci:v00008086d000027DAsv00001025sd00000349bc0Csc05i00"
    class = 0xc0500
    vendor = 0x8086
    device = 0x27da
    subvendor = 0x1025
    subdevice = 0x349
    irq = 10
    res[4] = 0x6000 0x601f 0x40101
    config[64]
  pci device: name = 0000:01:00.0
    path = /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
    modalias = "pci:v00001969d00002060sv00001025sd00000349bc02sc00i00"
    class = 0x20000
    vendor = 0x1969
    device = 0x2060
    subvendor = 0x1025
    subdevice = 0x349
    irq = 45
    res[0] = 0x57000000 0x5703ffff 0x140204
    res[2] = 0x5000 0x507f 0x40101
    config[64]
  pci device: name = 0000:02:00.0
    path = /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
    modalias = "pci:v000014E4d00004727sv000014E4sd00000510bc02sc80i00"
    class = 0x28000
    vendor = 0x14e4
    device = 0x4727
    subvendor = 0x14e4
    subdevice = 0x510
    irq = 17
    res[0] = 0x56000000 0x56003fff 0x140204
    config[64]
---------- PCI raw data ----------
bus 00, slot 00, func 0, vend:dev:s_vend:s_dev:rev 8086:a010:1025:0349:00
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 86 80 10 a0 06 00 90 20 00 00 00 06 00 00 00 00  "....... ........"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 25 10 49 03  "............%.I."
  30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 02, func 0, vend:dev:s_vend:s_dev:rev 8086:a011:1025:0349:00
class 03, sub_class 00 prog_if 00, hdr 0, flags <>, irq 43
  addr0 58180000, size 00080000
  addr1 000060c0, size 00000008
  addr2 40000000, size 10000000
  addr3 58000000, size 00100000
  00: 86 80 11 a0 07 04 90 00 00 00 00 03 00 00 80 00  "................"
  10: 00 00 18 58 c1 60 00 00 08 00 00 40 00 00 00 58  "...X.`.....@...X"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 25 10 49 03  "............%.I."
  30: 00 00 00 00 90 00 00 00 00 00 00 00 0b 01 00 00  "................"

bus 00, slot 02, func 1, vend:dev:s_vend:s_dev:rev 8086:a012:1025:0349:00
class 03, sub_class 80 prog_if 00, hdr 0, flags <>, irq 0
  addr0 58100000, size 00080000
  00: 86 80 12 a0 07 00 90 00 00 00 80 03 00 00 80 00  "................"
  10: 00 00 10 58 00 00 00 00 00 00 00 00 00 00 00 00  "...X............"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 25 10 49 03  "............%.I."
  30: 00 00 00 00 d0 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 1b, func 0, vend:dev:s_vend:s_dev:rev 8086:27d8:1025:0349:02
class 04, sub_class 03 prog_if 00, hdr 0, flags <>, irq 44
  addr0 58200000, size 00004000
  00: 86 80 d8 27 06 04 10 00 02 00 03 04 10 00 00 00  "...'............"
  10: 04 00 20 58 00 00 00 00 00 00 00 00 00 00 00 00  ".. X............"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 25 10 49 03  "............%.I."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0b 01 00 00  "....P..........."

bus 00->01, slot 1c, func 0, vend:dev:s_vend:s_dev:rev 8086:27d0:1025:0349:02
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 40
  00: 86 80 d0 27 07 04 10 00 02 00 04 06 10 00 81 00  "...'............"
  10: 00 00 00 00 00 00 00 00 00 01 01 00 50 50 00 00  "............PP.."
  20: 00 57 f0 57 01 50 f1 50 00 00 00 00 00 00 00 00  ".W.W.P.P........"
  30: 00 00 00 00 40 00 00 00 00 00 00 00 ff 01 00 00  "....@..........."

bus 00->02, slot 1c, func 1, vend:dev:s_vend:s_dev:rev 8086:27d2:1025:0349:02
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 41
  00: 86 80 d2 27 07 04 10 00 02 00 04 06 10 00 81 00  "...'............"
  10: 00 00 00 00 00 00 00 00 00 02 02 00 40 40 00 00  "............@@.."
  20: 00 56 f0 56 01 51 f1 51 00 00 00 00 00 00 00 00  ".V.V.Q.Q........"
  30: 00 00 00 00 40 00 00 00 00 00 00 00 ff 02 00 00  "....@..........."

bus 00, slot 1d, func 0, vend:dev:s_vend:s_dev:rev 8086:27c8:1025:0349:02
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 18
  addr4 00006080, size 00000020
  00: 86 80 c8 27 05 00 80 02 02 00 03 0c 00 00 80 00  "...'............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 81 60 00 00 00 00 00 00 00 00 00 00 25 10 49 03  ".`..........%.I."
  30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 01 00 00  "................"

bus 00, slot 1d, func 1, vend:dev:s_vend:s_dev:rev 8086:27c9:1025:0349:02
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 20
  addr4 00006060, size 00000020
  00: 86 80 c9 27 05 00 80 02 02 00 03 0c 00 00 00 00  "...'............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 61 60 00 00 00 00 00 00 00 00 00 00 25 10 49 03  "a`..........%.I."
  30: 00 00 00 00 00 00 00 00 00 00 00 00 0a 02 00 00  "................"

bus 00, slot 1d, func 2, vend:dev:s_vend:s_dev:rev 8086:27ca:1025:0349:02
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 21
  addr4 00006040, size 00000020
  00: 86 80 ca 27 05 00 80 02 02 00 03 0c 00 00 00 00  "...'............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 41 60 00 00 00 00 00 00 00 00 00 00 25 10 49 03  "A`..........%.I."
  30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 03 00 00  "................"

bus 00, slot 1d, func 3, vend:dev:s_vend:s_dev:rev 8086:27cb:1025:0349:02
class 0c, sub_class 03 prog_if 00, hdr 0, flags <>, irq 22
  addr4 00006020, size 00000020
  00: 86 80 cb 27 05 00 80 02 02 00 03 0c 00 00 00 00  "...'............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 21 60 00 00 00 00 00 00 00 00 00 00 25 10 49 03  "!`..........%.I."
  30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 04 00 00  "................"

bus 00, slot 1d, func 7, vend:dev:s_vend:s_dev:rev 8086:27cc:1025:0349:02
class 0c, sub_class 03 prog_if 20, hdr 0, flags <>, irq 22
  addr0 58204400, size 00000400
  00: 86 80 cc 27 06 00 90 02 02 20 03 0c 00 00 00 00  "...'..... ......"
  10: 00 44 20 58 00 00 00 00 00 00 00 00 00 00 00 00  ".D X............"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 25 10 49 03  "............%.I."
  30: 00 00 00 00 50 00 00 00 00 00 00 00 0b 04 00 00  "....P..........."

bus 00->05, slot 1e, func 0, vend:dev:s_vend:s_dev:rev 8086:2448:1025:0349:e2
class 06, sub_class 04 prog_if 01, hdr 1, flags <>, irq 0
  00: 86 80 48 24 07 00 10 00 e2 01 04 06 00 00 01 00  "..H$............"
  10: 00 00 00 00 00 00 00 00 00 05 05 20 f0 00 80 22  "........... ...""
  20: f0 ff 00 00 f1 ff 01 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 50 00 00 00 00 00 00 00 ff 00 00 00  "....P..........."

bus 00, slot 1f, func 0, vend:dev:s_vend:s_dev:rev 8086:27bc:1025:0349:02
class 06, sub_class 01 prog_if 00, hdr 0, flags <>, irq 0
  00: 86 80 bc 27 07 00 10 02 02 00 01 06 00 00 80 00  "...'............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 25 10 49 03  "............%.I."
  30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 1f, func 2, vend:dev:s_vend:s_dev:rev 8086:27c1:1025:0349:02
class 01, sub_class 06 prog_if 01, hdr 0, flags <>, irq 42
  addr0 000060b8, size 00000008
  addr1 000060cc, size 00000004
  addr2 000060b0, size 00000008
  addr3 000060c8, size 00000004
  addr4 000060a0, size 00000010
  addr5 58204000, size 00000400
  00: 86 80 c1 27 07 04 b0 02 02 01 06 01 00 00 00 00  "...'............"
  10: b9 60 00 00 cd 60 00 00 b1 60 00 00 c9 60 00 00  ".`...`...`...`.."
  20: a1 60 00 00 00 40 20 58 00 00 00 00 25 10 49 03  ".`...@ X....%.I."
  30: 00 00 00 00 80 00 00 00 00 00 00 00 0a 02 00 00  "................"

bus 00, slot 1f, func 3, vend:dev:s_vend:s_dev:rev 8086:27da:1025:0349:02
class 0c, sub_class 05 prog_if 00, hdr 0, flags <>, irq 10
  addr4 00006000, size 00000020
  00: 86 80 da 27 01 00 80 02 02 00 05 0c 00 00 00 00  "...'............"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 01 60 00 00 00 00 00 00 00 00 00 00 25 10 49 03  ".`..........%.I."
  30: 00 00 00 00 00 00 00 00 00 00 00 00 0a 02 00 00  "................"

bus 01, slot 00, func 0, vend:dev:s_vend:s_dev:rev 1969:2060:1025:0349:c1
class 02, sub_class 00 prog_if 00, hdr 0, flags <>, irq 45
  addr0 57000000, size 00040000
  addr2 00005000, size 00000080
  00: 69 19 60 20 07 04 10 00 c1 00 00 02 10 00 00 00  "i.` ............"
  10: 04 00 00 57 00 00 00 00 01 50 00 00 00 00 00 00  "...W.....P......"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 25 10 49 03  "............%.I."
  30: 00 00 00 00 40 00 00 00 00 00 00 00 0b 01 00 00  "....@..........."

bus 02, slot 00, func 0, vend:dev:s_vend:s_dev:rev 14e4:4727:14e4:0510:01
class 02, sub_class 80 prog_if 00, hdr 0, flags <>, irq 17
  addr0 56000000, size 00004000
  00: e4 14 27 47 06 00 10 00 01 00 80 02 10 00 00 00  "..'G............"
  10: 04 00 00 56 00 00 00 00 00 00 00 00 00 00 00 00  "...V............"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 e4 14 10 05  "................"
  30: 00 00 00 00 40 00 00 00 00 00 00 00 0a 01 00 00  "....@..........."
---------- PCI raw data end ----------
>> pci.4: build list
>> pci.3: macio
sysfs: no such bus: macio
>> pci.4: vio
sysfs: no such bus: vio
>> pci.5: xen
sysfs: no such bus: xen
>> pci.6: ps3
sysfs: no such bus: ps3_system_bus
>> pci.7: platform
  platform device: name = pcspkr
    path = /devices/platform/pcspkr
    type = "platform:pcspkr"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = serial8250
    path = /devices/platform/serial8250
    type = "platform:serial8250"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = Fixed MDIO bus.0
    path = /devices/platform/Fixed MDIO bus.0
    type = "platform:Fixed MDIO bus"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = i8042
    path = /devices/platform/i8042
    type = "platform:i8042"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = eisa.0
    path = /devices/platform/eisa.0
    type = "platform:eisa"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = vboxdrv.0
    path = /devices/platform/vboxdrv.0
    type = "platform:vboxdrv"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
>> pci.8: of_platform
sysfs: no such bus: of_platform
>> pci.9: vm
sysfs: no such bus: vm
>> pci.10: virtio
sysfs: no such bus: virtio
>> pci.11: ibmebus
sysfs: no such bus: ibmebus
>> monitor.1: ddc
>> monitor.2: bios
>> monitor.3: pci
>> monitor.4: internal db
>> monitor.5: prom
>> isapnp.1: pnp devices
  pnp device: name = 00:00
    path = /devices/pnp0/00:00
    id = PNP 0a08
  pnp device: name = 00:01
    path = /devices/pnp0/00:01
    id = PNP 0c02
  pnp device: name = 00:02
    path = /devices/pnp0/00:02
    id = PNP 0200
  pnp device: name = 00:03
    path = /devices/pnp0/00:03
    id = PNP 0b00
  pnp device: name = 00:04
    path = /devices/pnp0/00:04
    id = PNP 0103
  pnp device: name = 00:05
    path = /devices/pnp0/00:05
    id = PNP 0c04
  pnp device: name = 00:06
    path = /devices/pnp0/00:06
    id = INT 0800
  pnp device: name = 00:07
    path = /devices/pnp0/00:07
    id = PNP 0303
  pnp device: name = 00:08
    path = /devices/pnp0/00:08
    id = SYN 1b1c
>> pcmcia.1: sysfs drivers
>> pcmcia.2: pcmcia
sysfs: no such bus: pcmcia
>> pcmcia.3: pcmcia ctrl
sysfs: no such class: pcmcia_socket
>> serial.1: read info
----- serial info -----
----- serial info end -----
>> serial.2: build list
>> misc.5: misc data
----- misc resources -----
i/o:0 0x0000 - 0x0cf7 (0xcf8) "PCI Bus 0000:00"
i/o:1 0x0000 - 0x001f (0x20) "dma1"
i/o:1 0x0020 - 0x0021 (0x02) "pic1"
i/o:0 0x0040 - 0x0043 (0x04) "timer0"
i/o:0 0x0050 - 0x0053 (0x04) "timer1"
i/o:1 0x0060 - 0x0060 (0x01) "keyboard"
i/o:1 0x0064 - 0x0064 (0x01) "keyboard"
i/o:0 0x0070 - 0x0077 (0x08) "rtc0"
i/o:1 0x0080 - 0x008f (0x10) "dma page reg"
i/o:1 0x00a0 - 0x00a1 (0x02) "pic2"
i/o:1 0x00c0 - 0x00df (0x20) "dma2"
i/o:1 0x00f0 - 0x00ff (0x10) "fpu"
i/o:1 0x03c0 - 0x03df (0x20) "vga+"
i/o:0 0x0400 - 0x047f (0x80) "pnp 00:01"
i/o:0 0x0400 - 0x0403 (0x04) "ACPI PM1a_EVT_BLK"
i/o:0 0x0404 - 0x0405 (0x02) "ACPI PM1a_CNT_BLK"
i/o:0 0x0408 - 0x040b (0x04) "ACPI PM_TMR"
i/o:0 0x0410 - 0x0415 (0x06) "ACPI CPU throttle"
i/o:0 0x0420 - 0x0420 (0x01) "ACPI PM2_CNT_BLK"
i/o:0 0x0428 - 0x042f (0x08) "ACPI GPE0_BLK"
i/o:0 0x0500 - 0x053f (0x40) "pnp 00:01"
i/o:0 0x0600 - 0x060f (0x10) "pnp 00:01"
i/o:0 0x0610 - 0x0610 (0x01) "pnp 00:01"
i/o:0 0x0800 - 0x080f (0x10) "pnp 00:01"
i/o:0 0x0810 - 0x0817 (0x08) "pnp 00:01"
i/o:0 0x0cf8 - 0x0cff (0x08) "PCI conf1"
i/o:0 0x0d00 - 0xffff (0xf300) "PCI Bus 0000:00"
i/o:0 0x164e - 0x164f (0x02) "pnp 00:01"
i/o:0 0x4000 - 0x4fff (0x1000) "PCI Bus 0000:02"
i/o:0 0x5000 - 0x5fff (0x1000) "PCI Bus 0000:01"
i/o:0 0x5000 - 0x507f (0x80) "0000:01:00.0"
i/o:0 0x5000 - 0x507f (0x80) "atl1c"
i/o:0 0x6000 - 0x601f (0x20) "0000:00:1f.3"
i/o:0 0x6020 - 0x603f (0x20) "0000:00:1d.3"
i/o:0 0x6020 - 0x603f (0x20) "uhci_hcd"
i/o:0 0x6040 - 0x605f (0x20) "0000:00:1d.2"
i/o:0 0x6040 - 0x605f (0x20) "uhci_hcd"
i/o:0 0x6060 - 0x607f (0x20) "0000:00:1d.1"
i/o:0 0x6060 - 0x607f (0x20) "uhci_hcd"
i/o:0 0x6080 - 0x609f (0x20) "0000:00:1d.0"
i/o:0 0x6080 - 0x609f (0x20) "uhci_hcd"
i/o:0 0x60a0 - 0x60af (0x10) "0000:00:1f.2"
i/o:0 0x60a0 - 0x60af (0x10) "ahci"
i/o:0 0x60b0 - 0x60b7 (0x08) "0000:00:1f.2"
i/o:0 0x60b0 - 0x60b7 (0x08) "ahci"
i/o:0 0x60b8 - 0x60bf (0x08) "0000:00:1f.2"
i/o:0 0x60b8 - 0x60bf (0x08) "ahci"
i/o:0 0x60c0 - 0x60c7 (0x08) "0000:00:02.0"
i/o:0 0x60c8 - 0x60cb (0x04) "0000:00:1f.2"
i/o:0 0x60c8 - 0x60cb (0x04) "ahci"
i/o:0 0x60cc - 0x60cf (0x04) "0000:00:1f.2"
i/o:0 0x60cc - 0x60cf (0x04) "ahci"
i/o:0 0xff2c - 0xff2f (0x04) "pnp 00:01"
irq:1  0 (  9031783) "timer"
irq:0  1 (     5508) "i8042"
irq:0  8 (        1) "rtc0"
irq:0  9 (    39825) "acpi"
irq:0 12 (  1489997) "i8042"
irq:0 17 (   411132) "eth1"
irq:0 18 (        0) "uhci_hcd:usb2"
irq:0 20 (        2) "uhci_hcd:usb3"
irq:0 21 (        2) "uhci_hcd:usb4"
irq:0 22 (       94) "ehci_hcd:usb1" "uhci_hcd:usb5"
irq:0 42 (   128239) "ahci"
irq:0 43 (   187325) "i915@pci:0000:00:02.0"
irq:0 44 (     1492) "hda_intel"
irq:0 45 (        0) "eth0"
dma:1 4 "cascade"
----- misc resources end -----
>> parallel.1: pp mod
----- exec: "/sbin/rmmod lp" -----
  ERROR: Removing 'lp': Operation not permitted
----- return code: ? -----
----- exec: "/sbin/rmmod parport_pc" -----
  ERROR: Removing 'parport_pc': Operation not permitted
----- return code: ? -----
>> parallel.2.1: lp read info
>> parallel.2.2: lp read info
>> parallel.2.3: lp read info
----- parallel info -----
----- parallel info end -----
>> block.1: block modules
----- exec: "/sbin/modprobe ide-cd_mod " -----
  FATAL: Module ide_cd_mod not found.
----- return code: ? -----
----- exec: "/sbin/modprobe ide-disk " -----
  FATAL: Module ide_disk not found.
----- return code: ? -----
----- exec: "/sbin/modprobe sr_mod " -----
----- return code: ? -----
----- exec: "/sbin/modprobe sd_mod " -----
----- return code: ? -----
----- exec: "/sbin/modprobe st " -----
  FATAL: Error inserting st (/lib/modules/2.6.35-28-generic/kernel/drivers/scsi/st.ko): Operation not permitted
----- return code: ? -----
>> block.2: sysfs drivers
>> block.3: cdrom
----- /proc/sys/dev/cdrom/info -----
drive name:	
drive speed:	
drive # of slots:
Can close tray:	
Can open tray:	
Can lock tray:	
Can change speed:
Can select disk:
Can read multisession:
Can read MCN:	
Reports media changed:
Can play audio:	
Can write CD-R:	
Can write CD-RW:
Can read DVD:	
Can write DVD-R:
Can write DVD-RAM:
Can read MRW:	
Can write MRW:	
Can write RAM:	
----- /proc/sys/dev/cdrom/info end -----
>> block.4: partition
----- /proc/partitions -----
     8        0  244198584 sda
     8        1   13733888 sda1
     8        2    1321984 sda2
     8        3  110000000 sda3
     8        4  119140352 sda4
----- /proc/partitions end -----
disks:
  sda
partitions:
  sda1
  sda2
  sda3
  sda4
>> block.5: get sysfs block dev data
-----  lsscsi -----
-----  lsscsi end -----
  block: name = ram0, path = /class/block/ram0
    dev = 1:0
    range = 1
  block: name = ram1, path = /class/block/ram1
    dev = 1:1
    range = 1
  block: name = ram2, path = /class/block/ram2
    dev = 1:2
    range = 1
  block: name = ram3, path = /class/block/ram3
    dev = 1:3
    range = 1
  block: name = ram4, path = /class/block/ram4
    dev = 1:4
    range = 1
  block: name = ram5, path = /class/block/ram5
    dev = 1:5
    range = 1
  block: name = ram6, path = /class/block/ram6
    dev = 1:6
    range = 1
  block: name = ram7, path = /class/block/ram7
    dev = 1:7
    range = 1
  block: name = ram8, path = /class/block/ram8
    dev = 1:8
    range = 1
  block: name = ram9, path = /class/block/ram9
    dev = 1:9
    range = 1
  block: name = ram10, path = /class/block/ram10
    dev = 1:10
    range = 1
  block: name = ram11, path = /class/block/ram11
    dev = 1:11
    range = 1
  block: name = ram12, path = /class/block/ram12
    dev = 1:12
    range = 1
  block: name = ram13, path = /class/block/ram13
    dev = 1:13
    range = 1
  block: name = ram14, path = /class/block/ram14
    dev = 1:14
    range = 1
  block: name = ram15, path = /class/block/ram15
    dev = 1:15
    range = 1
  block: name = loop0, path = /class/block/loop0
    dev = 7:0
    range = 1
  block: name = loop1, path = /class/block/loop1
    dev = 7:1
    range = 1
  block: name = loop2, path = /class/block/loop2
    dev = 7:2
    range = 1
  block: name = loop3, path = /class/block/loop3
    dev = 7:3
    range = 1
  block: name = loop4, path = /class/block/loop4
    dev = 7:4
    range = 1
  block: name = loop5, path = /class/block/loop5
    dev = 7:5
    range = 1
  block: name = loop6, path = /class/block/loop6
    dev = 7:6
    range = 1
  block: name = loop7, path = /class/block/loop7
    dev = 7:7
    range = 1
  block: name = sda, path = /class/block/sda
    dev = 8:0
    range = 16
    block device: bus = scsi, bus_id = 0:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
    vendor = ATA
    model = TOSHIBA MK2565GS
    rev = GJ00
    type = 0
>> block.5: /dev/sda
  block: name = sda1, path = /class/block/sda1
    dev = 8:1
  block: name = sda2, path = /class/block/sda2
    dev = 8:2
  block: name = sda3, path = /class/block/sda3
    dev = 8:3
  block: name = sda4, path = /class/block/sda4
    dev = 8:4
>> scsi.1: scsi modules
----- exec: "/sbin/modprobe sg " -----
----- return code: ? -----
>> scsi.2: scsi tape
sysfs: no such class: scsi_tape
>> scsi.3: scsi generic
  scsi: name = sg0, path = /class/scsi_generic/sg0
    dev = 21:0
    scsi device: bus_id = 0:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
>> usb.1: sysfs drivers
>> usb.2: usb
  usb dev: /devices/pci0000:00/0000:00:1d.7/usb1
  usb dev: /devices/pci0000:00/0000:00:1d.0/usb2
  usb dev: /devices/pci0000:00/0000:00:1d.1/usb3
  usb dev: /devices/pci0000:00/0000:00:1d.2/usb4
  usb dev: /devices/pci0000:00/0000:00:1d.3/usb5
  usb dev: /devices/pci0000:00/0000:00:1d.7/usb1/1-4
  usb dev: /devices/pci0000:00/0000:00:1d.7/usb1/1-5
  usb device: name = usb1
    path = /devices/pci0000:00/0000:00:1d.7/usb1
  usb device: name = 1-0:1.0
    path = /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
    modalias = "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 1-0:1.0 @ /devices/pci0000:00/0000:00:1d.7/usb1
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0002
    manufacturer = "Linux 2.6.35-28-generic ehci_hcd"
    product = "EHCI Host Controller"
    serial = "0000:00:1d.7"
    bcdDevice = 0206
    speed = "480"
  usb device: name = usb2
    path = /devices/pci0000:00/0000:00:1d.0/usb2
  usb device: name = 2-0:1.0
    path = /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
    modalias = "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 2-0:1.0 @ /devices/pci0000:00/0000:00:1d.0/usb2
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 2.6.35-28-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1d.0"
    bcdDevice = 0206
    speed = "12"
  usb device: name = usb3
    path = /devices/pci0000:00/0000:00:1d.1/usb3
  usb device: name = 3-0:1.0
    path = /devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
    modalias = "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 3-0:1.0 @ /devices/pci0000:00/0000:00:1d.1/usb3
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 2.6.35-28-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1d.1"
    bcdDevice = 0206
    speed = "12"
  usb device: name = usb4
    path = /devices/pci0000:00/0000:00:1d.2/usb4
  usb device: name = 4-0:1.0
    path = /devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
    modalias = "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 4-0:1.0 @ /devices/pci0000:00/0000:00:1d.2/usb4
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 2.6.35-28-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1d.2"
    bcdDevice = 0206
    speed = "12"
  usb device: name = usb5
    path = /devices/pci0000:00/0000:00:1d.3/usb5
  usb device: name = 5-0:1.0
    path = /devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
    modalias = "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 5-0:1.0 @ /devices/pci0000:00/0000:00:1d.3/usb5
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 2.6.35-28-generic uhci_hcd"
    product = "UHCI Host Controller"
    serial = "0000:00:1d.3"
    bcdDevice = 0206
    speed = "12"
  usb device: name = 1-4
    path = /devices/pci0000:00/0000:00:1d.7/usb1/1-4
  usb device: name = 1-4:1.0
    path = /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0
    modalias = "usb:v064EpA219d0215dcEFdsc02dp01ic0Eisc01ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 14
    bInterfaceSubClass = 1
    bInterfaceProtocol = 0
    if: 1-4:1.0 @ /devices/pci0000:00/0000:00:1d.7/usb1/1-4
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x064e
    idProduct = 0xa219
    manufacturer = "Suyin"
    product = "1.3M WebCam"
    serial = "HF1315-S32B-OV01-VA-R02.01.05"
    bcdDevice = 0215
    speed = "480"
  usb device: name = 1-4:1.1
    path = /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.1
    modalias = "usb:v064EpA219d0215dcEFdsc02dp01ic0Eisc02ip00"
    bInterfaceNumber = 1
    bInterfaceClass = 14
    bInterfaceSubClass = 2
    bInterfaceProtocol = 0
    if: 1-4:1.1 @ /devices/pci0000:00/0000:00:1d.7/usb1/1-4
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x064e
    idProduct = 0xa219
    manufacturer = "Suyin"
    product = "1.3M WebCam"
    serial = "HF1315-S32B-OV01-VA-R02.01.05"
    bcdDevice = 0215
    speed = "480"
  usb device: name = 1-5
    path = /devices/pci0000:00/0000:00:1d.7/usb1/1-5
  usb device: name = 1-5:1.0
    path = /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0
    modalias = "usb:v0CF2p6250d0100dc00dsc00dp00icFFisc06ip50"
    bInterfaceNumber = 0
    bInterfaceClass = 255
    bInterfaceSubClass = 6
    bInterfaceProtocol = 80
    if: 1-5:1.0 @ /devices/pci0000:00/0000:00:1d.7/usb1/1-5
    bDeviceClass = 0
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x0cf2
    idProduct = 0x6250
    manufacturer = "ENE Flash"
    product = "UB6250"
    serial = "606569746801"
    bcdDevice = 0100
    speed = "480"
removed: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.1
>> usb.3.1: joydev mod
>> usb.3.2: evdev mod
----- exec: "/sbin/modprobe evdev " -----
----- return code: ? -----
>> usb.3.3: input
  input: name = input0, path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
    no dev - ignored
  input: name = input1, path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
    no dev - ignored
  input: name = input2, path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
    no dev - ignored
  input: name = input3, path = /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
    no dev - ignored
  input: name = mice, path = /devices/virtual/input/mice
    dev = 13:63
  input: name = event0, path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0
    dev = 13:64
    input device: bus = acpi, bus_id = PNP0C0C:00 driver = button
      path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00
  input: name = event1, path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1
    dev = 13:65
    input device: bus = acpi, bus_id = PNP0C0E:00 driver = button
      path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00
  input: name = event2, path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2/event2
    dev = 13:66
    input device: bus = acpi, bus_id = PNP0C0D:00 driver = button
      path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00
  input: name = event3, path = /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3
    dev = 13:67
    input device: bus = acpi, bus_id = LNXPWRBN:00 driver = button
      path = /devices/LNXSYSTM:00/LNXPWRBN:00
  input: name = input4, path = /devices/platform/i8042/serio0/input/input4
    no dev - ignored
  input: name = event4, path = /devices/platform/i8042/serio0/input/input4/event4
    dev = 13:68
    input device: bus = serio, bus_id = serio0 driver = atkbd
      path = /devices/platform/i8042/serio0
  input: name = input5, path = /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5
    no dev - ignored
  input: name = event5, path = /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5/event5
    dev = 13:69
    input device: bus = usb, bus_id = 1-4:1.0 driver = uvcvideo
      path = /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0
  input: name = input6, path = /devices/platform/i8042/serio1/input/input6
    no dev - ignored
  input: name = mouse0, path = /devices/platform/i8042/serio1/input/input6/mouse0
    dev = 13:32
    input device: bus = serio, bus_id = serio1 driver = psmouse
      path = /devices/platform/i8042/serio1
  input: name = event6, path = /devices/platform/i8042/serio1/input/input6/event6
    dev = 13:70
    input device: bus = serio, bus_id = serio1 driver = psmouse
      path = /devices/platform/i8042/serio1
  input: name = input7, path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
    no dev - ignored
  input: name = event7, path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7/event7
    dev = 13:71
    input device: bus = acpi, bus_id = LNXVIDEO:00 driver = video
      path = /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00
>> usb.3.4: lp
sysfs: no such class: usb
>> usb.3.5: serial
>> edd.1: edd mod
----- exec: "/sbin/modprobe edd " -----
----- return code: ? -----
>> edd.2: edd info
>> modem.1: serial
******  started child process 4892 (15s/120s)  ******
******  stopped child process 4892 (120s)  ******
>> mouse.2: serial
******  started child process 4893 (20s/20s)  ******
******  stopped child process 4893 (20s)  ******
>> input.1: joydev mod
>> input.1.1: evdev mod
----- exec: "/sbin/modprobe evdev " -----
----- return code: ? -----
>> input.2: input
----- /proc/bus/input/devices -----
  I: Bus=0019 Vendor=0000 Product=0001 Version=0000
  N: Name="Power Button"
  P: Phys=PNP0C0C/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
  U: Uniq=
  H: Handlers=kbd event0 
  B: EV=3
  B: KEY=100000 0 0 0
  
  I: Bus=0019 Vendor=0000 Product=0003 Version=0000
  N: Name="Sleep Button"
  P: Phys=PNP0C0E/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
  U: Uniq=
  H: Handlers=kbd event1 
  B: EV=3
  B: KEY=4000 0 0 0 0
  
  I: Bus=0019 Vendor=0000 Product=0005 Version=0000
  N: Name="Lid Switch"
  P: Phys=PNP0C0D/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
  U: Uniq=
  H: Handlers=event2 
  B: EV=21
  B: SW=1
  
  I: Bus=0019 Vendor=0000 Product=0001 Version=0000
  N: Name="Power Button"
  P: Phys=LNXPWRBN/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
  U: Uniq=
  H: Handlers=kbd event3 
  B: EV=3
  B: KEY=100000 0 0 0
  
  I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
  N: Name="AT Translated Set 2 keyboard"
  P: Phys=isa0060/serio0/input0
  S: Sysfs=/devices/platform/i8042/serio0/input/input4
  U: Uniq=
  H: Handlers=sysrq kbd event4 
  B: EV=120013
  B: KEY=10000 c0200 0 0 0 0 0 700f 2000003 3803078 f830f401 febfffdf ffefffff ffffffff fffffffe
  B: MSC=10
  B: LED=7
  
  I: Bus=0003 Vendor=064e Product=a219 Version=0215
  N: Name="1.3M WebCam"
  P: Phys=usb-0000:00:1d.7-4/button
  S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5
  U: Uniq=
  H: Handlers=kbd event5 
  B: EV=3
  B: KEY=100000 0 0 0 0 0 0
  
  I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
  N: Name="SynPS/2 Synaptics TouchPad"
  P: Phys=isa0060/serio1/input0
  S: Sysfs=/devices/platform/i8042/serio1/input/input6
  U: Uniq=
  H: Handlers=mouse0 event6 
  B: EV=b
  B: KEY=420 0 30000 0 0 0 0 0 0 0 0
  B: ABS=11000003
  
  I: Bus=0019 Vendor=0000 Product=0006 Version=0000
  N: Name="Video Bus"
  P: Phys=LNXVIDEO/video/input0
  S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
  U: Uniq=
  H: Handlers=kbd event7 
  B: EV=3
  B: KEY=3e000b 0 0 0 0 0 0 0
  
----- /proc/bus/input/devices end -----
bus = 25, name = Power Button
  handlers = kbd event0
  key = 00100000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Sleep Button
  handlers = kbd event1
  key = 0000400000000000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Lid Switch
  handlers = event2
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Power Button
  handlers = kbd event3
  key = 00100000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 17, name = AT Translated Set 2 keyboard
  handlers = sysrq kbd event4
  key = 00010000000c020000000000000000000000000000000000000000000000700f0200000303803078f830f401febfffdfffeffffffffffffffffffffe
  mouse buttons = 0
  mouse wheels = 0
bus = 3, name = 1.3M WebCam
  handlers = kbd event5
  key = 00100000000000000000000000000000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 17, name = SynPS/2 Synaptics TouchPad
  handlers = mouse0 event6
  key = 0000042000000000000300000000000000000000000000000000000000000000000000000000000000000000
  abs = 11000003
  mouse buttons = 2
  mouse wheels = 0
bus = 25, name = Video Bus
  handlers = kbd event7
  key = 003e000b00000000000000000000000000000000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
>> kbd.2: uml
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 28
  model name	: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
  stepping	: 10
  cpu MHz		: 1666.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 2
  core id		: 0
  cpu cores	: 1
  apicid		: 0
  initial apicid	: 0
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 10
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
  bogomips	: 3324.37
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 32 bits physical, 48 bits virtual
  power management:
  
  processor	: 1
  vendor_id	: GenuineIntel
  cpu family	: 6
  model		: 28
  model name	: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
  stepping	: 10
  cpu MHz		: 1000.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 2
  core id		: 0
  cpu cores	: 1
  apicid		: 1
  initial apicid	: 1
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 10
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
  bogomips	: 3325.08
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 32 bits physical, 48 bits virtual
  power management:
  
----- /proc/cpuinfo end -----
>> kbd.3: serial console
>> fb.1: read info
>> net.1: get network data
  net interface: name = lo, path = /class/net/lo
    type = 772
    carrier = 1
    hw_addr = 00:00:00:00:00:00
    GDRVINFO ethtool error: Operation not supported
  net interface: name = eth0, path = /class/net/eth0
    type = 1
    carrier = 0
    hw_addr = 1c:75:08:ba:16:6c
    net device: path = /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
    net driver: name = atl1c, path = /bus/pci/drivers/atl1c
  net interface: name = eth1, path = /class/net/eth1
    type = 1
    carrier = 1
    hw_addr = 88:9f:fa:1c:24:3b
    net device: path = /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
    net driver: name = wl, path = /bus/pci/drivers/wl
  net interface: name = vboxnet0, path = /class/net/vboxnet0
    type = 1
    hw_addr = 0a:00:27:00:00:00
    GDRVINFO ethtool error: Operation not supported
>> net.2: eeprom dump
>> net.2: eeprom dump
>> net.2: eeprom dump
>> net.2: eeprom dump
  vboxnet0: GLINK ethtool error: Operation not supported
>> pppoe.1: looking for pppoe
>> pppoe.2: discovery
eth0: socket failed: Operation not permitted
eth1: socket failed: Operation not permitted
vboxnet0: socket failed: Operation not permitted
>> wlan.1: detecting wlan features
>> wlan.2: assign udi
>> isdn.1: list
>> dsl.1: list
>> int.2: cdrom
>> int.3: media
>> int.4.1: /dev/sda
  read_block0: open(/dev/sda) failed
>> int.4: floppy
>> int.5: edd
>> int.5.1: bios
  bios ctrl 0: 24
>> int.6: mouse
>> int.15: system info
  system type:
  acpi: 1
>> int.7: hdb
>> int.7.1: modules
>> int.8: usbscsi
>> int.9: hotplug
>> int.10: modem
>> int.11: wlan
>> int.12: udev
-----  udevinfo -----
  P: /devices/LNXSYSTM:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:LNXSYSTM:
  
  P: /devices/LNXSYSTM:00/LNXCPU:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:00
  E: SUBSYSTEM=acpi
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  
  P: /devices/LNXSYSTM:00/LNXCPU:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:01
  E: SUBSYSTEM=acpi
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  
  P: /devices/LNXSYSTM:00/LNXCPU:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:02
  E: SUBSYSTEM=acpi
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  
  P: /devices/LNXSYSTM:00/LNXCPU:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:03
  E: SUBSYSTEM=acpi
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  
  P: /devices/LNXSYSTM:00/LNXPWRBN:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00
  E: SUBSYSTEM=acpi
  E: DRIVER=button
  E: MODALIAS=acpi:LNXPWRBN:
  
  P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
  E: SUBSYSTEM=input
  E: PRODUCT=19/0/1/0
  E: NAME="Power Button"
  E: PHYS="LNXPWRBN/button/input0"
  E: EV==3
  E: KEY==100000 0 0 0
  E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
  
  P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3
  N: input/event3
  S: char/13:67
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3
  E: SUBSYSTEM=input
  E: DEVNAME=input/event3
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: XKBMODEL=pc105
  E: XKBLAYOUT=latam
  E: MAJOR=13
  E: MINOR=67
  E: DEVLINKS=/dev/char/13:67
  E: DMI_VENDOR=Acer
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:LNXSYBUS:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00
  E: SUBSYSTEM=acpi
  E: DRIVER=pci_root
  E: MODALIAS=acpi:PNP0A08:PNP0A03:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00
  E: SUBSYSTEM=acpi
  E: DRIVER=video
  E: MODALIAS=acpi:LNXVIDEO:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:26
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:26
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:27
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:27
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:28
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:28
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:29
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:29
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:2a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:2a
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
  E: SUBSYSTEM=input
  E: PRODUCT=19/0/6/0
  E: NAME="Video Bus"
  E: PHYS="LNXVIDEO/video/input0"
  E: EV==3
  E: KEY==3e000b 0 0 0 0 0 0 0
  E: MODALIAS=input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7/event7
  N: input/event7
  S: char/13:71
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7/event7
  E: SUBSYSTEM=input
  E: DEVNAME=input/event7
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: XKBMODEL=pc105
  E: XKBLAYOUT=latam
  E: MAJOR=13
  E: MINOR=71
  E: DEVLINKS=/dev/char/13:71
  E: DMI_VENDOR=Acer
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C14:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C14:00
  E: SUBSYSTEM=acpi
  E: DRIVER=wmi
  E: MODALIAS=acpi:PNP0C14:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/ACPI0003:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/ACPI0003:00
  E: SUBSYSTEM=acpi
  E: DRIVER=ac
  E: MODALIAS=acpi:ACPI0003:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/ACPI0003:00/power_supply/AC
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/ACPI0003:00/power_supply/AC
  E: SUBSYSTEM=power_supply
  E: POWER_SUPPLY_NAME=AC
  E: POWER_SUPPLY_ONLINE=1
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/INT0800:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/INT0800:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:INT0800:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0000:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0000:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:PNP0000:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0100:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0100:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:PNP0100:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0103:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0103:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:PNP0103:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0200:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0200:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:PNP0200:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0303:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0303:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:PNP0303:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0B00:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0B00:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:PNP0B00:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C02:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C02:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:PNP0C02:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C04:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C04:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:PNP0C04:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C09:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C09:00
  E: SUBSYSTEM=acpi
  E: DRIVER=ec
  E: MODALIAS=acpi:PNP0C09:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00
  E: SUBSYSTEM=acpi
  E: DRIVER=battery
  E: MODALIAS=acpi:PNP0C0A:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
  E: SUBSYSTEM=power_supply
  E: POWER_SUPPLY_NAME=BAT0
  E: POWER_SUPPLY_STATUS=Charging
  E: POWER_SUPPLY_PRESENT=1
  E: POWER_SUPPLY_TECHNOLOGY=Li-ion
  E: POWER_SUPPLY_CYCLE_COUNT=0
  E: POWER_SUPPLY_VOLTAGE_MIN_DESIGN=11100000
  E: POWER_SUPPLY_VOLTAGE_NOW=11970000
  E: POWER_SUPPLY_CURRENT_NOW=0
  E: POWER_SUPPLY_CHARGE_FULL_DESIGN=2200000
  E: POWER_SUPPLY_CHARGE_FULL=2132000
  E: POWER_SUPPLY_CHARGE_NOW=1258000
  E: POWER_SUPPLY_MODEL_NAME=AL10A31
  E: POWER_SUPPLY_MANUFACTURER=SANYO 
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:00
  E: SUBSYSTEM=acpi
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:01
  E: SUBSYSTEM=acpi
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:02
  E: SUBSYSTEM=acpi
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:03
  E: SUBSYSTEM=acpi
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:04
  E: SUBSYSTEM=acpi
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:05
  E: SUBSYSTEM=acpi
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:06
  E: SUBSYSTEM=acpi
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:07
  E: SUBSYSTEM=acpi
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/SYN1B1C:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/SYN1B1C:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:SYN1B1C:SYN1B00:SYN0002:PNP0F13:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:03
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/device:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/device:05
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/device:05/device:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/device:05/device:06
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/device:05/device:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/device:05/device:07
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/device:09
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/device:09
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/device:09/device:0a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/device:09/device:0a
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/device:09/device:0b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/device:09/device:0b
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d/device:0e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d/device:0e
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d/device:0f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d/device:0f
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d/device:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d/device:10
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d/device:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d/device:11
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/device:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/device:13
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:14
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:14/device:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:14/device:15
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:16
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:16/device:17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:16/device:17
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:18
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:18
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:18/device:19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:18/device:19
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1a
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1b
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:1e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:1e
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:1e/device:1f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:1e/device:1f
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:1e/device:20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:1e/device:20
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:21
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:21/device:22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:21/device:22
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:21/device:23
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:21/device:23
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:24
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:24
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:25
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:25
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:device:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00
  E: SUBSYSTEM=acpi
  E: DRIVER=button
  E: MODALIAS=acpi:PNP0C0C:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
  E: SUBSYSTEM=input
  E: PRODUCT=19/0/1/0
  E: NAME="Power Button"
  E: PHYS="PNP0C0C/button/input0"
  E: EV==3
  E: KEY==100000 0 0 0
  E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0
  N: input/event0
  S: char/13:64
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0
  E: SUBSYSTEM=input
  E: DEVNAME=input/event0
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: XKBMODEL=pc105
  E: XKBLAYOUT=latam
  E: MAJOR=13
  E: MINOR=64
  E: DEVLINKS=/dev/char/13:64
  E: DMI_VENDOR=Acer
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00
  E: SUBSYSTEM=acpi
  E: DRIVER=button
  E: MODALIAS=acpi:PNP0C0D:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
  E: SUBSYSTEM=input
  E: PRODUCT=19/0/5/0
  E: NAME="Lid Switch"
  E: PHYS="PNP0C0D/button/input0"
  E: EV==21
  E: SW==1
  E: MODALIAS=input:b0019v0000p0005e0000-e0,5,kramlsfw0,
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2/event2
  N: input/event2
  S: char/13:66
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2/event2
  E: SUBSYSTEM=input
  E: DEVNAME=input/event2
  E: ID_INPUT=1
  E: DMI_VENDOR=Acer
  E: MAJOR=13
  E: MINOR=66
  E: DEVLINKS=/dev/char/13:66
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00
  E: SUBSYSTEM=acpi
  E: DRIVER=button
  E: MODALIAS=acpi:PNP0C0E:
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
  E: SUBSYSTEM=input
  E: PRODUCT=19/0/3/0
  E: NAME="Sleep Button"
  E: PHYS="PNP0C0E/button/input0"
  E: EV==3
  E: KEY==4000 0 0 0 0
  E: MODALIAS=input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw
  
  P: /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1
  N: input/event1
  S: char/13:65
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1
  E: SUBSYSTEM=input
  E: DEVNAME=input/event1
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: XKBMODEL=pc105
  E: XKBLAYOUT=latam
  E: MAJOR=13
  E: MINOR=65
  E: DEVLINKS=/dev/char/13:65
  E: DMI_VENDOR=Acer
  
  P: /devices/LNXSYSTM:00/LNXTHERM:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXTHERM:00
  E: SUBSYSTEM=acpi
  E: MODALIAS=acpi:LNXTHERM:
  
  P: /devices/LNXSYSTM:00/LNXTHERM:00/LNXPOWER:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXTHERM:00/LNXPOWER:00
  E: SUBSYSTEM=acpi
  E: DRIVER=power
  E: MODALIAS=acpi:LNXPOWER:
  
  P: /devices/LNXSYSTM:00/LNXTHERM:00/LNXTHERM:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXTHERM:00/LNXTHERM:01
  E: SUBSYSTEM=acpi
  E: DRIVER=thermal
  E: MODALIAS=acpi:LNXTHERM:
  
  P: /devices/LNXSYSTM:00/LNXTHERM:00/PNP0C0B:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXTHERM:00/PNP0C0B:00
  E: SUBSYSTEM=acpi
  E: DRIVER=fan
  E: MODALIAS=acpi:PNP0C0B:
  
  P: /devices/pci0000:00/0000:00:00.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:00.0
  E: SUBSYSTEM=pci
  E: DRIVER=agpgart-intel
  E: PCI_CLASS=60000
  E: PCI_ID=8086:A010
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:00.0
  E: MODALIAS=pci:v00008086d0000A010sv00001025sd00000349bc06sc00i00
  
  P: /devices/pci0000:00/0000:00:02.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0
  E: SUBSYSTEM=pci
  E: DRIVER=i915
  E: PCI_CLASS=30000
  E: PCI_ID=8086:A011
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:02.0
  E: MODALIAS=pci:v00008086d0000A011sv00001025sd00000349bc03sc00i00
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0
  N: dri/card0
  S: char/226:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0
  E: SUBSYSTEM=drm
  E: DEVNAME=dri/card0
  E: MAJOR=226
  E: MINOR=0
  E: DEVTYPE=drm_minor
  E: DEVLINKS=/dev/char/226:0
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1
  E: SUBSYSTEM=drm
  
  P: /devices/pci0000:00/0000:00:02.0/drm/controlD64
  N: dri/controlD64
  S: char/226:64
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/controlD64
  E: SUBSYSTEM=drm
  E: DEVNAME=/dev/dri/controlD64
  E: MAJOR=226
  E: MINOR=64
  E: DEVTYPE=drm_minor
  E: DEVLINKS=/dev/char/226:64
  
  P: /devices/pci0000:00/0000:00:02.0/graphics/fb0
  N: fb0
  S: char/29:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/graphics/fb0
  E: SUBSYSTEM=graphics
  E: DEVNAME=/dev/fb0
  E: MAJOR=29
  E: MINOR=0
  E: DEVLINKS=/dev/char/29:0
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-0
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.0/i2c-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/i2c-1
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:02.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.1
  E: SUBSYSTEM=pci
  E: PCI_CLASS=38000
  E: PCI_ID=8086:A012
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:02.1
  E: MODALIAS=pci:v00008086d0000A012sv00001025sd00000349bc03sc80i00
  
  P: /devices/pci0000:00/0000:00:1b.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0
  E: SUBSYSTEM=pci
  E: DRIVER=HDA Intel
  E: PCI_CLASS=40300
  E: PCI_ID=8086:27D8
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:1b.0
  E: MODALIAS=pci:v00008086d000027D8sv00001025sd00000349bc04sc03i00
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0
  E: SUBSYSTEM=sound
  E: SOUND_INITIALIZED=1
  E: ID_VENDOR_FROM_DATABASE=Intel Corporation
  E: ID_MODEL_FROM_DATABASE=N10/ICH 7 Family High Definition Audio Controller
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x8086
  E: ID_MODEL_ID=0x27d8
  E: ID_PATH=pci-0000:00:1b.0
  E: SOUND_FORM_FACTOR=internal
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
  N: snd/hwC0D0
  S: char/116:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
  E: SUBSYSTEM=sound
  E: DEVNAME=snd/hwC0D0
  E: MAJOR=116
  E: MINOR=6
  E: DEVLINKS=/dev/char/116:6
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  N: snd/pcmC0D0c
  S: char/116:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  E: SUBSYSTEM=sound
  E: DEVNAME=snd/pcmC0D0c
  E: MAJOR=116
  E: MINOR=5
  E: DEVLINKS=/dev/char/116:5
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  N: snd/pcmC0D0p
  S: char/116:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  E: SUBSYSTEM=sound
  E: DEVNAME=snd/pcmC0D0p
  E: MAJOR=116
  E: MINOR=4
  E: DEVLINKS=/dev/char/116:4
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  N: snd/controlC0
  S: char/116:7
  S: snd/by-path/pci-0000:00:1b.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  E: SUBSYSTEM=sound
  E: DEVNAME=snd/controlC0
  E: ID_PATH=pci-0000:00:1b.0
  E: MAJOR=116
  E: MINOR=7
  E: DEVLINKS=/dev/char/116:7 /dev/snd/by-path/pci-0000:00:1b.0
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1c.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0
  E: SUBSYSTEM=pci
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=8086:27D0
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:1c.0
  E: MODALIAS=pci:v00008086d000027D0sv00001025sd00000349bc06sc04i00
  
  P: /devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie01
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie04
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie08
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:01:00.0
  E: SUBSYSTEM=pci
  E: DRIVER=atl1c
  E: PCI_CLASS=20000
  E: PCI_ID=1969:2060
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:01:00.0
  E: MODALIAS=pci:v00001969d00002060sv00001025sd00000349bc02sc00i00
  
  P: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
  E: SUBSYSTEM=net
  E: ID_VENDOR_FROM_DATABASE=Atheros Communications
  E: ID_MODEL_FROM_DATABASE=AR8152 v1.1 Fast Ethernet
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x1969
  E: ID_MODEL_ID=0x2060
  E: INTERFACE=eth0
  E: IFINDEX=2
  
  P: /devices/pci0000:00/0000:00:1c.0/pci_bus/0000:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.0/pci_bus/0000:01
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1c.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1
  E: SUBSYSTEM=pci
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=8086:27D2
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:1c.1
  E: MODALIAS=pci:v00008086d000027D2sv00001025sd00000349bc06sc04i00
  
  P: /devices/pci0000:00/0000:00:1c.1/0000:00:1c.1:pcie01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1/0000:00:1c.1:pcie01
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.1/0000:00:1c.1:pcie04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1/0000:00:1c.1:pcie04
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.1/0000:00:1c.1:pcie08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1/0000:00:1c.1:pcie08
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1/0000:02:00.0
  E: SUBSYSTEM=pci
  E: DRIVER=wl
  E: PCI_CLASS=28000
  E: PCI_ID=14E4:4727
  E: PCI_SUBSYS_ID=14E4:0510
  E: PCI_SLOT_NAME=0000:02:00.0
  E: MODALIAS=pci:v000014E4d00004727sv000014E4sd00000510bc02sc80i00
  
  P: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth1
  E: SUBSYSTEM=net
  E: ID_VENDOR_FROM_DATABASE=Broadcom Corporation
  E: ID_MODEL_FROM_DATABASE=BCM4313 802.11b/g LP-PHY
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x14e4
  E: ID_MODEL_ID=0x4727
  E: INTERFACE=eth1
  E: IFINDEX=3
  
  P: /devices/pci0000:00/0000:00:1c.1/pci_bus/0000:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1c.1/pci_bus/0000:02
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1d.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0
  E: SUBSYSTEM=pci
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:27C8
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:1d.0
  E: MODALIAS=pci:v00008086d000027C8sv00001025sd00000349bc0Csc03i00
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2
  N: bus/usb/002/001
  S: char/189:128
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2
  E: SUBSYSTEM=usb
  E: DEVNAME=bus/usb/002/001
  E: ID_VENDOR=Linux_2.6.35-28-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x202.6.35-28-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0206
  E: ID_SERIAL=Linux_2.6.35-28-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.0
  E: ID_SERIAL_SHORT=0000:00:1d.0
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  E: MAJOR=189
  E: MINOR=128
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/206
  E: TYPE=9/0/0
  E: BUSNUM=002
  E: DEVNUM=001
  E: DEVLINKS=/dev/char/189:128
  
  P: /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
  E: SUBSYSTEM=usb
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/206
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
  
  P: /devices/pci0000:00/0000:00:1d.0/usbmon/usbmon2
  N: usbmon2
  S: char/252:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usbmon/usbmon2
  E: SUBSYSTEM=usbmon
  E: DEVNAME=/dev/usbmon2
  E: MAJOR=252
  E: MINOR=2
  E: DEVLINKS=/dev/char/252:2
  
  P: /devices/pci0000:00/0000:00:1d.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.1
  E: SUBSYSTEM=pci
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:27C9
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:1d.1
  E: MODALIAS=pci:v00008086d000027C9sv00001025sd00000349bc0Csc03i00
  
  P: /devices/pci0000:00/0000:00:1d.1/usb3
  N: bus/usb/003/001
  S: char/189:256
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb3
  E: SUBSYSTEM=usb
  E: DEVNAME=bus/usb/003/001
  E: ID_VENDOR=Linux_2.6.35-28-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x202.6.35-28-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0206
  E: ID_SERIAL=Linux_2.6.35-28-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.1
  E: ID_SERIAL_SHORT=0000:00:1d.1
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  E: MAJOR=189
  E: MINOR=256
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/206
  E: TYPE=9/0/0
  E: BUSNUM=003
  E: DEVNUM=001
  E: DEVLINKS=/dev/char/189:256
  
  P: /devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
  E: SUBSYSTEM=usb
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/206
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
  
  P: /devices/pci0000:00/0000:00:1d.1/usbmon/usbmon3
  N: usbmon3
  S: char/252:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usbmon/usbmon3
  E: SUBSYSTEM=usbmon
  E: DEVNAME=/dev/usbmon3
  E: MAJOR=252
  E: MINOR=3
  E: DEVLINKS=/dev/char/252:3
  
  P: /devices/pci0000:00/0000:00:1d.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.2
  E: SUBSYSTEM=pci
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:27CA
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:1d.2
  E: MODALIAS=pci:v00008086d000027CAsv00001025sd00000349bc0Csc03i00
  
  P: /devices/pci0000:00/0000:00:1d.2/usb4
  N: bus/usb/004/001
  S: char/189:384
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb4
  E: SUBSYSTEM=usb
  E: DEVNAME=bus/usb/004/001
  E: ID_VENDOR=Linux_2.6.35-28-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x202.6.35-28-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0206
  E: ID_SERIAL=Linux_2.6.35-28-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.2
  E: ID_SERIAL_SHORT=0000:00:1d.2
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  E: MAJOR=189
  E: MINOR=384
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/206
  E: TYPE=9/0/0
  E: BUSNUM=004
  E: DEVNUM=001
  E: DEVLINKS=/dev/char/189:384
  
  P: /devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
  E: SUBSYSTEM=usb
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/206
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
  
  P: /devices/pci0000:00/0000:00:1d.2/usbmon/usbmon4
  N: usbmon4
  S: char/252:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.2/usbmon/usbmon4
  E: SUBSYSTEM=usbmon
  E: DEVNAME=/dev/usbmon4
  E: MAJOR=252
  E: MINOR=4
  E: DEVLINKS=/dev/char/252:4
  
  P: /devices/pci0000:00/0000:00:1d.3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3
  E: SUBSYSTEM=pci
  E: DRIVER=uhci_hcd
  E: PCI_CLASS=C0300
  E: PCI_ID=8086:27CB
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:1d.3
  E: MODALIAS=pci:v00008086d000027CBsv00001025sd00000349bc0Csc03i00
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5
  N: bus/usb/005/001
  S: char/189:512
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5
  E: SUBSYSTEM=usb
  E: DEVNAME=bus/usb/005/001
  E: ID_VENDOR=Linux_2.6.35-28-generic_uhci_hcd
  E: ID_VENDOR_ENC=Linux\x202.6.35-28-generic\x20uhci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=UHCI_Host_Controller
  E: ID_MODEL_ENC=UHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0206
  E: ID_SERIAL=Linux_2.6.35-28-generic_uhci_hcd_UHCI_Host_Controller_0000:00:1d.3
  E: ID_SERIAL_SHORT=0000:00:1d.3
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  E: MAJOR=189
  E: MINOR=512
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/206
  E: TYPE=9/0/0
  E: BUSNUM=005
  E: DEVNUM=001
  E: DEVLINKS=/dev/char/189:512
  
  P: /devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
  E: SUBSYSTEM=usb
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/206
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
  
  P: /devices/pci0000:00/0000:00:1d.3/usbmon/usbmon5
  N: usbmon5
  S: char/252:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usbmon/usbmon5
  E: SUBSYSTEM=usbmon
  E: DEVNAME=/dev/usbmon5
  E: MAJOR=252
  E: MINOR=5
  E: DEVLINKS=/dev/char/252:5
  
  P: /devices/pci0000:00/0000:00:1d.7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7
  E: SUBSYSTEM=pci
  E: DRIVER=ehci_hcd
  E: PCI_CLASS=C0320
  E: PCI_ID=8086:27CC
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:1d.7
  E: MODALIAS=pci:v00008086d000027CCsv00001025sd00000349bc0Csc03i20
  
  P: /devices/pci0000:00/0000:00:1d.7/usb1
  N: bus/usb/001/001
  S: char/189:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1
  E: SUBSYSTEM=usb
  E: DEVNAME=bus/usb/001/001
  E: ID_VENDOR=Linux_2.6.35-28-generic_ehci_hcd
  E: ID_VENDOR_ENC=Linux\x202.6.35-28-generic\x20ehci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=EHCI_Host_Controller
  E: ID_MODEL_ENC=EHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0206
  E: ID_SERIAL=Linux_2.6.35-28-generic_ehci_hcd_EHCI_Host_Controller_0000:00:1d.7
  E: ID_SERIAL_SHORT=0000:00:1d.7
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  E: MAJOR=189
  E: MINOR=0
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/2/206
  E: TYPE=9/0/0
  E: BUSNUM=001
  E: DEVNUM=001
  E: DEVLINKS=/dev/char/189:0
  
  P: /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
  E: SUBSYSTEM=usb
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/2/206
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00
  
  P: /devices/pci0000:00/0000:00:1d.7/usb1/1-4
  N: bus/usb/001/002
  S: char/189:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-4
  E: SUBSYSTEM=usb
  E: DEVNAME=bus/usb/001/002
  E: ID_VENDOR=Suyin
  E: ID_VENDOR_ENC=Suyin
  E: ID_VENDOR_ID=064e
  E: ID_MODEL=1.3M_WebCam
  E: ID_MODEL_ENC=1.3M\x20WebCam
  E: ID_MODEL_ID=a219
  E: ID_REVISION=0215
  E: ID_SERIAL=Suyin_1.3M_WebCam_HF1315-S32B-OV01-VA-R02.01.05
  E: ID_SERIAL_SHORT=HF1315-S32B-OV01-VA-R02.01.05
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:0e0100:0e0200:
  E: MAJOR=189
  E: MINOR=1
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=64e/a219/215
  E: TYPE=239/2/1
  E: BUSNUM=001
  E: DEVNUM=002
  E: DEVLINKS=/dev/char/189:1
  
  P: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0
  E: SUBSYSTEM=usb
  E: DEVTYPE=usb_interface
  E: DRIVER=uvcvideo
  E: PRODUCT=64e/a219/215
  E: TYPE=239/2/1
  E: INTERFACE=14/1/0
  E: MODALIAS=usb:v064EpA219d0215dcEFdsc02dp01ic0Eisc01ip00
  
  P: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5
  E: SUBSYSTEM=input
  E: PRODUCT=3/64e/a219/215
  E: NAME="1.3M WebCam"
  E: PHYS="usb-0000:00:1d.7-4/button"
  E: EV==3
  E: KEY==100000 0 0 0 0 0 0
  E: MODALIAS=input:b0003v064EpA219e0215-e0,1,kD4,ramlsfw
  
  P: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5/event5
  N: input/event5
  S: char/13:69
  S: input/by-id/usb-Suyin_1.3M_WebCam_HF1315-S32B-OV01-VA-R02.01.05-event-if00
  S: input/by-path/pci-0000:00:1d.7-usb-0:4:1.0-event
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5/event5
  E: SUBSYSTEM=input
  E: DEVNAME=input/event5
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_VENDOR=Suyin
  E: ID_VENDOR_ENC=Suyin
  E: ID_VENDOR_ID=064e
  E: ID_MODEL=1.3M_WebCam
  E: ID_MODEL_ENC=1.3M\x20WebCam
  E: ID_MODEL_ID=a219
  E: ID_REVISION=0215
  E: ID_SERIAL=Suyin_1.3M_WebCam_HF1315-S32B-OV01-VA-R02.01.05
  E: ID_SERIAL_SHORT=HF1315-S32B-OV01-VA-R02.01.05
  E: ID_TYPE=video
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:0e0100:0e0200:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=uvcvideo
  E: ID_PATH=pci-0000:00:1d.7-usb-0:4:1.0
  E: XKBMODEL=pc105
  E: XKBLAYOUT=latam
  E: MAJOR=13
  E: MINOR=69
  E: DEVLINKS=/dev/char/13:69 /dev/input/by-id/usb-Suyin_1.3M_WebCam_HF1315-S32B-OV01-VA-R02.01.05-event-if00 /dev/input/by-path/pci-0000:00:1d.7-usb-0:4:1.0-event
  
  P: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/video4linux/video0
  N: video0
  S: char/81:0
  S: v4l/by-id/usb-Suyin_1.3M_WebCam_HF1315-S32B-OV01-VA-R02.01.05-video-index0
  S: v4l/by-path/pci-0000:00:1d.7-usb-0:4:1.0-video-index0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/video4linux/video0
  E: SUBSYSTEM=video4linux
  E: DEVNAME=video0
  E: ID_V4L_VERSION=2
  E: ID_V4L_PRODUCT=1.3M WebCam
  E: ID_V4L_CAPABILITIES=:capture:
  E: ID_VENDOR=Suyin
  E: ID_VENDOR_ENC=Suyin
  E: ID_VENDOR_ID=064e
  E: ID_MODEL=1.3M_WebCam
  E: ID_MODEL_ENC=1.3M\x20WebCam
  E: ID_MODEL_ID=a219
  E: ID_REVISION=0215
  E: ID_SERIAL=Suyin_1.3M_WebCam_HF1315-S32B-OV01-VA-R02.01.05
  E: ID_SERIAL_SHORT=HF1315-S32B-OV01-VA-R02.01.05
  E: ID_TYPE=video
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:0e0100:0e0200:
  E: ID_USB_INTERFACE_NUM=00
  E: ID_USB_DRIVER=uvcvideo
  E: ID_PATH=pci-0000:00:1d.7-usb-0:4:1.0
  E: MAJOR=81
  E: MINOR=0
  E: DEVLINKS=/dev/char/81:0 /dev/v4l/by-id/usb-Suyin_1.3M_WebCam_HF1315-S32B-OV01-VA-R02.01.05-video-index0 /dev/v4l/by-path/pci-0000:00:1d.7-usb-0:4:1.0-video-index0
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.1
  E: SUBSYSTEM=usb
  E: DEVTYPE=usb_interface
  E: DRIVER=uvcvideo
  E: PRODUCT=64e/a219/215
  E: TYPE=239/2/1
  E: INTERFACE=14/2/0
  E: MODALIAS=usb:v064EpA219d0215dcEFdsc02dp01ic0Eisc02ip00
  
  P: /devices/pci0000:00/0000:00:1d.7/usb1/1-5
  N: bus/usb/001/003
  S: char/189:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-5
  E: SUBSYSTEM=usb
  E: DEVNAME=bus/usb/001/003
  E: ID_VENDOR=ENE_Flash
  E: ID_VENDOR_ENC=ENE\x20Flash\x20\x20
  E: ID_VENDOR_ID=0cf2
  E: ID_MODEL=UB6250
  E: ID_MODEL_ENC=UB6250\x20\x20\x20\x20\x20\x20\x20
  E: ID_MODEL_ID=6250
  E: ID_REVISION=0100
  E: ID_SERIAL=ENE_Flash_UB6250_606569746801
  E: ID_SERIAL_SHORT=606569746801
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:ff0650:
  E: MAJOR=189
  E: MINOR=2
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=cf2/6250/100
  E: TYPE=0/0/0
  E: BUSNUM=001
  E: DEVNUM=003
  E: DEVLINKS=/dev/char/189:2
  
  P: /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0
  E: SUBSYSTEM=usb
  E: DEVTYPE=usb_interface
  E: PRODUCT=cf2/6250/100
  E: TYPE=0/0/0
  E: INTERFACE=255/6/80
  E: MODALIAS=usb:v0CF2p6250d0100dc00dsc00dp00icFFisc06ip50
  
  P: /devices/pci0000:00/0000:00:1d.7/usbmon/usbmon1
  N: usbmon1
  S: char/252:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usbmon/usbmon1
  E: SUBSYSTEM=usbmon
  E: DEVNAME=/dev/usbmon1
  E: MAJOR=252
  E: MINOR=1
  E: DEVLINKS=/dev/char/252:1
  
  P: /devices/pci0000:00/0000:00:1e.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0
  E: SUBSYSTEM=pci
  E: PCI_CLASS=60401
  E: PCI_ID=8086:2448
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:1e.0
  E: MODALIAS=pci:v00008086d00002448sv00001025sd00000349bc06sc04i01
  
  P: /devices/pci0000:00/0000:00:1e.0/pci_bus/0000:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1e.0/pci_bus/0000:05
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:1f.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.0
  E: SUBSYSTEM=pci
  E: PCI_CLASS=60100
  E: PCI_ID=8086:27BC
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:1f.0
  E: MODALIAS=pci:v00008086d000027BCsv00001025sd00000349bc06sc01i00
  
  P: /devices/pci0000:00/0000:00:1f.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2
  E: SUBSYSTEM=pci
  E: ID_VENDOR_FROM_DATABASE=Intel Corporation
  E: ID_MODEL_FROM_DATABASE=N10/ICH7 Family SATA AHCI Controller
  E: DRIVER=ahci
  E: PCI_CLASS=10601
  E: PCI_ID=8086:27C1
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:1f.2
  E: MODALIAS=pci:v00008086d000027C1sv00001025sd00000349bc01sc06i01
  
  P: /devices/pci0000:00/0000:00:1f.2/host0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0
  E: SUBSYSTEM=scsi
  E: DEVTYPE=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
  E: SUBSYSTEM=scsi
  E: DEVTYPE=scsi_target
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  E: SUBSYSTEM=scsi
  E: DEVTYPE=scsi_device
  E: DRIVER=sd
  E: MODALIAS=scsi:t-0x00
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  N: sda
  S: block/8:0
  S: disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB
  S: disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
  S: disk/by-id/wwn-0x50000392f9181995
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  E: SUBSYSTEM=block
  E: DEVNAME=sda
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=TOSHIBA_MK2565GSX
  E: ID_MODEL_ENC=TOSHIBA\x20MK2565GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=GJ002J
  E: ID_SERIAL=TOSHIBA_MK2565GSX_Z0A1B2BCB
  E: ID_SERIAL_SHORT=Z0A1B2BCB
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=94
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=94
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=128
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=5400
  E: ID_WWN=0x50000392f9181995
  E: ID_WWN_WITH_EXTENSION=0x50000392f9181995
  E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK2565G_Z0A1B2BCB
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION_TABLE=1
  E: UDISKS_PARTITION_TABLE_SCHEME=mbr
  E: UDISKS_PARTITION_TABLE_COUNT=4
  E: UDISKS_ATA_SMART_IS_AVAILABLE=1
  E: MAJOR=8
  E: MINOR=0
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/8:0 /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0 /dev/disk/by-id/wwn-0x50000392f9181995
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1
  N: sda1
  S: block/8:1
  S: disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part1
  S: disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part1
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1
  S: disk/by-uuid/58682f5c-0155-4154-adff-b3bdd58cc626
  S: disk/by-id/wwn-0x50000392f9181995-part1
  S: root
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1
  E: SUBSYSTEM=block
  E: DEVNAME=sda1
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=TOSHIBA_MK2565GSX
  E: ID_MODEL_ENC=TOSHIBA\x20MK2565GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=GJ002J
  E: ID_SERIAL=TOSHIBA_MK2565GSX_Z0A1B2BCB
  E: ID_SERIAL_SHORT=Z0A1B2BCB
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=94
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=94
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=128
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=5400
  E: ID_WWN=0x50000392f9181995
  E: ID_WWN_WITH_EXTENSION=0x50000392f9181995
  E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK2565G_Z0A1B2BCB
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_UUID=58682f5c-0155-4154-adff-b3bdd58cc626
  E: ID_FS_UUID_ENC=58682f5c-0155-4154-adff-b3bdd58cc626
  E: ID_FS_VERSION=1.0
  E: ID_FS_TYPE=ext3
  E: ID_FS_USAGE=filesystem
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=1
  E: UDISKS_PARTITION_TYPE=0x83
  E: UDISKS_PARTITION_SIZE=14063501312
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=1048576
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: MAJOR=8
  E: MINOR=1
  E: DEVTYPE=partition
  E: DEVLINKS=/dev/block/8:1 /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part1 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part1 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1 /dev/disk/by-uuid/58682f5c-0155-4154-adff-b3bdd58cc626 /dev/disk/by-id/wwn-0x50000392f9181995-part1 /dev/root
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2
  N: sda2
  S: block/8:2
  S: disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part2
  S: disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part2
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2
  S: disk/by-uuid/d7a9a922-eb3e-4c30-88d4-d026e9cb1c67
  S: disk/by-id/wwn-0x50000392f9181995-part2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2
  E: SUBSYSTEM=block
  E: DEVNAME=sda2
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=TOSHIBA_MK2565GSX
  E: ID_MODEL_ENC=TOSHIBA\x20MK2565GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=GJ002J
  E: ID_SERIAL=TOSHIBA_MK2565GSX_Z0A1B2BCB
  E: ID_SERIAL_SHORT=Z0A1B2BCB
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=94
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=94
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=128
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=5400
  E: ID_WWN=0x50000392f9181995
  E: ID_WWN_WITH_EXTENSION=0x50000392f9181995
  E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK2565G_Z0A1B2BCB
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_UUID=d7a9a922-eb3e-4c30-88d4-d026e9cb1c67
  E: ID_FS_UUID_ENC=d7a9a922-eb3e-4c30-88d4-d026e9cb1c67
  E: ID_FS_VERSION=2
  E: ID_FS_TYPE=swap
  E: ID_FS_USAGE=other
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=2
  E: UDISKS_PARTITION_TYPE=0x82
  E: UDISKS_PARTITION_SIZE=1353711616
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=248705449984
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: MAJOR=8
  E: MINOR=2
  E: DEVTYPE=partition
  E: DEVLINKS=/dev/block/8:2 /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part2 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part2 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2 /dev/disk/by-uuid/d7a9a922-eb3e-4c30-88d4-d026e9cb1c67 /dev/disk/by-id/wwn-0x50000392f9181995-part2
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda3
  N: sda3
  S: block/8:3
  S: disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part3
  S: disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part3
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part3
  S: disk/by-uuid/0A728F44728F340B
  S: disk/by-label/Acer
  S: disk/by-id/wwn-0x50000392f9181995-part3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda3
  E: SUBSYSTEM=block
  E: DEVNAME=sda3
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=TOSHIBA_MK2565GSX
  E: ID_MODEL_ENC=TOSHIBA\x20MK2565GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=GJ002J
  E: ID_SERIAL=TOSHIBA_MK2565GSX_Z0A1B2BCB
  E: ID_SERIAL_SHORT=Z0A1B2BCB
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=94
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=94
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=128
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=5400
  E: ID_WWN=0x50000392f9181995
  E: ID_WWN_WITH_EXTENSION=0x50000392f9181995
  E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK2565G_Z0A1B2BCB
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_LABEL=Acer
  E: ID_FS_LABEL_ENC=Acer
  E: ID_FS_UUID=0A728F44728F340B
  E: ID_FS_UUID_ENC=0A728F44728F340B
  E: ID_FS_TYPE=ntfs
  E: ID_FS_USAGE=filesystem
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=3
  E: UDISKS_PARTITION_TYPE=0x07
  E: UDISKS_PARTITION_SIZE=112640000000
  E: UDISKS_PARTITION_FLAGS=boot
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=14064549888
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: MAJOR=8
  E: MINOR=3
  E: DEVTYPE=partition
  E: DEVLINKS=/dev/block/8:3 /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part3 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part3 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part3 /dev/disk/by-uuid/0A728F44728F340B /dev/disk/by-label/Acer /dev/disk/by-id/wwn-0x50000392f9181995-part3
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda4
  N: sda4
  S: block/8:4
  S: disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part4
  S: disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part4
  S: disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part4
  S: disk/by-uuid/b6a0eae2-ce1c-4ce0-9831-085826248369
  S: disk/by-id/wwn-0x50000392f9181995-part4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda4
  E: SUBSYSTEM=block
  E: DEVNAME=sda4
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=TOSHIBA_MK2565GSX
  E: ID_MODEL_ENC=TOSHIBA\x20MK2565GSX\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=GJ002J
  E: ID_SERIAL=TOSHIBA_MK2565GSX_Z0A1B2BCB
  E: ID_SERIAL_SHORT=Z0A1B2BCB
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_HPA=1
  E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=94
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=94
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=128
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_ATA_ROTATION_RATE_RPM=5400
  E: ID_WWN=0x50000392f9181995
  E: ID_WWN_WITH_EXTENSION=0x50000392f9181995
  E: ID_SCSI_COMPAT=SATA_TOSHIBA_MK2565G_Z0A1B2BCB
  E: ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_UUID=b6a0eae2-ce1c-4ce0-9831-085826248369
  E: ID_FS_UUID_ENC=b6a0eae2-ce1c-4ce0-9831-085826248369
  E: ID_FS_SEC_TYPE=ext2
  E: ID_FS_VERSION=1.0
  E: ID_FS_TYPE=ext3
  E: ID_FS_USAGE=filesystem
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=4
  E: UDISKS_PARTITION_TYPE=0x83
  E: UDISKS_PARTITION_SIZE=121999720448
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=126704680960
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: MAJOR=8
  E: MINOR=4
  E: DEVTYPE=partition
  E: DEVLINKS=/dev/block/8:4 /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part4 /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part4 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part4 /dev/disk/by-uuid/b6a0eae2-ce1c-4ce0-9831-085826248369 /dev/disk/by-id/wwn-0x50000392f9181995-part4
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
  N: bsg/0:0:0:0
  S: char/253:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
  E: SUBSYSTEM=bsg
  E: DEVNAME=/dev/bsg/0:0:0:0
  E: MAJOR=253
  E: MINOR=0
  E: DEVLINKS=/dev/char/253:0
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_disk/0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_disk/0:0:0:0
  E: SUBSYSTEM=scsi_disk
  
  P: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
  N: sg0
  S: char/21:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
  E: SUBSYSTEM=scsi_generic
  E: DEVNAME=/dev/sg0
  E: MAJOR=21
  E: MINOR=0
  E: DEVLINKS=/dev/char/21:0
  
  P: /devices/pci0000:00/0000:00:1f.2/host1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1
  E: SUBSYSTEM=scsi
  E: DEVTYPE=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2
  E: SUBSYSTEM=scsi
  E: DEVTYPE=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host3
  E: SUBSYSTEM=scsi
  E: DEVTYPE=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:1f.3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:1f.3
  E: SUBSYSTEM=pci
  E: PCI_CLASS=C0500
  E: PCI_ID=8086:27DA
  E: PCI_SUBSYS_ID=1025:0349
  E: PCI_SLOT_NAME=0000:00:1f.3
  E: MODALIAS=pci:v00008086d000027DAsv00001025sd00000349bc0Csc05i00
  
  P: /devices/pci0000:00/pci_bus/0000:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/pci_bus/0000:00
  E: SUBSYSTEM=pci_bus
  
  P: /devices/platform/Fixed MDIO bus.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/Fixed MDIO bus.0
  E: SUBSYSTEM=platform
  E: MODALIAS=platform:Fixed MDIO bus
  
  P: /devices/platform/Fixed MDIO bus.0/mdio_bus/0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/Fixed MDIO bus.0/mdio_bus/0
  E: SUBSYSTEM=mdio_bus
  
  P: /devices/platform/eisa.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/eisa.0
  E: SUBSYSTEM=platform
  E: MODALIAS=platform:eisa
  
  P: /devices/platform/i8042
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042
  E: SUBSYSTEM=platform
  E: DRIVER=i8042
  E: MODALIAS=platform:i8042
  
  P: /devices/platform/i8042/serio0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio0
  E: SUBSYSTEM=serio
  E: DMI_VENDOR=Acer
  E: DRIVER=atkbd
  E: SERIO_TYPE=06
  E: SERIO_PROTO=00
  E: SERIO_ID=00
  E: SERIO_EXTRA=00
  E: MODALIAS=serio:ty06pr00id00ex00
  
  P: /devices/platform/i8042/serio0/input/input4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio0/input/input4
  E: SUBSYSTEM=input
  E: PRODUCT=11/1/1/ab41
  E: NAME="AT Translated Set 2 keyboard"
  E: PHYS="isa0060/serio0/input0"
  E: EV==120013
  E: KEY==10000 c0200 0 0 0 0 0 700f 2000003 3803078 f830f401 febfffdf ffefffff ffffffff fffffffe
  E: MSC==10
  E: LED==7
  E: MODALIAS=input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8D,8E,8F,94,95,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D9,E0,E1,E2,E3,EC,ED,EE,1A9,1B2,1B3,1D0,ram4,l0,1,2,sfw
  
  P: /devices/platform/i8042/serio0/input/input4/event4
  N: input/event4
  S: char/13:68
  S: input/by-path/platform-i8042-serio-0-event-kbd
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio0/input/input4/event4
  E: SUBSYSTEM=input
  E: DEVNAME=input/event4
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-0
  E: XKBMODEL=pc105
  E: XKBLAYOUT=latam
  E: MAJOR=13
  E: MINOR=68
  E: DEVLINKS=/dev/char/13:68 /dev/input/by-path/platform-i8042-serio-0-event-kbd
  E: DMI_VENDOR=Acer
  
  P: /devices/platform/i8042/serio1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1
  E: SUBSYSTEM=serio
  E: DRIVER=psmouse
  E: SERIO_TYPE=01
  E: SERIO_PROTO=00
  E: SERIO_ID=00
  E: SERIO_EXTRA=00
  E: MODALIAS=serio:ty01pr00id00ex00
  
  P: /devices/platform/i8042/serio1/input/input6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1/input/input6
  E: SUBSYSTEM=input
  E: PRODUCT=11/2/7/1b1
  E: NAME="SynPS/2 Synaptics TouchPad"
  E: PHYS="isa0060/serio1/input0"
  E: EV==b
  E: KEY==420 0 30000 0 0 0 0 0 0 0 0
  E: ABS==11000003
  E: MODALIAS=input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw
  
  P: /devices/platform/i8042/serio1/input/input6/event6
  N: input/event6
  S: char/13:70
  S: input/by-path/platform-i8042-serio-1-event-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1/input/input6/event6
  E: SUBSYSTEM=input
  E: DEVNAME=input/event6
  E: ID_INPUT=1
  E: ID_INPUT_TOUCHPAD=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-1
  E: DMI_VENDOR=Acer
  E: MAJOR=13
  E: MINOR=70
  E: DEVLINKS=/dev/char/13:70 /dev/input/by-path/platform-i8042-serio-1-event-mouse
  
  P: /devices/platform/i8042/serio1/input/input6/mouse0
  N: input/mouse0
  S: char/13:32
  S: input/by-path/platform-i8042-serio-1-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1/input/input6/mouse0
  E: SUBSYSTEM=input
  E: DEVNAME=input/mouse0
  E: ID_INPUT=1
  E: ID_INPUT_TOUCHPAD=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-1
  E: MAJOR=13
  E: MINOR=32
  E: DEVLINKS=/dev/char/13:32 /dev/input/by-path/platform-i8042-serio-1-mouse
  
  P: /devices/platform/pcspkr
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/pcspkr
  E: SUBSYSTEM=platform
  E: MODALIAS=platform:pcspkr
  
  P: /devices/platform/serial8250
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250
  E: SUBSYSTEM=platform
  E: DRIVER=serial8250
  E: MODALIAS=platform:serial8250
  
  P: /devices/platform/serial8250/tty/ttyS0
  N: ttyS0
  S: char/4:64
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS0
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/ttyS0
  E: MAJOR=4
  E: MINOR=64
  E: DEVLINKS=/dev/char/4:64
  
  P: /devices/platform/serial8250/tty/ttyS1
  N: ttyS1
  S: char/4:65
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS1
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/ttyS1
  E: MAJOR=4
  E: MINOR=65
  E: DEVLINKS=/dev/char/4:65
  
  P: /devices/platform/serial8250/tty/ttyS2
  N: ttyS2
  S: char/4:66
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS2
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/ttyS2
  E: MAJOR=4
  E: MINOR=66
  E: DEVLINKS=/dev/char/4:66
  
  P: /devices/platform/serial8250/tty/ttyS3
  N: ttyS3
  S: char/4:67
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS3
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/ttyS3
  E: MAJOR=4
  E: MINOR=67
  E: DEVLINKS=/dev/char/4:67
  
  P: /devices/platform/vboxdrv.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/vboxdrv.0
  E: SUBSYSTEM=platform
  E: DRIVER=vboxdrv
  E: MODALIAS=platform:vboxdrv
  
  P: /devices/pnp0/00:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:00
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:01
  E: SUBSYSTEM=pnp
  E: DRIVER=system
  
  P: /devices/pnp0/00:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:02
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:03
  E: SUBSYSTEM=pnp
  E: DRIVER=rtc_cmos
  
  P: /devices/pnp0/00:03/rtc/rtc0
  N: rtc0
  S: char/254:0
  S: rtc
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:03/rtc/rtc0
  E: SUBSYSTEM=rtc
  E: DEVNAME=/dev/rtc0
  E: MAJOR=254
  E: MINOR=0
  E: DEVLINKS=/dev/char/254:0 /dev/rtc
  
  P: /devices/pnp0/00:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:04
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:05
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:06
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:07
  E: SUBSYSTEM=pnp
  E: DRIVER=i8042 kbd
  
  P: /devices/pnp0/00:08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:08
  E: SUBSYSTEM=pnp
  E: DRIVER=i8042 aux
  
  P: /devices/virtual/backlight/acpi_video0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/backlight/acpi_video0
  E: SUBSYSTEM=backlight
  
  P: /devices/virtual/bdi/0:20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/0:20
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:10
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:11
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:12
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:13
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:14
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:15
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:2
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:3
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:4
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:5
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:6
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:7
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:8
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:9
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:2
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:3
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:4
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:5
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:6
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:7
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/8:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/8:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/default
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/default
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/block/loop0
  N: loop0
  S: block/7:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop0
  E: SUBSYSTEM=block
  E: DEVNAME=loop0
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: MAJOR=7
  E: MINOR=0
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/7:0
  
  P: /devices/virtual/block/loop1
  N: loop1
  S: block/7:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop1
  E: SUBSYSTEM=block
  E: DEVNAME=loop1
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: MAJOR=7
  E: MINOR=1
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/7:1
  
  P: /devices/virtual/block/loop2
  N: loop2
  S: block/7:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop2
  E: SUBSYSTEM=block
  E: DEVNAME=loop2
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: MAJOR=7
  E: MINOR=2
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/7:2
  
  P: /devices/virtual/block/loop3
  N: loop3
  S: block/7:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop3
  E: SUBSYSTEM=block
  E: DEVNAME=loop3
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: MAJOR=7
  E: MINOR=3
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/7:3
  
  P: /devices/virtual/block/loop4
  N: loop4
  S: block/7:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop4
  E: SUBSYSTEM=block
  E: DEVNAME=loop4
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: MAJOR=7
  E: MINOR=4
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/7:4
  
  P: /devices/virtual/block/loop5
  N: loop5
  S: block/7:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop5
  E: SUBSYSTEM=block
  E: DEVNAME=loop5
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: MAJOR=7
  E: MINOR=5
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/7:5
  
  P: /devices/virtual/block/loop6
  N: loop6
  S: block/7:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop6
  E: SUBSYSTEM=block
  E: DEVNAME=loop6
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: MAJOR=7
  E: MINOR=6
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/7:6
  
  P: /devices/virtual/block/loop7
  N: loop7
  S: block/7:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop7
  E: SUBSYSTEM=block
  E: DEVNAME=loop7
  E: UDISKS_PRESENTATION_NOPOLICY=1
  E: MAJOR=7
  E: MINOR=7
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/7:7
  
  P: /devices/virtual/block/ram0
  N: ram0
  S: block/1:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram0
  E: SUBSYSTEM=block
  E: DEVNAME=ram0
  E: MAJOR=1
  E: MINOR=0
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:0
  
  P: /devices/virtual/block/ram1
  N: ram1
  S: block/1:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram1
  E: SUBSYSTEM=block
  E: DEVNAME=ram1
  E: MAJOR=1
  E: MINOR=1
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:1
  
  P: /devices/virtual/block/ram10
  N: ram10
  S: block/1:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram10
  E: SUBSYSTEM=block
  E: DEVNAME=ram10
  E: MAJOR=1
  E: MINOR=10
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:10
  
  P: /devices/virtual/block/ram11
  N: ram11
  S: block/1:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram11
  E: SUBSYSTEM=block
  E: DEVNAME=ram11
  E: MAJOR=1
  E: MINOR=11
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:11
  
  P: /devices/virtual/block/ram12
  N: ram12
  S: block/1:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram12
  E: SUBSYSTEM=block
  E: DEVNAME=ram12
  E: MAJOR=1
  E: MINOR=12
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:12
  
  P: /devices/virtual/block/ram13
  N: ram13
  S: block/1:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram13
  E: SUBSYSTEM=block
  E: DEVNAME=ram13
  E: MAJOR=1
  E: MINOR=13
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:13
  
  P: /devices/virtual/block/ram14
  N: ram14
  S: block/1:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram14
  E: SUBSYSTEM=block
  E: DEVNAME=ram14
  E: MAJOR=1
  E: MINOR=14
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:14
  
  P: /devices/virtual/block/ram15
  N: ram15
  S: block/1:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram15
  E: SUBSYSTEM=block
  E: DEVNAME=ram15
  E: MAJOR=1
  E: MINOR=15
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:15
  
  P: /devices/virtual/block/ram2
  N: ram2
  S: block/1:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram2
  E: SUBSYSTEM=block
  E: DEVNAME=ram2
  E: MAJOR=1
  E: MINOR=2
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:2
  
  P: /devices/virtual/block/ram3
  N: ram3
  S: block/1:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram3
  E: SUBSYSTEM=block
  E: DEVNAME=ram3
  E: MAJOR=1
  E: MINOR=3
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:3
  
  P: /devices/virtual/block/ram4
  N: ram4
  S: block/1:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram4
  E: SUBSYSTEM=block
  E: DEVNAME=ram4
  E: MAJOR=1
  E: MINOR=4
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:4
  
  P: /devices/virtual/block/ram5
  N: ram5
  S: block/1:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram5
  E: SUBSYSTEM=block
  E: DEVNAME=ram5
  E: MAJOR=1
  E: MINOR=5
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:5
  
  P: /devices/virtual/block/ram6
  N: ram6
  S: block/1:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram6
  E: SUBSYSTEM=block
  E: DEVNAME=ram6
  E: MAJOR=1
  E: MINOR=6
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:6
  
  P: /devices/virtual/block/ram7
  N: ram7
  S: block/1:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram7
  E: SUBSYSTEM=block
  E: DEVNAME=ram7
  E: MAJOR=1
  E: MINOR=7
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:7
  
  P: /devices/virtual/block/ram8
  N: ram8
  S: block/1:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram8
  E: SUBSYSTEM=block
  E: DEVNAME=ram8
  E: MAJOR=1
  E: MINOR=8
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:8
  
  P: /devices/virtual/block/ram9
  N: ram9
  S: block/1:9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram9
  E: SUBSYSTEM=block
  E: DEVNAME=ram9
  E: MAJOR=1
  E: MINOR=9
  E: DEVTYPE=disk
  E: DEVLINKS=/dev/block/1:9
  
  P: /devices/virtual/dmi/id
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/dmi/id
  E: SUBSYSTEM=dmi
  E: MODALIAS=dmi:bvnAcer:bvrV3.13(DDR3):bd12/23/2010:svnAcer:pnAOD255E:pvrV3.13(DDR3):rvnAcer:rnJE02_PT:rvrV3.13(DDR3):cvnAcer:ct10:cvrV3.13(DDR3):
  
  P: /devices/virtual/graphics/fbcon
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/graphics/fbcon
  E: SUBSYSTEM=graphics
  
  P: /devices/virtual/hwmon/hwmon0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/hwmon/hwmon0
  E: SUBSYSTEM=hwmon
  
  P: /devices/virtual/input/mice
  N: input/mice
  S: char/13:63
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/input/mice
  E: SUBSYSTEM=input
  E: DEVNAME=/dev/input/mice
  E: MAJOR=13
  E: MINOR=63
  E: DEVLINKS=/dev/char/13:63
  
  P: /devices/virtual/mem/full
  N: full
  S: char/1:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/full
  E: SUBSYSTEM=mem
  E: DEVNAME=/dev/full
  E: MAJOR=1
  E: MINOR=7
  E: DEVMODE=0666
  E: DEVLINKS=/dev/char/1:7
  
  P: /devices/virtual/mem/kmsg
  N: kmsg
  S: char/1:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/kmsg
  E: SUBSYSTEM=mem
  E: DEVNAME=/dev/kmsg
  E: MAJOR=1
  E: MINOR=11
  E: DEVLINKS=/dev/char/1:11
  
  P: /devices/virtual/mem/mem
  N: mem
  S: char/1:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/mem
  E: SUBSYSTEM=mem
  E: DEVNAME=/dev/mem
  E: MAJOR=1
  E: MINOR=1
  E: DEVLINKS=/dev/char/1:1
  
  P: /devices/virtual/mem/null
  N: null
  S: char/1:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/null
  E: SUBSYSTEM=mem
  E: DEVNAME=/dev/null
  E: MAJOR=1
  E: MINOR=3
  E: DEVMODE=0666
  E: DEVLINKS=/dev/char/1:3
  
  P: /devices/virtual/mem/oldmem
  N: oldmem
  S: char/1:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/oldmem
  E: SUBSYSTEM=mem
  E: DEVNAME=/dev/oldmem
  E: MAJOR=1
  E: MINOR=12
  E: DEVLINKS=/dev/char/1:12
  
  P: /devices/virtual/mem/port
  N: port
  S: char/1:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/port
  E: SUBSYSTEM=mem
  E: DEVNAME=/dev/port
  E: MAJOR=1
  E: MINOR=4
  E: DEVLINKS=/dev/char/1:4
  
  P: /devices/virtual/mem/random
  N: random
  S: char/1:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/random
  E: SUBSYSTEM=mem
  E: DEVNAME=/dev/random
  E: MAJOR=1
  E: MINOR=8
  E: DEVMODE=0666
  E: DEVLINKS=/dev/char/1:8
  
  P: /devices/virtual/mem/urandom
  N: urandom
  S: char/1:9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/urandom
  E: SUBSYSTEM=mem
  E: DEVNAME=/dev/urandom
  E: MAJOR=1
  E: MINOR=9
  E: DEVMODE=0666
  E: DEVLINKS=/dev/char/1:9
  
  P: /devices/virtual/mem/zero
  N: zero
  S: char/1:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/zero
  E: SUBSYSTEM=mem
  E: DEVNAME=/dev/zero
  E: MAJOR=1
  E: MINOR=5
  E: DEVMODE=0666
  E: DEVLINKS=/dev/char/1:5
  
  P: /devices/virtual/misc/agpgart
  N: agpgart
  S: char/10:175
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/agpgart
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/agpgart
  E: MAJOR=10
  E: MINOR=175
  E: DEVLINKS=/dev/char/10:175
  
  P: /devices/virtual/misc/cpu_dma_latency
  N: cpu_dma_latency
  S: char/10:58
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/cpu_dma_latency
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/cpu_dma_latency
  E: MAJOR=10
  E: MINOR=58
  E: DEVLINKS=/dev/char/10:58
  
  P: /devices/virtual/misc/device-mapper
  N: mapper/control
  S: char/10:59
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/device-mapper
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/mapper/control
  E: MAJOR=10
  E: MINOR=59
  E: DEVLINKS=/dev/char/10:59
  
  P: /devices/virtual/misc/ecryptfs
  N: ecryptfs
  S: char/10:61
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/ecryptfs
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/ecryptfs
  E: MAJOR=10
  E: MINOR=61
  E: DEVLINKS=/dev/char/10:61
  
  P: /devices/virtual/misc/fuse
  N: fuse
  S: char/10:229
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/fuse
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/fuse
  E: MAJOR=10
  E: MINOR=229
  E: DEVLINKS=/dev/char/10:229
  
  P: /devices/virtual/misc/hpet
  N: hpet
  S: char/10:228
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/hpet
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/hpet
  E: MAJOR=10
  E: MINOR=228
  E: DEVLINKS=/dev/char/10:228
  
  P: /devices/virtual/misc/mcelog
  N: mcelog
  S: char/10:227
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/mcelog
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/mcelog
  E: MAJOR=10
  E: MINOR=227
  E: DEVLINKS=/dev/char/10:227
  
  P: /devices/virtual/misc/network_latency
  N: network_latency
  S: char/10:57
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/network_latency
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/network_latency
  E: MAJOR=10
  E: MINOR=57
  E: DEVLINKS=/dev/char/10:57
  
  P: /devices/virtual/misc/network_throughput
  N: network_throughput
  S: char/10:56
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/network_throughput
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/network_throughput
  E: MAJOR=10
  E: MINOR=56
  E: DEVLINKS=/dev/char/10:56
  
  P: /devices/virtual/misc/pktcdvd
  N: pktcdvd/control
  S: char/10:60
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/pktcdvd
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/pktcdvd/control
  E: MAJOR=10
  E: MINOR=60
  E: DEVLINKS=/dev/char/10:60
  
  P: /devices/virtual/misc/psaux
  N: psaux
  S: char/10:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/psaux
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/psaux
  E: MAJOR=10
  E: MINOR=1
  E: DEVLINKS=/dev/char/10:1
  
  P: /devices/virtual/misc/rfkill
  N: rfkill
  S: char/10:62
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/rfkill
  E: SUBSYSTEM=misc
  E: DEVNAME=rfkill
  E: MAJOR=10
  E: MINOR=62
  E: DEVLINKS=/dev/char/10:62
  E: TAGS=:udev-acl:
  
  P: /devices/virtual/misc/snapshot
  N: snapshot
  S: char/10:231
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/snapshot
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/snapshot
  E: MAJOR=10
  E: MINOR=231
  E: DEVLINKS=/dev/char/10:231
  
  P: /devices/virtual/misc/tun
  N: net/tun
  S: char/10:200
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/tun
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/net/tun
  E: MAJOR=10
  E: MINOR=200
  E: DEVLINKS=/dev/char/10:200
  
  P: /devices/virtual/misc/uinput
  N: uinput
  S: char/10:223
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/uinput
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/uinput
  E: MAJOR=10
  E: MINOR=223
  E: DEVLINKS=/dev/char/10:223
  
  P: /devices/virtual/misc/vboxdrv
  N: vboxdrv
  S: char/10:55
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/vboxdrv
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/vboxdrv
  E: MAJOR=10
  E: MINOR=55
  E: DEVLINKS=/dev/char/10:55
  
  P: /devices/virtual/misc/vboxnetctl
  N: vboxnetctl
  S: char/10:54
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/vboxnetctl
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/vboxnetctl
  E: MAJOR=10
  E: MINOR=54
  E: DEVLINKS=/dev/char/10:54
  
  P: /devices/virtual/misc/vga_arbiter
  N: vga_arbiter
  S: char/10:63
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/vga_arbiter
  E: SUBSYSTEM=misc
  E: DEVNAME=/dev/vga_arbiter
  E: MAJOR=10
  E: MINOR=63
  E: DEVLINKS=/dev/char/10:63
  
  P: /devices/virtual/net/lo
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/net/lo
  E: SUBSYSTEM=net
  E: INTERFACE=lo
  E: IFINDEX=1
  
  P: /devices/virtual/net/vboxnet0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/net/vboxnet0
  E: SUBSYSTEM=net
  E: INTERFACE=vboxnet0
  E: IFINDEX=4
  
  P: /devices/virtual/ppp/ppp
  N: ppp
  S: char/108:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/ppp/ppp
  E: SUBSYSTEM=ppp
  E: DEVNAME=/dev/ppp
  E: MAJOR=108
  E: MINOR=0
  E: DEVLINKS=/dev/char/108:0
  
  P: /devices/virtual/sound/seq
  N: snd/seq
  S: char/116:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/sound/seq
  E: SUBSYSTEM=sound
  E: DEVNAME=snd/seq
  E: MAJOR=116
  E: MINOR=3
  E: DEVLINKS=/dev/char/116:3
  E: TAGS=:udev-acl:
  
  P: /devices/virtual/sound/timer
  N: snd/timer
  S: char/116:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/sound/timer
  E: SUBSYSTEM=sound
  E: DEVNAME=snd/timer
  E: MAJOR=116
  E: MINOR=2
  E: DEVLINKS=/dev/char/116:2
  E: TAGS=:udev-acl:
  
  P: /devices/virtual/thermal/cooling_device0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device0
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/cooling_device1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device1
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/cooling_device2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device2
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/cooling_device3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device3
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/thermal_zone0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/thermal_zone0
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/tty/console
  N: console
  S: char/5:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/console
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/console
  E: MAJOR=5
  E: MINOR=1
  E: DEVLINKS=/dev/char/5:1
  
  P: /devices/virtual/tty/ptmx
  N: ptmx
  S: char/5:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/ptmx
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/ptmx
  E: MAJOR=5
  E: MINOR=2
  E: DEVMODE=0666
  E: DEVLINKS=/dev/char/5:2
  
  P: /devices/virtual/tty/tty
  N: tty
  S: char/5:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty
  E: MAJOR=5
  E: MINOR=0
  E: DEVMODE=0666
  E: DEVLINKS=/dev/char/5:0
  
  P: /devices/virtual/tty/tty0
  N: tty0
  S: char/4:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty0
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty0
  E: MAJOR=4
  E: MINOR=0
  E: DEVLINKS=/dev/char/4:0
  
  P: /devices/virtual/tty/tty1
  N: tty1
  S: char/4:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty1
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty1
  E: MAJOR=4
  E: MINOR=1
  E: DEVLINKS=/dev/char/4:1
  
  P: /devices/virtual/tty/tty10
  N: tty10
  S: char/4:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty10
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty10
  E: MAJOR=4
  E: MINOR=10
  E: DEVLINKS=/dev/char/4:10
  
  P: /devices/virtual/tty/tty11
  N: tty11
  S: char/4:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty11
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty11
  E: MAJOR=4
  E: MINOR=11
  E: DEVLINKS=/dev/char/4:11
  
  P: /devices/virtual/tty/tty12
  N: tty12
  S: char/4:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty12
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty12
  E: MAJOR=4
  E: MINOR=12
  E: DEVLINKS=/dev/char/4:12
  
  P: /devices/virtual/tty/tty13
  N: tty13
  S: char/4:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty13
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty13
  E: MAJOR=4
  E: MINOR=13
  E: DEVLINKS=/dev/char/4:13
  
  P: /devices/virtual/tty/tty14
  N: tty14
  S: char/4:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty14
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty14
  E: MAJOR=4
  E: MINOR=14
  E: DEVLINKS=/dev/char/4:14
  
  P: /devices/virtual/tty/tty15
  N: tty15
  S: char/4:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty15
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty15
  E: MAJOR=4
  E: MINOR=15
  E: DEVLINKS=/dev/char/4:15
  
  P: /devices/virtual/tty/tty16
  N: tty16
  S: char/4:16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty16
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty16
  E: MAJOR=4
  E: MINOR=16
  E: DEVLINKS=/dev/char/4:16
  
  P: /devices/virtual/tty/tty17
  N: tty17
  S: char/4:17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty17
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty17
  E: MAJOR=4
  E: MINOR=17
  E: DEVLINKS=/dev/char/4:17
  
  P: /devices/virtual/tty/tty18
  N: tty18
  S: char/4:18
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty18
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty18
  E: MAJOR=4
  E: MINOR=18
  E: DEVLINKS=/dev/char/4:18
  
  P: /devices/virtual/tty/tty19
  N: tty19
  S: char/4:19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty19
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty19
  E: MAJOR=4
  E: MINOR=19
  E: DEVLINKS=/dev/char/4:19
  
  P: /devices/virtual/tty/tty2
  N: tty2
  S: char/4:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty2
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty2
  E: MAJOR=4
  E: MINOR=2
  E: DEVLINKS=/dev/char/4:2
  
  P: /devices/virtual/tty/tty20
  N: tty20
  S: char/4:20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty20
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty20
  E: MAJOR=4
  E: MINOR=20
  E: DEVLINKS=/dev/char/4:20
  
  P: /devices/virtual/tty/tty21
  N: tty21
  S: char/4:21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty21
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty21
  E: MAJOR=4
  E: MINOR=21
  E: DEVLINKS=/dev/char/4:21
  
  P: /devices/virtual/tty/tty22
  N: tty22
  S: char/4:22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty22
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty22
  E: MAJOR=4
  E: MINOR=22
  E: DEVLINKS=/dev/char/4:22
  
  P: /devices/virtual/tty/tty23
  N: tty23
  S: char/4:23
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty23
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty23
  E: MAJOR=4
  E: MINOR=23
  E: DEVLINKS=/dev/char/4:23
  
  P: /devices/virtual/tty/tty24
  N: tty24
  S: char/4:24
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty24
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty24
  E: MAJOR=4
  E: MINOR=24
  E: DEVLINKS=/dev/char/4:24
  
  P: /devices/virtual/tty/tty25
  N: tty25
  S: char/4:25
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty25
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty25
  E: MAJOR=4
  E: MINOR=25
  E: DEVLINKS=/dev/char/4:25
  
  P: /devices/virtual/tty/tty26
  N: tty26
  S: char/4:26
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty26
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty26
  E: MAJOR=4
  E: MINOR=26
  E: DEVLINKS=/dev/char/4:26
  
  P: /devices/virtual/tty/tty27
  N: tty27
  S: char/4:27
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty27
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty27
  E: MAJOR=4
  E: MINOR=27
  E: DEVLINKS=/dev/char/4:27
  
  P: /devices/virtual/tty/tty28
  N: tty28
  S: char/4:28
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty28
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty28
  E: MAJOR=4
  E: MINOR=28
  E: DEVLINKS=/dev/char/4:28
  
  P: /devices/virtual/tty/tty29
  N: tty29
  S: char/4:29
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty29
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty29
  E: MAJOR=4
  E: MINOR=29
  E: DEVLINKS=/dev/char/4:29
  
  P: /devices/virtual/tty/tty3
  N: tty3
  S: char/4:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty3
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty3
  E: MAJOR=4
  E: MINOR=3
  E: DEVLINKS=/dev/char/4:3
  
  P: /devices/virtual/tty/tty30
  N: tty30
  S: char/4:30
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty30
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty30
  E: MAJOR=4
  E: MINOR=30
  E: DEVLINKS=/dev/char/4:30
  
  P: /devices/virtual/tty/tty31
  N: tty31
  S: char/4:31
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty31
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty31
  E: MAJOR=4
  E: MINOR=31
  E: DEVLINKS=/dev/char/4:31
  
  P: /devices/virtual/tty/tty32
  N: tty32
  S: char/4:32
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty32
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty32
  E: MAJOR=4
  E: MINOR=32
  E: DEVLINKS=/dev/char/4:32
  
  P: /devices/virtual/tty/tty33
  N: tty33
  S: char/4:33
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty33
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty33
  E: MAJOR=4
  E: MINOR=33
  E: DEVLINKS=/dev/char/4:33
  
  P: /devices/virtual/tty/tty34
  N: tty34
  S: char/4:34
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty34
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty34
  E: MAJOR=4
  E: MINOR=34
  E: DEVLINKS=/dev/char/4:34
  
  P: /devices/virtual/tty/tty35
  N: tty35
  S: char/4:35
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty35
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty35
  E: MAJOR=4
  E: MINOR=35
  E: DEVLINKS=/dev/char/4:35
  
  P: /devices/virtual/tty/tty36
  N: tty36
  S: char/4:36
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty36
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty36
  E: MAJOR=4
  E: MINOR=36
  E: DEVLINKS=/dev/char/4:36
  
  P: /devices/virtual/tty/tty37
  N: tty37
  S: char/4:37
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty37
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty37
  E: MAJOR=4
  E: MINOR=37
  E: DEVLINKS=/dev/char/4:37
  
  P: /devices/virtual/tty/tty38
  N: tty38
  S: char/4:38
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty38
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty38
  E: MAJOR=4
  E: MINOR=38
  E: DEVLINKS=/dev/char/4:38
  
  P: /devices/virtual/tty/tty39
  N: tty39
  S: char/4:39
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty39
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty39
  E: MAJOR=4
  E: MINOR=39
  E: DEVLINKS=/dev/char/4:39
  
  P: /devices/virtual/tty/tty4
  N: tty4
  S: char/4:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty4
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty4
  E: MAJOR=4
  E: MINOR=4
  E: DEVLINKS=/dev/char/4:4
  
  P: /devices/virtual/tty/tty40
  N: tty40
  S: char/4:40
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty40
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty40
  E: MAJOR=4
  E: MINOR=40
  E: DEVLINKS=/dev/char/4:40
  
  P: /devices/virtual/tty/tty41
  N: tty41
  S: char/4:41
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty41
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty41
  E: MAJOR=4
  E: MINOR=41
  E: DEVLINKS=/dev/char/4:41
  
  P: /devices/virtual/tty/tty42
  N: tty42
  S: char/4:42
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty42
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty42
  E: MAJOR=4
  E: MINOR=42
  E: DEVLINKS=/dev/char/4:42
  
  P: /devices/virtual/tty/tty43
  N: tty43
  S: char/4:43
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty43
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty43
  E: MAJOR=4
  E: MINOR=43
  E: DEVLINKS=/dev/char/4:43
  
  P: /devices/virtual/tty/tty44
  N: tty44
  S: char/4:44
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty44
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty44
  E: MAJOR=4
  E: MINOR=44
  E: DEVLINKS=/dev/char/4:44
  
  P: /devices/virtual/tty/tty45
  N: tty45
  S: char/4:45
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty45
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty45
  E: MAJOR=4
  E: MINOR=45
  E: DEVLINKS=/dev/char/4:45
  
  P: /devices/virtual/tty/tty46
  N: tty46
  S: char/4:46
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty46
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty46
  E: MAJOR=4
  E: MINOR=46
  E: DEVLINKS=/dev/char/4:46
  
  P: /devices/virtual/tty/tty47
  N: tty47
  S: char/4:47
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty47
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty47
  E: MAJOR=4
  E: MINOR=47
  E: DEVLINKS=/dev/char/4:47
  
  P: /devices/virtual/tty/tty48
  N: tty48
  S: char/4:48
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty48
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty48
  E: MAJOR=4
  E: MINOR=48
  E: DEVLINKS=/dev/char/4:48
  
  P: /devices/virtual/tty/tty49
  N: tty49
  S: char/4:49
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty49
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty49
  E: MAJOR=4
  E: MINOR=49
  E: DEVLINKS=/dev/char/4:49
  
  P: /devices/virtual/tty/tty5
  N: tty5
  S: char/4:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty5
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty5
  E: MAJOR=4
  E: MINOR=5
  E: DEVLINKS=/dev/char/4:5
  
  P: /devices/virtual/tty/tty50
  N: tty50
  S: char/4:50
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty50
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty50
  E: MAJOR=4
  E: MINOR=50
  E: DEVLINKS=/dev/char/4:50
  
  P: /devices/virtual/tty/tty51
  N: tty51
  S: char/4:51
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty51
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty51
  E: MAJOR=4
  E: MINOR=51
  E: DEVLINKS=/dev/char/4:51
  
  P: /devices/virtual/tty/tty52
  N: tty52
  S: char/4:52
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty52
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty52
  E: MAJOR=4
  E: MINOR=52
  E: DEVLINKS=/dev/char/4:52
  
  P: /devices/virtual/tty/tty53
  N: tty53
  S: char/4:53
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty53
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty53
  E: MAJOR=4
  E: MINOR=53
  E: DEVLINKS=/dev/char/4:53
  
  P: /devices/virtual/tty/tty54
  N: tty54
  S: char/4:54
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty54
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty54
  E: MAJOR=4
  E: MINOR=54
  E: DEVLINKS=/dev/char/4:54
  
  P: /devices/virtual/tty/tty55
  N: tty55
  S: char/4:55
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty55
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty55
  E: MAJOR=4
  E: MINOR=55
  E: DEVLINKS=/dev/char/4:55
  
  P: /devices/virtual/tty/tty56
  N: tty56
  S: char/4:56
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty56
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty56
  E: MAJOR=4
  E: MINOR=56
  E: DEVLINKS=/dev/char/4:56
  
  P: /devices/virtual/tty/tty57
  N: tty57
  S: char/4:57
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty57
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty57
  E: MAJOR=4
  E: MINOR=57
  E: DEVLINKS=/dev/char/4:57
  
  P: /devices/virtual/tty/tty58
  N: tty58
  S: char/4:58
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty58
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty58
  E: MAJOR=4
  E: MINOR=58
  E: DEVLINKS=/dev/char/4:58
  
  P: /devices/virtual/tty/tty59
  N: tty59
  S: char/4:59
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty59
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty59
  E: MAJOR=4
  E: MINOR=59
  E: DEVLINKS=/dev/char/4:59
  
  P: /devices/virtual/tty/tty6
  N: tty6
  S: char/4:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty6
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty6
  E: MAJOR=4
  E: MINOR=6
  E: DEVLINKS=/dev/char/4:6
  
  P: /devices/virtual/tty/tty60
  N: tty60
  S: char/4:60
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty60
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty60
  E: MAJOR=4
  E: MINOR=60
  E: DEVLINKS=/dev/char/4:60
  
  P: /devices/virtual/tty/tty61
  N: tty61
  S: char/4:61
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty61
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty61
  E: MAJOR=4
  E: MINOR=61
  E: DEVLINKS=/dev/char/4:61
  
  P: /devices/virtual/tty/tty62
  N: tty62
  S: char/4:62
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty62
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty62
  E: MAJOR=4
  E: MINOR=62
  E: DEVLINKS=/dev/char/4:62
  
  P: /devices/virtual/tty/tty63
  N: tty63
  S: char/4:63
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty63
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty63
  E: MAJOR=4
  E: MINOR=63
  E: DEVLINKS=/dev/char/4:63
  
  P: /devices/virtual/tty/tty7
  N: tty7
  S: char/4:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty7
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty7
  E: MAJOR=4
  E: MINOR=7
  E: DEVLINKS=/dev/char/4:7
  
  P: /devices/virtual/tty/tty8
  N: tty8
  S: char/4:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty8
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty8
  E: MAJOR=4
  E: MINOR=8
  E: DEVLINKS=/dev/char/4:8
  
  P: /devices/virtual/tty/tty9
  N: tty9
  S: char/4:9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty9
  E: SUBSYSTEM=tty
  E: DEVNAME=/dev/tty9
  E: MAJOR=4
  E: MINOR=9
  E: DEVLINKS=/dev/char/4:9
  
  P: /devices/virtual/usbmon/usbmon0
  N: usbmon0
  S: char/252:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/usbmon/usbmon0
  E: SUBSYSTEM=usbmon
  E: DEVNAME=/dev/usbmon0
  E: MAJOR=252
  E: MINOR=0
  E: DEVLINKS=/dev/char/252:0
  
  P: /devices/virtual/vc/vcs
  N: vcs
  S: char/7:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcs
  E: MAJOR=7
  E: MINOR=0
  E: DEVLINKS=/dev/char/7:0
  
  P: /devices/virtual/vc/vcs1
  N: vcs1
  S: char/7:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs1
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcs1
  E: MAJOR=7
  E: MINOR=1
  E: DEVLINKS=/dev/char/7:1
  
  P: /devices/virtual/vc/vcs2
  N: vcs2
  S: char/7:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs2
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcs2
  E: MAJOR=7
  E: MINOR=2
  E: DEVLINKS=/dev/char/7:2
  
  P: /devices/virtual/vc/vcs3
  N: vcs3
  S: char/7:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs3
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcs3
  E: MAJOR=7
  E: MINOR=3
  E: DEVLINKS=/dev/char/7:3
  
  P: /devices/virtual/vc/vcs4
  N: vcs4
  S: char/7:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs4
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcs4
  E: MAJOR=7
  E: MINOR=4
  E: DEVLINKS=/dev/char/7:4
  
  P: /devices/virtual/vc/vcs5
  N: vcs5
  S: char/7:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs5
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcs5
  E: MAJOR=7
  E: MINOR=5
  E: DEVLINKS=/dev/char/7:5
  
  P: /devices/virtual/vc/vcs6
  N: vcs6
  S: char/7:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs6
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcs6
  E: MAJOR=7
  E: MINOR=6
  E: DEVLINKS=/dev/char/7:6
  
  P: /devices/virtual/vc/vcs63
  N: vcs63
  S: char/7:63
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs63
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcs63
  E: MAJOR=7
  E: MINOR=63
  E: DEVLINKS=/dev/char/7:63
  
  P: /devices/virtual/vc/vcs7
  N: vcs7
  S: char/7:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs7
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcs7
  E: MAJOR=7
  E: MINOR=7
  E: DEVLINKS=/dev/char/7:7
  
  P: /devices/virtual/vc/vcsa
  N: vcsa
  S: char/7:128
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcsa
  E: MAJOR=7
  E: MINOR=128
  E: DEVLINKS=/dev/char/7:128
  
  P: /devices/virtual/vc/vcsa1
  N: vcsa1
  S: char/7:129
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa1
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcsa1
  E: MAJOR=7
  E: MINOR=129
  E: DEVLINKS=/dev/char/7:129
  
  P: /devices/virtual/vc/vcsa2
  N: vcsa2
  S: char/7:130
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa2
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcsa2
  E: MAJOR=7
  E: MINOR=130
  E: DEVLINKS=/dev/char/7:130
  
  P: /devices/virtual/vc/vcsa3
  N: vcsa3
  S: char/7:131
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa3
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcsa3
  E: MAJOR=7
  E: MINOR=131
  E: DEVLINKS=/dev/char/7:131
  
  P: /devices/virtual/vc/vcsa4
  N: vcsa4
  S: char/7:132
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa4
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcsa4
  E: MAJOR=7
  E: MINOR=132
  E: DEVLINKS=/dev/char/7:132
  
  P: /devices/virtual/vc/vcsa5
  N: vcsa5
  S: char/7:133
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa5
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcsa5
  E: MAJOR=7
  E: MINOR=133
  E: DEVLINKS=/dev/char/7:133
  
  P: /devices/virtual/vc/vcsa6
  N: vcsa6
  S: char/7:134
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa6
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcsa6
  E: MAJOR=7
  E: MINOR=134
  E: DEVLINKS=/dev/char/7:134
  
  P: /devices/virtual/vc/vcsa63
  N: vcsa63
  S: char/7:191
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa63
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcsa63
  E: MAJOR=7
  E: MINOR=191
  E: DEVLINKS=/dev/char/7:191
  
  P: /devices/virtual/vc/vcsa7
  N: vcsa7
  S: char/7:135
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa7
  E: SUBSYSTEM=vc
  E: DEVNAME=/dev/vcsa7
  E: MAJOR=7
  E: MINOR=135
  E: DEVLINKS=/dev/char/7:135
  
  P: /devices/virtual/video_output/acpi_video0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/video_output/acpi_video0
  E: SUBSYSTEM=video_output
  
  P: /devices/virtual/vtconsole/vtcon0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vtconsole/vtcon0
  E: SUBSYSTEM=vtconsole
  
  P: /devices/virtual/vtconsole/vtcon1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vtconsole/vtcon1
  E: SUBSYSTEM=vtconsole
  
  P: /devices/virtual/wmi/05901221-D566-11D1-B2F0-00A0C9062910
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/05901221-D566-11D1-B2F0-00A0C9062910
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:05901221-D566-11D1-B2F0-00A0C9062910
  
  P: /devices/virtual/wmi/36916B91-1A64-4583-84D0-53830FB9108D
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/36916B91-1A64-4583-84D0-53830FB9108D
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:36916B91-1A64-4583-84D0-53830FB9108D
  
  P: /devices/virtual/wmi/5923DD45-0480-4ED5-B61A-C9EC6C90E26A
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/5923DD45-0480-4ED5-B61A-C9EC6C90E26A
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:5923DD45-0480-4ED5-B61A-C9EC6C90E26A
  
  P: /devices/virtual/wmi/61EF69EA-865C-4BC3-A502-A0DEBA0CB531
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/61EF69EA-865C-4BC3-A502-A0DEBA0CB531
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:61EF69EA-865C-4BC3-A502-A0DEBA0CB531
  
  P: /devices/virtual/wmi/653A064F-A23A-485F-B3D9-13F6532A0182
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/653A064F-A23A-485F-B3D9-13F6532A0182
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:653A064F-A23A-485F-B3D9-13F6532A0182
  
  P: /devices/virtual/wmi/676AA15E-6A47-4D9F-A2CC-1E6D18D14026
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/676AA15E-6A47-4D9F-A2CC-1E6D18D14026
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:676AA15E-6A47-4D9F-A2CC-1E6D18D14026
  
  P: /devices/virtual/wmi/6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3
  
  P: /devices/virtual/wmi/79772EC5-04B1-4BFD-843C-61E7F77B6CC9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/79772EC5-04B1-4BFD-843C-61E7F77B6CC9
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:79772EC5-04B1-4BFD-843C-61E7F77B6CC9
  
  P: /devices/virtual/wmi/83B9D139-CE71-45DB-A7A6-2628D3A65F4C
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/83B9D139-CE71-45DB-A7A6-2628D3A65F4C
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:83B9D139-CE71-45DB-A7A6-2628D3A65F4C
  
  P: /devices/virtual/wmi/95764E09-FB56-4E83-B31A-37761F60994A
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/95764E09-FB56-4E83-B31A-37761F60994A
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:95764E09-FB56-4E83-B31A-37761F60994A
  
  P: /devices/virtual/wmi/A7C9A0B7-4C9D-4C72-83BB-53A3459171DF
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/A7C9A0B7-4C9D-4C72-83BB-53A3459171DF
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:A7C9A0B7-4C9D-4C72-83BB-53A3459171DF
  
  P: /devices/virtual/wmi/AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B
  
  P: /devices/virtual/wmi/CC1A61AC-4256-41A3-B9E0-05A445ADE2F5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/CC1A61AC-4256-41A3-B9E0-05A445ADE2F5
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:CC1A61AC-4256-41A3-B9E0-05A445ADE2F5
  
  P: /devices/virtual/wmi/CFF94C79-6C77-4AF7-AC56-7DD0CE01C997
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/CFF94C79-6C77-4AF7-AC56-7DD0CE01C997
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:CFF94C79-6C77-4AF7-AC56-7DD0CE01C997
  
  P: /devices/virtual/wmi/DB85B1A7-069A-4ABB-A2B5-D186A21B80F1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/DB85B1A7-069A-4ABB-A2B5-D186A21B80F1
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:DB85B1A7-069A-4ABB-A2B5-D186A21B80F1
  
  P: /devices/virtual/wmi/E78C4453-0227-4861-9EDE-F5600B4A3D39
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/E78C4453-0227-4861-9EDE-F5600B4A3D39
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:E78C4453-0227-4861-9EDE-F5600B4A3D39
  
  P: /devices/virtual/wmi/FAAA1397-1188-448F-8516-9A07987DD38A
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/FAAA1397-1188-448F-8516-9A07987DD38A
  E: SUBSYSTEM=wmi
  E: MODALIAS=wmi:FAAA1397-1188-448F-8516-9A07987DD38A
  
-----  udevinfo end -----
/devices/LNXSYSTM:00
/devices/LNXSYSTM:00/LNXCPU:00
/devices/LNXSYSTM:00/LNXCPU:01
/devices/LNXSYSTM:00/LNXCPU:02
/devices/LNXSYSTM:00/LNXCPU:03
/devices/LNXSYSTM:00/LNXPWRBN:00
/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3
  name: /dev/input/event3
  links: /dev/char/13:67
/devices/LNXSYSTM:00/LNXSYBUS:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:26
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:27
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:28
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:29
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/device:2a
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7/event7
  name: /dev/input/event7
  links: /dev/char/13:71
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/PNP0C14:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/ACPI0003:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/ACPI0003:00/power_supply/AC
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/INT0800:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0000:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0100:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0103:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0200:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0303:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0B00:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C02:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C04:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C09:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0A:00/power_supply/BAT0
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:01
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:02
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:03
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:04
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:05
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:06
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0F:07
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/SYN1B1C:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:03
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/device:05
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/device:05/device:06
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/device:05/device:07
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/device:09
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/device:09/device:0a
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/device:09/device:0b
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d/device:0e
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d/device:0f
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d/device:10
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0c/device:0d/device:11
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/device:13
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:14
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:14/device:15
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:16
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:16/device:17
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:18
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:18/device:19
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1a
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1b
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1c
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:1e
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:1e/device:1f
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:1e/device:20
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:21
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:21/device:22
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:21/device:23
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:24
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1d/device:25
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0
  name: /dev/input/event0
  links: /dev/char/13:64
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2/event2
  name: /dev/input/event2
  links: /dev/char/13:66
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1
  name: /dev/input/event1
  links: /dev/char/13:65
/devices/LNXSYSTM:00/LNXTHERM:00
/devices/LNXSYSTM:00/LNXTHERM:00/LNXPOWER:00
/devices/LNXSYSTM:00/LNXTHERM:00/LNXTHERM:01
/devices/LNXSYSTM:00/LNXTHERM:00/PNP0C0B:00
/devices/pci0000:00/0000:00:00.0
/devices/pci0000:00/0000:00:02.0
/devices/pci0000:00/0000:00:02.0/drm/card0
  name: /dev/dri/card0
  links: /dev/char/226:0
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1
/devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1
/devices/pci0000:00/0000:00:02.0/drm/controlD64
  name: /dev/dri/controlD64
  links: /dev/char/226:64
/devices/pci0000:00/0000:00:02.0/graphics/fb0
  name: /dev/fb0
  links: /dev/char/29:0
/devices/pci0000:00/0000:00:02.0/i2c-0
/devices/pci0000:00/0000:00:02.0/i2c-1
/devices/pci0000:00/0000:00:02.1
/devices/pci0000:00/0000:00:1b.0
/devices/pci0000:00/0000:00:1b.0/sound/card0
/devices/pci0000:00/0000:00:1b.0/sound/card0/hwC0D0
  name: /dev/snd/hwC0D0
  links: /dev/char/116:6
/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c
  name: /dev/snd/pcmC0D0c
  links: /dev/char/116:5
/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p
  name: /dev/snd/pcmC0D0p
  links: /dev/char/116:4
/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0
  name: /dev/snd/controlC0
  links: /dev/char/116:7, /dev/snd/by-path/pci-0000:00:1b.0
/devices/pci0000:00/0000:00:1c.0
/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie01
/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie04
/devices/pci0000:00/0000:00:1c.0/0000:00:1c.0:pcie08
/devices/pci0000:00/0000:00:1c.0/0000:01:00.0
/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
/devices/pci0000:00/0000:00:1c.0/pci_bus/0000:01
/devices/pci0000:00/0000:00:1c.1
/devices/pci0000:00/0000:00:1c.1/0000:00:1c.1:pcie01
/devices/pci0000:00/0000:00:1c.1/0000:00:1c.1:pcie04
/devices/pci0000:00/0000:00:1c.1/0000:00:1c.1:pcie08
/devices/pci0000:00/0000:00:1c.1/0000:02:00.0
/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth1
/devices/pci0000:00/0000:00:1c.1/pci_bus/0000:02
/devices/pci0000:00/0000:00:1d.0
/devices/pci0000:00/0000:00:1d.0/usb2
  name: /dev/bus/usb/002/001
  links: /dev/char/189:128
/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
/devices/pci0000:00/0000:00:1d.0/usbmon/usbmon2
  name: /dev/usbmon2
  links: /dev/char/252:2
/devices/pci0000:00/0000:00:1d.1
/devices/pci0000:00/0000:00:1d.1/usb3
  name: /dev/bus/usb/003/001
  links: /dev/char/189:256
/devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
/devices/pci0000:00/0000:00:1d.1/usbmon/usbmon3
  name: /dev/usbmon3
  links: /dev/char/252:3
/devices/pci0000:00/0000:00:1d.2
/devices/pci0000:00/0000:00:1d.2/usb4
  name: /dev/bus/usb/004/001
  links: /dev/char/189:384
/devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
/devices/pci0000:00/0000:00:1d.2/usbmon/usbmon4
  name: /dev/usbmon4
  links: /dev/char/252:4
/devices/pci0000:00/0000:00:1d.3
/devices/pci0000:00/0000:00:1d.3/usb5
  name: /dev/bus/usb/005/001
  links: /dev/char/189:512
/devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
/devices/pci0000:00/0000:00:1d.3/usbmon/usbmon5
  name: /dev/usbmon5
  links: /dev/char/252:5
/devices/pci0000:00/0000:00:1d.7
/devices/pci0000:00/0000:00:1d.7/usb1
  name: /dev/bus/usb/001/001
  links: /dev/char/189:0
/devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
/devices/pci0000:00/0000:00:1d.7/usb1/1-4
  name: /dev/bus/usb/001/002
  links: /dev/char/189:1
/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0
/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5
/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5/event5
  name: /dev/input/event5
  links: /dev/char/13:69, /dev/input/by-id/usb-Suyin_1.3M_WebCam_HF1315-S32B-OV01-VA-R02.01.05-event-if00, /dev/input/by-path/pci-0000:00:1d.7-usb-0:4:1.0-event
/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/video4linux/video0
  name: /dev/video0
  links: /dev/char/81:0, /dev/v4l/by-id/usb-Suyin_1.3M_WebCam_HF1315-S32B-OV01-VA-R02.01.05-video-index0, /dev/v4l/by-path/pci-0000:00:1d.7-usb-0:4:1.0-video-index0
/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.1
/devices/pci0000:00/0000:00:1d.7/usb1/1-5
  name: /dev/bus/usb/001/003
  links: /dev/char/189:2
/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0
/devices/pci0000:00/0000:00:1d.7/usbmon/usbmon1
  name: /dev/usbmon1
  links: /dev/char/252:1
/devices/pci0000:00/0000:00:1e.0
/devices/pci0000:00/0000:00:1e.0/pci_bus/0000:05
/devices/pci0000:00/0000:00:1f.0
/devices/pci0000:00/0000:00:1f.2
/devices/pci0000:00/0000:00:1f.2/host0
/devices/pci0000:00/0000:00:1f.2/host0/scsi_host/host0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda
  name: /dev/sda
  links: /dev/block/8:0, /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0, /dev/disk/by-id/wwn-0x50000392f9181995
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1
  name: /dev/sda1
  links: /dev/block/8:1, /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part1, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part1, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1, /dev/disk/by-uuid/58682f5c-0155-4154-adff-b3bdd58cc626, /dev/disk/by-id/wwn-0x50000392f9181995-part1, /dev/root
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2
  name: /dev/sda2
  links: /dev/block/8:2, /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part2, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part2, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2, /dev/disk/by-uuid/d7a9a922-eb3e-4c30-88d4-d026e9cb1c67, /dev/disk/by-id/wwn-0x50000392f9181995-part2
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda3
  name: /dev/sda3
  links: /dev/block/8:3, /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part3, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part3, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part3, /dev/disk/by-uuid/0A728F44728F340B, /dev/disk/by-label/Acer, /dev/disk/by-id/wwn-0x50000392f9181995-part3
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda4
  name: /dev/sda4
  links: /dev/block/8:4, /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part4, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part4, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part4, /dev/disk/by-uuid/b6a0eae2-ce1c-4ce0-9831-085826248369, /dev/disk/by-id/wwn-0x50000392f9181995-part4
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
  name: /dev/bsg/0:0:0:0
  links: /dev/char/253:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_disk/0:0:0:0
/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
  name: /dev/sg0
  links: /dev/char/21:0
/devices/pci0000:00/0000:00:1f.2/host1
/devices/pci0000:00/0000:00:1f.2/host1/scsi_host/host1
/devices/pci0000:00/0000:00:1f.2/host2
/devices/pci0000:00/0000:00:1f.2/host2/scsi_host/host2
/devices/pci0000:00/0000:00:1f.2/host3
/devices/pci0000:00/0000:00:1f.2/host3/scsi_host/host3
/devices/pci0000:00/0000:00:1f.3
/devices/pci0000:00/pci_bus/0000:00
/devices/platform/Fixed
/devices/platform/Fixed
/devices/platform/eisa.0
/devices/platform/i8042
/devices/platform/i8042/serio0
/devices/platform/i8042/serio0/input/input4
/devices/platform/i8042/serio0/input/input4/event4
  name: /dev/input/event4
  links: /dev/char/13:68, /dev/input/by-path/platform-i8042-serio-0-event-kbd
/devices/platform/i8042/serio1
/devices/platform/i8042/serio1/input/input6
/devices/platform/i8042/serio1/input/input6/event6
  name: /dev/input/event6
  links: /dev/char/13:70, /dev/input/by-path/platform-i8042-serio-1-event-mouse
/devices/platform/i8042/serio1/input/input6/mouse0
  name: /dev/input/mouse0
  links: /dev/char/13:32, /dev/input/by-path/platform-i8042-serio-1-mouse
/devices/platform/pcspkr
/devices/platform/serial8250
/devices/platform/serial8250/tty/ttyS0
  name: /dev/ttyS0
  links: /dev/char/4:64
/devices/platform/serial8250/tty/ttyS1
  name: /dev/ttyS1
  links: /dev/char/4:65
/devices/platform/serial8250/tty/ttyS2
  name: /dev/ttyS2
  links: /dev/char/4:66
/devices/platform/serial8250/tty/ttyS3
  name: /dev/ttyS3
  links: /dev/char/4:67
/devices/platform/vboxdrv.0
/devices/pnp0/00:00
/devices/pnp0/00:01
/devices/pnp0/00:02
/devices/pnp0/00:03
/devices/pnp0/00:03/rtc/rtc0
  name: /dev/rtc0
  links: /dev/char/254:0, /dev/rtc
/devices/pnp0/00:04
/devices/pnp0/00:05
/devices/pnp0/00:06
/devices/pnp0/00:07
/devices/pnp0/00:08
/devices/virtual/backlight/acpi_video0
/devices/virtual/bdi/0:20
/devices/virtual/bdi/1:0
/devices/virtual/bdi/1:1
/devices/virtual/bdi/1:10
/devices/virtual/bdi/1:11
/devices/virtual/bdi/1:12
/devices/virtual/bdi/1:13
/devices/virtual/bdi/1:14
/devices/virtual/bdi/1:15
/devices/virtual/bdi/1:2
/devices/virtual/bdi/1:3
/devices/virtual/bdi/1:4
/devices/virtual/bdi/1:5
/devices/virtual/bdi/1:6
/devices/virtual/bdi/1:7
/devices/virtual/bdi/1:8
/devices/virtual/bdi/1:9
/devices/virtual/bdi/7:0
/devices/virtual/bdi/7:1
/devices/virtual/bdi/7:2
/devices/virtual/bdi/7:3
/devices/virtual/bdi/7:4
/devices/virtual/bdi/7:5
/devices/virtual/bdi/7:6
/devices/virtual/bdi/7:7
/devices/virtual/bdi/8:0
/devices/virtual/bdi/default
/devices/virtual/block/loop0
  name: /dev/loop0
  links: /dev/block/7:0
/devices/virtual/block/loop1
  name: /dev/loop1
  links: /dev/block/7:1
/devices/virtual/block/loop2
  name: /dev/loop2
  links: /dev/block/7:2
/devices/virtual/block/loop3
  name: /dev/loop3
  links: /dev/block/7:3
/devices/virtual/block/loop4
  name: /dev/loop4
  links: /dev/block/7:4
/devices/virtual/block/loop5
  name: /dev/loop5
  links: /dev/block/7:5
/devices/virtual/block/loop6
  name: /dev/loop6
  links: /dev/block/7:6
/devices/virtual/block/loop7
  name: /dev/loop7
  links: /dev/block/7:7
/devices/virtual/block/ram0
  name: /dev/ram0
  links: /dev/block/1:0
/devices/virtual/block/ram1
  name: /dev/ram1
  links: /dev/block/1:1
/devices/virtual/block/ram10
  name: /dev/ram10
  links: /dev/block/1:10
/devices/virtual/block/ram11
  name: /dev/ram11
  links: /dev/block/1:11
/devices/virtual/block/ram12
  name: /dev/ram12
  links: /dev/block/1:12
/devices/virtual/block/ram13
  name: /dev/ram13
  links: /dev/block/1:13
/devices/virtual/block/ram14
  name: /dev/ram14
  links: /dev/block/1:14
/devices/virtual/block/ram15
  name: /dev/ram15
  links: /dev/block/1:15
/devices/virtual/block/ram2
  name: /dev/ram2
  links: /dev/block/1:2
/devices/virtual/block/ram3
  name: /dev/ram3
  links: /dev/block/1:3
/devices/virtual/block/ram4
  name: /dev/ram4
  links: /dev/block/1:4
/devices/virtual/block/ram5
  name: /dev/ram5
  links: /dev/block/1:5
/devices/virtual/block/ram6
  name: /dev/ram6
  links: /dev/block/1:6
/devices/virtual/block/ram7
  name: /dev/ram7
  links: /dev/block/1:7
/devices/virtual/block/ram8
  name: /dev/ram8
  links: /dev/block/1:8
/devices/virtual/block/ram9
  name: /dev/ram9
  links: /dev/block/1:9
/devices/virtual/dmi/id
/devices/virtual/graphics/fbcon
/devices/virtual/hwmon/hwmon0
/devices/virtual/input/mice
  name: /dev/input/mice
  links: /dev/char/13:63
/devices/virtual/mem/full
  name: /dev/full
  links: /dev/char/1:7
/devices/virtual/mem/kmsg
  name: /dev/kmsg
  links: /dev/char/1:11
/devices/virtual/mem/mem
  name: /dev/mem
  links: /dev/char/1:1
/devices/virtual/mem/null
  name: /dev/null
  links: /dev/char/1:3
/devices/virtual/mem/oldmem
  name: /dev/oldmem
  links: /dev/char/1:12
/devices/virtual/mem/port
  name: /dev/port
  links: /dev/char/1:4
/devices/virtual/mem/random
  name: /dev/random
  links: /dev/char/1:8
/devices/virtual/mem/urandom
  name: /dev/urandom
  links: /dev/char/1:9
/devices/virtual/mem/zero
  name: /dev/zero
  links: /dev/char/1:5
/devices/virtual/misc/agpgart
  name: /dev/agpgart
  links: /dev/char/10:175
/devices/virtual/misc/cpu_dma_latency
  name: /dev/cpu_dma_latency
  links: /dev/char/10:58
/devices/virtual/misc/device-mapper
  name: /dev/mapper/control
  links: /dev/char/10:59
/devices/virtual/misc/ecryptfs
  name: /dev/ecryptfs
  links: /dev/char/10:61
/devices/virtual/misc/fuse
  name: /dev/fuse
  links: /dev/char/10:229
/devices/virtual/misc/hpet
  name: /dev/hpet
  links: /dev/char/10:228
/devices/virtual/misc/mcelog
  name: /dev/mcelog
  links: /dev/char/10:227
/devices/virtual/misc/network_latency
  name: /dev/network_latency
  links: /dev/char/10:57
/devices/virtual/misc/network_throughput
  name: /dev/network_throughput
  links: /dev/char/10:56
/devices/virtual/misc/pktcdvd
  name: /dev/pktcdvd/control
  links: /dev/char/10:60
/devices/virtual/misc/psaux
  name: /dev/psaux
  links: /dev/char/10:1
/devices/virtual/misc/rfkill
  name: /dev/rfkill
  links: /dev/char/10:62
/devices/virtual/misc/snapshot
  name: /dev/snapshot
  links: /dev/char/10:231
/devices/virtual/misc/tun
  name: /dev/net/tun
  links: /dev/char/10:200
/devices/virtual/misc/uinput
  name: /dev/uinput
  links: /dev/char/10:223
/devices/virtual/misc/vboxdrv
  name: /dev/vboxdrv
  links: /dev/char/10:55
/devices/virtual/misc/vboxnetctl
  name: /dev/vboxnetctl
  links: /dev/char/10:54
/devices/virtual/misc/vga_arbiter
  name: /dev/vga_arbiter
  links: /dev/char/10:63
/devices/virtual/net/lo
/devices/virtual/net/vboxnet0
/devices/virtual/ppp/ppp
  name: /dev/ppp
  links: /dev/char/108:0
/devices/virtual/sound/seq
  name: /dev/snd/seq
  links: /dev/char/116:3
/devices/virtual/sound/timer
  name: /dev/snd/timer
  links: /dev/char/116:2
/devices/virtual/thermal/cooling_device0
/devices/virtual/thermal/cooling_device1
/devices/virtual/thermal/cooling_device2
/devices/virtual/thermal/cooling_device3
/devices/virtual/thermal/thermal_zone0
/devices/virtual/tty/console
  name: /dev/console
  links: /dev/char/5:1
/devices/virtual/tty/ptmx
  name: /dev/ptmx
  links: /dev/char/5:2
/devices/virtual/tty/tty
  name: /dev/tty
  links: /dev/char/5:0
/devices/virtual/tty/tty0
  name: /dev/tty0
  links: /dev/char/4:0
/devices/virtual/tty/tty1
  name: /dev/tty1
  links: /dev/char/4:1
/devices/virtual/tty/tty10
  name: /dev/tty10
  links: /dev/char/4:10
/devices/virtual/tty/tty11
  name: /dev/tty11
  links: /dev/char/4:11
/devices/virtual/tty/tty12
  name: /dev/tty12
  links: /dev/char/4:12
/devices/virtual/tty/tty13
  name: /dev/tty13
  links: /dev/char/4:13
/devices/virtual/tty/tty14
  name: /dev/tty14
  links: /dev/char/4:14
/devices/virtual/tty/tty15
  name: /dev/tty15
  links: /dev/char/4:15
/devices/virtual/tty/tty16
  name: /dev/tty16
  links: /dev/char/4:16
/devices/virtual/tty/tty17
  name: /dev/tty17
  links: /dev/char/4:17
/devices/virtual/tty/tty18
  name: /dev/tty18
  links: /dev/char/4:18
/devices/virtual/tty/tty19
  name: /dev/tty19
  links: /dev/char/4:19
/devices/virtual/tty/tty2
  name: /dev/tty2
  links: /dev/char/4:2
/devices/virtual/tty/tty20
  name: /dev/tty20
  links: /dev/char/4:20
/devices/virtual/tty/tty21
  name: /dev/tty21
  links: /dev/char/4:21
/devices/virtual/tty/tty22
  name: /dev/tty22
  links: /dev/char/4:22
/devices/virtual/tty/tty23
  name: /dev/tty23
  links: /dev/char/4:23
/devices/virtual/tty/tty24
  name: /dev/tty24
  links: /dev/char/4:24
/devices/virtual/tty/tty25
  name: /dev/tty25
  links: /dev/char/4:25
/devices/virtual/tty/tty26
  name: /dev/tty26
  links: /dev/char/4:26
/devices/virtual/tty/tty27
  name: /dev/tty27
  links: /dev/char/4:27
/devices/virtual/tty/tty28
  name: /dev/tty28
  links: /dev/char/4:28
/devices/virtual/tty/tty29
  name: /dev/tty29
  links: /dev/char/4:29
/devices/virtual/tty/tty3
  name: /dev/tty3
  links: /dev/char/4:3
/devices/virtual/tty/tty30
  name: /dev/tty30
  links: /dev/char/4:30
/devices/virtual/tty/tty31
  name: /dev/tty31
  links: /dev/char/4:31
/devices/virtual/tty/tty32
  name: /dev/tty32
  links: /dev/char/4:32
/devices/virtual/tty/tty33
  name: /dev/tty33
  links: /dev/char/4:33
/devices/virtual/tty/tty34
  name: /dev/tty34
  links: /dev/char/4:34
/devices/virtual/tty/tty35
  name: /dev/tty35
  links: /dev/char/4:35
/devices/virtual/tty/tty36
  name: /dev/tty36
  links: /dev/char/4:36
/devices/virtual/tty/tty37
  name: /dev/tty37
  links: /dev/char/4:37
/devices/virtual/tty/tty38
  name: /dev/tty38
  links: /dev/char/4:38
/devices/virtual/tty/tty39
  name: /dev/tty39
  links: /dev/char/4:39
/devices/virtual/tty/tty4
  name: /dev/tty4
  links: /dev/char/4:4
/devices/virtual/tty/tty40
  name: /dev/tty40
  links: /dev/char/4:40
/devices/virtual/tty/tty41
  name: /dev/tty41
  links: /dev/char/4:41
/devices/virtual/tty/tty42
  name: /dev/tty42
  links: /dev/char/4:42
/devices/virtual/tty/tty43
  name: /dev/tty43
  links: /dev/char/4:43
/devices/virtual/tty/tty44
  name: /dev/tty44
  links: /dev/char/4:44
/devices/virtual/tty/tty45
  name: /dev/tty45
  links: /dev/char/4:45
/devices/virtual/tty/tty46
  name: /dev/tty46
  links: /dev/char/4:46
/devices/virtual/tty/tty47
  name: /dev/tty47
  links: /dev/char/4:47
/devices/virtual/tty/tty48
  name: /dev/tty48
  links: /dev/char/4:48
/devices/virtual/tty/tty49
  name: /dev/tty49
  links: /dev/char/4:49
/devices/virtual/tty/tty5
  name: /dev/tty5
  links: /dev/char/4:5
/devices/virtual/tty/tty50
  name: /dev/tty50
  links: /dev/char/4:50
/devices/virtual/tty/tty51
  name: /dev/tty51
  links: /dev/char/4:51
/devices/virtual/tty/tty52
  name: /dev/tty52
  links: /dev/char/4:52
/devices/virtual/tty/tty53
  name: /dev/tty53
  links: /dev/char/4:53
/devices/virtual/tty/tty54
  name: /dev/tty54
  links: /dev/char/4:54
/devices/virtual/tty/tty55
  name: /dev/tty55
  links: /dev/char/4:55
/devices/virtual/tty/tty56
  name: /dev/tty56
  links: /dev/char/4:56
/devices/virtual/tty/tty57
  name: /dev/tty57
  links: /dev/char/4:57
/devices/virtual/tty/tty58
  name: /dev/tty58
  links: /dev/char/4:58
/devices/virtual/tty/tty59
  name: /dev/tty59
  links: /dev/char/4:59
/devices/virtual/tty/tty6
  name: /dev/tty6
  links: /dev/char/4:6
/devices/virtual/tty/tty60
  name: /dev/tty60
  links: /dev/char/4:60
/devices/virtual/tty/tty61
  name: /dev/tty61
  links: /dev/char/4:61
/devices/virtual/tty/tty62
  name: /dev/tty62
  links: /dev/char/4:62
/devices/virtual/tty/tty63
  name: /dev/tty63
  links: /dev/char/4:63
/devices/virtual/tty/tty7
  name: /dev/tty7
  links: /dev/char/4:7
/devices/virtual/tty/tty8
  name: /dev/tty8
  links: /dev/char/4:8
/devices/virtual/tty/tty9
  name: /dev/tty9
  links: /dev/char/4:9
/devices/virtual/usbmon/usbmon0
  name: /dev/usbmon0
  links: /dev/char/252:0
/devices/virtual/vc/vcs
  name: /dev/vcs
  links: /dev/char/7:0
/devices/virtual/vc/vcs1
  name: /dev/vcs1
  links: /dev/char/7:1
/devices/virtual/vc/vcs2
  name: /dev/vcs2
  links: /dev/char/7:2
/devices/virtual/vc/vcs3
  name: /dev/vcs3
  links: /dev/char/7:3
/devices/virtual/vc/vcs4
  name: /dev/vcs4
  links: /dev/char/7:4
/devices/virtual/vc/vcs5
  name: /dev/vcs5
  links: /dev/char/7:5
/devices/virtual/vc/vcs6
  name: /dev/vcs6
  links: /dev/char/7:6
/devices/virtual/vc/vcs63
  name: /dev/vcs63
  links: /dev/char/7:63
/devices/virtual/vc/vcs7
  name: /dev/vcs7
  links: /dev/char/7:7
/devices/virtual/vc/vcsa
  name: /dev/vcsa
  links: /dev/char/7:128
/devices/virtual/vc/vcsa1
  name: /dev/vcsa1
  links: /dev/char/7:129
/devices/virtual/vc/vcsa2
  name: /dev/vcsa2
  links: /dev/char/7:130
/devices/virtual/vc/vcsa3
  name: /dev/vcsa3
  links: /dev/char/7:131
/devices/virtual/vc/vcsa4
  name: /dev/vcsa4
  links: /dev/char/7:132
/devices/virtual/vc/vcsa5
  name: /dev/vcsa5
  links: /dev/char/7:133
/devices/virtual/vc/vcsa6
  name: /dev/vcsa6
  links: /dev/char/7:134
/devices/virtual/vc/vcsa63
  name: /dev/vcsa63
  links: /dev/char/7:191
/devices/virtual/vc/vcsa7
  name: /dev/vcsa7
  links: /dev/char/7:135
/devices/virtual/video_output/acpi_video0
/devices/virtual/vtconsole/vtcon0
/devices/virtual/vtconsole/vtcon1
/devices/virtual/wmi/05901221-D566-11D1-B2F0-00A0C9062910
/devices/virtual/wmi/36916B91-1A64-4583-84D0-53830FB9108D
/devices/virtual/wmi/5923DD45-0480-4ED5-B61A-C9EC6C90E26A
/devices/virtual/wmi/61EF69EA-865C-4BC3-A502-A0DEBA0CB531
/devices/virtual/wmi/653A064F-A23A-485F-B3D9-13F6532A0182
/devices/virtual/wmi/676AA15E-6A47-4D9F-A2CC-1E6D18D14026
/devices/virtual/wmi/6AF4F258-B401-42FD-BE91-3D4AC2D7C0D3
/devices/virtual/wmi/79772EC5-04B1-4BFD-843C-61E7F77B6CC9
/devices/virtual/wmi/83B9D139-CE71-45DB-A7A6-2628D3A65F4C
/devices/virtual/wmi/95764E09-FB56-4E83-B31A-37761F60994A
/devices/virtual/wmi/A7C9A0B7-4C9D-4C72-83BB-53A3459171DF
/devices/virtual/wmi/AAE04F7B-B3C5-4865-95D6-9FAC7FF3E92B
/devices/virtual/wmi/CC1A61AC-4256-41A3-B9E0-05A445ADE2F5
/devices/virtual/wmi/CFF94C79-6C77-4AF7-AC56-7DD0CE01C997
/devices/virtual/wmi/DB85B1A7-069A-4ABB-A2B5-D186A21B80F1
/devices/virtual/wmi/E78C4453-0227-4861-9EDE-F5600B4A3D39
/devices/virtual/wmi/FAAA1397-1188-448F-8516-9A07987DD38A
>> int.13: device names
>> int.14: soft raid
----- soft raid devices -----
----- soft raid devices end -----
>> int.15: geo
>> int.16: parent
  prop read: rdCR.lZF+r4EgHp4 (failed)
  old prop read: rdCR.lZF+r4EgHp4 (failed)
  prop read: rdCR.n_7QNeEnh23 (failed)
  old prop read: rdCR.n_7QNeEnh23 (failed)
  prop read: rdCR.EMpH5pjcahD (failed)
  old prop read: rdCR.EMpH5pjcahD (failed)
  prop read: rdCR.f5u1ucRm+H9 (failed)
  old prop read: rdCR.f5u1ucRm+H9 (failed)
  prop read: rdCR.8uRK7LxiIA2 (failed)
  old prop read: rdCR.8uRK7LxiIA2 (failed)
  prop read: rdCR.AJKleuxpiP0 (failed)
  old prop read: rdCR.AJKleuxpiP0 (failed)
  prop read: rdCR.9N+EecqykME (failed)
  old prop read: rdCR.9N+EecqykME (failed)
  prop read: rdCR.CxwsZFjVASF (failed)
  old prop read: rdCR.CxwsZFjVASF (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_a010 (failed)
  prop read: qLht.PdlOCWxMAH1 (failed)
  old prop read: qLht.PdlOCWxMAH1 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_a011 (failed)
  prop read: _Znp.ta1P8GNKN4D (failed)
  old prop read: _Znp.ta1P8GNKN4D (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_a012 (failed)
  prop read: ruGf.O1P126g_eh2 (failed)
  old prop read: ruGf.O1P126g_eh2 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_27d8 (failed)
  prop read: u1Nb.ZCVQnTUjxO7 (failed)
  old prop read: u1Nb.ZCVQnTUjxO7 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_27d0 (failed)
  prop read: z8Q3._3VzjoUPJG5 (failed)
  old prop read: z8Q3._3VzjoUPJG5 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_27d2 (failed)
  prop read: qTvu.0vNThxjpM16 (failed)
  old prop read: qTvu.0vNThxjpM16 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_27c8 (failed)
  prop read: 1GTX.RSqlCcPC2F4 (failed)
  old prop read: 1GTX.RSqlCcPC2F4 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_27c9 (failed)
  prop read: vayM.ysmVhAXvZd4 (failed)
  old prop read: vayM.ysmVhAXvZd4 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_27ca (failed)
  prop read: mvRC.THjFAlec505 (failed)
  old prop read: mvRC.THjFAlec505 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_27cb (failed)
  prop read: eEx1._hf+eJmJdO5 (failed)
  old prop read: eEx1._hf+eJmJdO5 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_27cc (failed)
  prop read: 5YuN.+6CxPyMngcA (failed)
  old prop read: 5YuN.+6CxPyMngcA (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_2448 (failed)
  prop read: 6NW+.SZEhIj3ISCE (failed)
  old prop read: 6NW+.SZEhIj3ISCE (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_27bc (failed)
  prop read: BUZT.79IsqZc8gE8 (failed)
  old prop read: BUZT.79IsqZc8gE8 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_27c1 (failed)
  prop read: w7Y8.D2p8kvfIMi4 (failed)
  old prop read: w7Y8.D2p8kvfIMi4 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_8086_27da (failed)
  prop read: nS1_.lKifNMuDxy7 (failed)
  old prop read: nS1_.lKifNMuDxy7 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1969_2060 (failed)
  prop read: rBUF.AfcciKaOfeA (failed)
  old prop read: rBUF.AfcciKaOfeA (failed)
  prop read: /org/freedesktop/Hal/devices/pci_14e4_4727 (failed)
  prop read: JNkJ.QPcitGWhgh4 (failed)
  old prop read: JNkJ.QPcitGWhgh4 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0a08 (failed)
  prop read: z9pp.+GmdJItMGB9 (failed)
  old prop read: z9pp.+GmdJItMGB9 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c02 (failed)
  prop read: QL3u.B+yZ9Ve8gC1 (failed)
  old prop read: QL3u.B+yZ9Ve8gC1 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0200 (failed)
  prop read: tWJy.ld94kxNGZf5 (failed)
  old prop read: tWJy.ld94kxNGZf5 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0b00 (failed)
  prop read: KiZ0.WYwRElrJa93 (failed)
  old prop read: KiZ0.WYwRElrJa93 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0103 (failed)
  prop read: ntp4.fG36JLVNse9 (failed)
  old prop read: ntp4.fG36JLVNse9 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c04 (failed)
  prop read: E349.DE8RM9cWQQ8 (failed)
  old prop read: E349.DE8RM9cWQQ8 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_INT0800 (failed)
  prop read: hEKD.jDhFyyFrbg5 (failed)
  old prop read: hEKD.jDhFyyFrbg5 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0303 (failed)
  prop read: NhVi.xhndlW9HXJ7 (failed)
  old prop read: NhVi.xhndlW9HXJ7 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_SYN1b1c (failed)
  prop read: qslm.e21BmhUQX01 (failed)
  old prop read: qslm.e21BmhUQX01 (failed)
  prop read: /org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB (failed)
  prop read: 3OOL.zqDXAFFi3vD (failed)
  old prop read: 3OOL.zqDXAFFi3vD (failed)
  prop read: /org/freedesktop/Hal/devices/volume_uuid_58682f5c_0155_4154_adff_b3bdd58cc626 (failed)
  prop read: bdUI.SE1wIdpsiiC (failed)
  old prop read: bdUI.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/volume_uuid_d7a9a922_eb3e_4c30_88d4_d026e9cb1c67 (failed)
  prop read: 2pkM.SE1wIdpsiiC (failed)
  old prop read: 2pkM.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/volume_uuid_0A728F44728F340B (failed)
  prop read: W__Q.SE1wIdpsiiC (failed)
  old prop read: W__Q.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/volume_uuid_b6a0eae2_ce1c_4ce0_9831_085826248369 (failed)
  prop read: z9FV.SE1wIdpsiiC (failed)
  old prop read: z9FV.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7_if0 (failed)
  prop read: k4bc.9T1GDCLyFd9 (failed)
  old prop read: k4bc.9T1GDCLyFd9 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0_if0 (failed)
  prop read: pBe4.v+N+B0xY+P6 (failed)
  old prop read: pBe4.v+N+B0xY+P6 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1_if0 (failed)
  prop read: uIhY.gkSaZmjGyhD (failed)
  old prop read: uIhY.gkSaZmjGyhD (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2_if0 (failed)
  prop read: zPk0.RTX9xWW_uz4 (failed)
  old prop read: zPk0.RTX9xWW_uz4 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3_if0 (failed)
  prop read: 2XnU.CCckIHJirFC (failed)
  old prop read: 2XnU.CCckIHJirFC (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if0_logicaldev_input (failed)
  prop read: Uc5H.sWuUzJ4g1a5 (failed)
  old prop read: Uc5H.sWuUzJ4g1a5 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_cf2_6250_606569746801_if0 (failed)
  prop read: wkjR.eexAj+JCq_E (failed)
  old prop read: wkjR.eexAj+JCq_E (failed)
  prop read: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input (failed)
  prop read: c3zD.+49ps10DtUF (failed)
  old prop read: c3zD.+49ps10DtUF (failed)
  prop read: /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input (failed)
  prop read: AH6Q.ZHI3OT7LsxA (failed)
  old prop read: AH6Q.ZHI3OT7LsxA (failed)
  prop read: rdCR.j8NaKXDZtZ6 (failed)
  old prop read: rdCR.j8NaKXDZtZ6 (failed)
  prop read: wkFv.j8NaKXDZtZ6 (failed)
  old prop read: wkFv.j8NaKXDZtZ6 (failed)
  prop read: ZsBS.GQNx7L4uPNA (failed)
  old prop read: ZsBS.GQNx7L4uPNA (failed)
  prop read: usDW.ndpeucax6V1 (failed)
  old prop read: usDW.ndpeucax6V1 (failed)
  prop read: L2Ua.ndpeucax6V1 (failed)
  old prop read: L2Ua.ndpeucax6V1 (failed)
  prop read: sG1U.ndpeucax6V1 (failed)
  old prop read: sG1U.ndpeucax6V1 (failed)
----- /proc/modules -----
  binfmt_misc 6599 1 - Live 0xf818e000
  vboxnetadp 6454 0 - Live 0xf8182000
  vboxnetflt 15152 0 - Live 0xf804c000
  vboxdrv 190199 2 vboxnetadp,vboxnetflt, Live 0xf83ba000
  parport_pc 26058 0 - Live 0xf80d1000
  ppdev 5556 0 - Live 0xf8020000
  snd_hda_codec_realtek 218492 1 - Live 0xf8382000
  joydev 8767 0 - Live 0xf801b000
  snd_hda_intel 22235 2 - Live 0xf8196000
  snd_hda_codec 87552 2 snd_hda_codec_realtek,snd_hda_intel, Live 0xf8293000
  snd_hwdep 5040 1 snd_hda_codec, Live 0xf805d000
  snd_pcm 71475 2 snd_hda_intel,snd_hda_codec, Live 0xf81e6000
  i915 295435 4 - Live 0xf8248000
  snd_seq_midi 4588 0 - Live 0xf8178000
  snd_rawmidi 17783 1 snd_seq_midi, Live 0xf8159000
  snd_seq_midi_event 6047 1 snd_seq_midi, Live 0xf8062000
  snd_seq 47174 2 snd_seq_midi,snd_seq_midi_event, Live 0xf87ef000
  drm_kms_helper 30200 1 i915, Live 0xf87cc000
  drm 168060 4 i915,drm_kms_helper, Live 0xf8782000
  snd_timer 19067 2 snd_pcm,snd_seq, Live 0xf81da000
  snd_seq_device 5744 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf81ce000
  lib80211_crypt_tkip 7736 0 - Live 0xf816e000
  uvcvideo 55847 0 - Live 0xf83f6000
  wl 1959533 0 - Live 0xf8412000 (P)
  psmouse 59033 0 - Live 0xf869b000
  snd 49038 13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf8070000
  videodev 43098 1 uvcvideo, Live 0xf8149000
  intel_agp 26566 2 i915, Live 0xf8405000
  serio_raw 4022 0 - Live 0xf8066000
  v4l1_compat 13359 2 uvcvideo,videodev, Live 0xf802b000
  lib80211 5058 2 lib80211_crypt_tkip,wl, Live 0xf81e2000
  agpgart 32011 2 drm,intel_agp, Live 0xf81c4000
  soundcore 880 1 snd, Live 0xf81d7000
  snd_page_alloc 7120 2 snd_hda_intel,snd_pcm, Live 0xf8192000
  i2c_algo_bit 5168 1 i915, Live 0xf819e000
  video 18712 1 i915, Live 0xf8171000
  output 1883 1 video, Live 0xf8160000
  lp 7342 0 - Live 0xf8155000
  parport 31492 3 parport_pc,ppdev,lp, Live 0xf813f000
  ahci 19198 3 - Live 0xf80c2000
  libahci 21728 1 ahci, Live 0xf8068000
  atl1c 29949 0 - Live 0xf8053000
----- /proc/modules end -----
  used irqs: 0,1,8,9,10,12,17,18,20,21,22,40,41,42,43,44,45
=========== end debug info ============
01: None 00.0: 10105 BIOS
  [Created at bios.190]
  Unique ID: rdCR.lZF+r4EgHp4
  Hardware Class: bios
  BIOS Keyboard LED Status:
    Scroll Lock: off
    Num Lock: off
    Caps Lock: off
  Config Status: cfg=new, avail=yes, need=no, active=unknown

02: None 00.0: 10107 System
  [Created at sys.63]
  Unique ID: rdCR.n_7QNeEnh23
  Hardware Class: system
  Model: "System"
  Formfactor: "laptop"
  Driver Info #0:
    Driver Status: thermal,fan are not active
    Driver Activation Cmd: "modprobe thermal; modprobe fan"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

03: None 00.0: 10104 FPU
  [Created at misc.192]
  Unique ID: rdCR.EMpH5pjcahD
  Hardware Class: unknown
  Model: "FPU"
  I/O Ports: 0xf0-0xff (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

04: None 00.0: 0801 DMA controller (8237)
  [Created at misc.206]
  Unique ID: rdCR.f5u1ucRm+H9
  Hardware Class: unknown
  Model: "DMA controller"
  I/O Ports: 0x00-0xcf7 (rw)
  I/O Ports: 0xc0-0xdf (rw)
  I/O Ports: 0x80-0x8f (rw)
  DMA: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

05: None 00.0: 0800 PIC (8259)
  [Created at misc.219]
  Unique ID: rdCR.8uRK7LxiIA2
  Hardware Class: unknown
  Model: "PIC"
  I/O Ports: 0x20-0x21 (rw)
  I/O Ports: 0xa0-0xa1 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

06: None 00.0: 0802 Timer (8254)
  [Created at misc.230]
  Unique ID: rdCR.AJKleuxpiP0
  Hardware Class: unknown
  Model: "Timer"
  IRQ: 0 (9031783 events)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

07: None 00.0: 0900 Keyboard controller
  [Created at misc.251]
  Unique ID: rdCR.9N+EecqykME
  Hardware Class: unknown
  Model: "Keyboard controller"
  I/O Port: 0x60 (rw)
  I/O Port: 0x64 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

10: None 00.0: 10102 Main Memory
  [Created at memory.61]
  Unique ID: rdCR.CxwsZFjVASF
  Hardware Class: memory
  Model: "Main Memory"
  Memory Range: 0x00000000-0x3f7fdfff (rw)
  Memory Size: 1016 MB
  Config Status: cfg=new, avail=yes, need=no, active=unknown

11: PCI 00.0: 0600 Host bridge
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_a010
  Unique ID: qLht.PdlOCWxMAH1
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "Intel Host bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0xa010 
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Driver: "agpgart-intel"
  Driver Modules: "intel_agp"
  Module Alias: "pci:v00008086d0000A010sv00001025sd00000349bc06sc00i00"
  Driver Info #0:
    Driver Status: intel_agp is active
    Driver Activation Cmd: "modprobe intel_agp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

12: PCI 02.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_a011
  Unique ID: _Znp.ta1P8GNKN4D
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel VGA compatible controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0xa011 
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0x58180000-0x581fffff (rw,non-prefetchable)
  I/O Ports: 0x60c0-0x60c7 (rw)
  Memory Range: 0x40000000-0x4fffffff (ro,non-prefetchable)
  Memory Range: 0x58000000-0x580fffff (rw,non-prefetchable)
  IRQ: 43 (187325 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d0000A011sv00001025sd00000349bc03sc00i00"
  Driver Info #0:
    Driver Status: i915 is active
    Driver Activation Cmd: "modprobe i915"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 02.1: 0380 Display controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_a012
  Unique ID: ruGf.O1P126g_eh2
  SysFS ID: /devices/pci0000:00/0000:00:02.1
  SysFS BusID: 0000:00:02.1
  Hardware Class: graphics card
  Model: "Intel Display controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0xa012 
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Memory Range: 0x58100000-0x5817ffff (rw,non-prefetchable)
  Module Alias: "pci:v00008086d0000A012sv00001025sd00000349bc03sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 1b.0: 0403 Audio device
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27d8
  Unique ID: u1Nb.ZCVQnTUjxO7
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801G (ICH7 Family) High Definition Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27d8 "82801G (ICH7 Family) High Definition Audio Controller"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0x02
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0x58200000-0x58203fff (rw,non-prefetchable)
  IRQ: 44 (1492 events)
  Module Alias: "pci:v00008086d000027D8sv00001025sd00000349bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

15: PCI 1c.0: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27d0
  Unique ID: z8Q3._3VzjoUPJG5
  SysFS ID: /devices/pci0000:00/0000:00:1c.0
  SysFS BusID: 0000:00:1c.0
  Hardware Class: bridge
  Model: "Intel 82801G (ICH7 Family) PCI Express Port 1"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27d0 "82801G (ICH7 Family) PCI Express Port 1"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0x02
  Driver: "pcieport"
  IRQ: 40 (no events)
  Module Alias: "pci:v00008086d000027D0sv00001025sd00000349bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

16: PCI 1c.1: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27d2
  Unique ID: qTvu.0vNThxjpM16
  SysFS ID: /devices/pci0000:00/0000:00:1c.1
  SysFS BusID: 0000:00:1c.1
  Hardware Class: bridge
  Model: "Intel 82801G (ICH7 Family) PCI Express Port 2"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27d2 "82801G (ICH7 Family) PCI Express Port 2"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0x02
  Driver: "pcieport"
  IRQ: 41 (no events)
  Module Alias: "pci:v00008086d000027D2sv00001025sd00000349bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

17: PCI 1d.0: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27c8
  Unique ID: 1GTX.RSqlCcPC2F4
  SysFS ID: /devices/pci0000:00/0000:00:1d.0
  SysFS BusID: 0000:00:1d.0
  Hardware Class: usb controller
  Model: "Intel 82801G (ICH7 Family) USB UHCI Controller #1"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27c8 "82801G (ICH7 Family) USB UHCI Controller #1"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0x02
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x6080-0x609f (rw)
  IRQ: 18 (no events)
  Module Alias: "pci:v00008086d000027C8sv00001025sd00000349bc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 1d.1: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27c9
  Unique ID: vayM.ysmVhAXvZd4
  SysFS ID: /devices/pci0000:00/0000:00:1d.1
  SysFS BusID: 0000:00:1d.1
  Hardware Class: usb controller
  Model: "Intel 82801G (ICH7 Family) USB UHCI Controller #2"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27c9 "82801G (ICH7 Family) USB UHCI Controller #2"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0x02
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x6060-0x607f (rw)
  IRQ: 20 (2 events)
  Module Alias: "pci:v00008086d000027C9sv00001025sd00000349bc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

19: PCI 1d.2: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27ca
  Unique ID: mvRC.THjFAlec505
  SysFS ID: /devices/pci0000:00/0000:00:1d.2
  SysFS BusID: 0000:00:1d.2
  Hardware Class: usb controller
  Model: "Intel 82801G (ICH7 Family) USB UHCI Controller #3"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27ca "82801G (ICH7 Family) USB UHCI Controller #3"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0x02
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x6040-0x605f (rw)
  IRQ: 21 (2 events)
  Module Alias: "pci:v00008086d000027CAsv00001025sd00000349bc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

20: PCI 1d.3: 0c03 USB Controller (UHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27cb
  Unique ID: eEx1._hf+eJmJdO5
  SysFS ID: /devices/pci0000:00/0000:00:1d.3
  SysFS BusID: 0000:00:1d.3
  Hardware Class: usb controller
  Model: "Intel 82801G (ICH7 Family) USB UHCI Controller #4"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27cb "82801G (ICH7 Family) USB UHCI Controller #4"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0x02
  Driver: "uhci_hcd"
  Driver Modules: "uhci_hcd"
  I/O Ports: 0x6020-0x603f (rw)
  IRQ: 22 (94 events)
  Module Alias: "pci:v00008086d000027CBsv00001025sd00000349bc0Csc03i00"
  Driver Info #0:
    Driver Status: uhci-hcd is not active
    Driver Activation Cmd: "modprobe uhci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

21: PCI 1d.7: 0c03 USB Controller (EHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27cc
  Unique ID: 5YuN.+6CxPyMngcA
  SysFS ID: /devices/pci0000:00/0000:00:1d.7
  SysFS BusID: 0000:00:1d.7
  Hardware Class: usb controller
  Model: "Intel 82801G (ICH7 Family) USB2 EHCI Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27cc "82801G (ICH7 Family) USB2 EHCI Controller"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0x02
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0x58204400-0x582047ff (rw,non-prefetchable)
  IRQ: 22 (94 events)
  Module Alias: "pci:v00008086d000027CCsv00001025sd00000349bc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

22: PCI 1e.0: 0604 PCI bridge (Subtractive decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_2448
  Unique ID: 6NW+.SZEhIj3ISCE
  SysFS ID: /devices/pci0000:00/0000:00:1e.0
  SysFS BusID: 0000:00:1e.0
  Hardware Class: bridge
  Model: "Intel 82801 Mobile PCI Bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2448 "82801 Mobile PCI Bridge"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0xe2
  Module Alias: "pci:v00008086d00002448sv00001025sd00000349bc06sc04i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

23: PCI 1f.0: 0601 ISA bridge
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27bc
  Unique ID: BUZT.79IsqZc8gE8
  SysFS ID: /devices/pci0000:00/0000:00:1f.0
  SysFS BusID: 0000:00:1f.0
  Hardware Class: bridge
  Model: "Intel ISA bridge"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27bc 
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0x02
  Module Alias: "pci:v00008086d000027BCsv00001025sd00000349bc06sc01i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

24: PCI 1f.2: 0106 SATA controller (AHCI 1.0)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27c1
  Unique ID: w7Y8.D2p8kvfIMi4
  SysFS ID: /devices/pci0000:00/0000:00:1f.2
  SysFS BusID: 0000:00:1f.2
  Hardware Class: storage
  Model: "Intel 82801GR/GH (ICH7 Family) SATA AHCI Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27c1 "82801GR/GH (ICH7 Family) SATA AHCI Controller"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0x02
  Driver: "ahci"
  Driver Modules: "ahci"
  I/O Ports: 0x60b8-0x60bf (rw)
  I/O Ports: 0x60cc-0x60cf (rw)
  I/O Ports: 0x60b0-0x60b7 (rw)
  I/O Ports: 0x60c8-0x60cb (rw)
  I/O Ports: 0x60a0-0x60af (rw)
  Memory Range: 0x58204000-0x582043ff (rw,non-prefetchable)
  IRQ: 42 (128239 events)
  Module Alias: "pci:v00008086d000027C1sv00001025sd00000349bc01sc06i01"
  Driver Info #0:
    Driver Status: ahci is active
    Driver Activation Cmd: "modprobe ahci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

25: PCI 1f.3: 0c05 SMBus
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27da
  Unique ID: nS1_.lKifNMuDxy7
  SysFS ID: /devices/pci0000:00/0000:00:1f.3
  SysFS BusID: 0000:00:1f.3
  Hardware Class: unknown
  Model: "Intel 82801G (ICH7 Family) SMBus Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27da "82801G (ICH7 Family) SMBus Controller"
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0x02
  I/O Ports: 0x6000-0x601f (rw)
  IRQ: 10 (no events)
  Module Alias: "pci:v00008086d000027DAsv00001025sd00000349bc0Csc05i00"
  Driver Info #0:
    Driver Status: i2c_i801 is not active
    Driver Activation Cmd: "modprobe i2c_i801"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

26: PCI 100.0: 0200 Ethernet controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1969_2060
  Unique ID: rBUF.AfcciKaOfeA
  Parent ID: z8Q3._3VzjoUPJG5
  SysFS ID: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: network
  Model: "Attansic Ethernet controller"
  Vendor: pci 0x1969 "Attansic Technology Corp."
  Device: pci 0x2060 
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x0349 
  Revision: 0xc1
  Driver: "atl1c"
  Driver Modules: "atl1c"
  Device File: eth0
  Memory Range: 0x57000000-0x5703ffff (rw,non-prefetchable)
  I/O Ports: 0x5000-0x5fff (rw)
  IRQ: 45 (no events)
  HW Address: 1c:75:08:ba:16:6c
  Link detected: no
  Module Alias: "pci:v00001969d00002060sv00001025sd00000349bc02sc00i00"
  Driver Info #0:
    Driver Status: atl1c is active
    Driver Activation Cmd: "modprobe atl1c"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

27: PCI 200.0: 0200 Ethernet controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_14e4_4727
  Unique ID: JNkJ.QPcitGWhgh4
  Parent ID: qTvu.0vNThxjpM16
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "Broadcom Ethernet controller"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x4727 
  SubVendor: pci 0x14e4 "Broadcom"
  SubDevice: pci 0x0510 
  Revision: 0x01
  Driver: "wl"
  Driver Modules: "wl"
  Device File: eth1
  Memory Range: 0x56000000-0x56003fff (rw,non-prefetchable)
  IRQ: 17 (411132 events)
  HW Address: 88:9f:fa:1c:24:3b
  Link detected: yes
  Module Alias: "pci:v000014E4d00004727sv000014E4sd00000510bc02sc80i00"
  Driver Info #0:
    Driver Status: wl is active
    Driver Activation Cmd: "modprobe wl"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (PCI bridge)

28: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0a08
  Unique ID: z9pp.+GmdJItMGB9
  SysFS ID: /devices/pnp0/00:00
  SysFS BusID: 00:00
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0a08 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

29: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02
  Unique ID: QL3u.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:01
  SysFS BusID: 00:01
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

30: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0200
  Unique ID: tWJy.ld94kxNGZf5
  SysFS ID: /devices/pnp0/00:02
  SysFS BusID: 00:02
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0200 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

31: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0b00
  Unique ID: KiZ0.WYwRElrJa93
  SysFS ID: /devices/pnp0/00:03
  SysFS BusID: 00:03
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0b00 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

32: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0103
  Unique ID: ntp4.fG36JLVNse9
  SysFS ID: /devices/pnp0/00:04
  SysFS BusID: 00:04
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0103 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

33: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c04
  Unique ID: E349.DE8RM9cWQQ8
  SysFS ID: /devices/pnp0/00:05
  SysFS BusID: 00:05
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c04 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

34: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_INT0800
  Unique ID: hEKD.jDhFyyFrbg5
  SysFS ID: /devices/pnp0/00:06
  SysFS BusID: 00:06
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: INT 
  SubDevice: eisa 0x0800 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

35: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0303
  Unique ID: NhVi.xhndlW9HXJ7
  SysFS ID: /devices/pnp0/00:07
  SysFS BusID: 00:07
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0303 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

36: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_SYN1b1c
  Unique ID: qslm.e21BmhUQX01
  SysFS ID: /devices/pnp0/00:08
  SysFS BusID: 00:08
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: SYN 
  SubDevice: eisa 0x1b1c 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

37: IDE 00.0: 10600 Disk
  [Created at block.243]
  UDI: /org/freedesktop/Hal/devices/storage_serial_TOSHIBA_MK2565GSX_Z0A1B2BCB
  Unique ID: 3OOL.zqDXAFFi3vD
  Parent ID: w7Y8.D2p8kvfIMi4
  SysFS ID: /class/block/sda
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
  Hardware Class: disk
  Model: "TOSHIBA MK2565GS"
  Vendor: "TOSHIBA"
  Device: "MK2565GS"
  Revision: "GJ00"
  Driver: "ahci", "sd"
  Driver Modules: "ahci"
  Device File: /dev/sda
  Device Files: /dev/sda, /dev/block/8:0, /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0, /dev/disk/by-id/wwn-0x50000392f9181995
  Device Number: block 8:0-8:15
  BIOS id: 0x80
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #24 (SATA controller)

38: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_58682f5c_0155_4154_adff_b3bdd58cc626
  Unique ID: bdUI.SE1wIdpsiiC
  Parent ID: 3OOL.zqDXAFFi3vD
  SysFS ID: /class/block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda1
  Device Files: /dev/sda1, /dev/block/8:1, /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part1, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part1, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1, /dev/disk/by-uuid/58682f5c-0155-4154-adff-b3bdd58cc626, /dev/disk/by-id/wwn-0x50000392f9181995-part1, /dev/root
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #37 (Disk)

39: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_d7a9a922_eb3e_4c30_88d4_d026e9cb1c67
  Unique ID: 2pkM.SE1wIdpsiiC
  Parent ID: 3OOL.zqDXAFFi3vD
  SysFS ID: /class/block/sda/sda2
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda2
  Device Files: /dev/sda2, /dev/block/8:2, /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part2, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part2, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2, /dev/disk/by-uuid/d7a9a922-eb3e-4c30-88d4-d026e9cb1c67, /dev/disk/by-id/wwn-0x50000392f9181995-part2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #37 (Disk)

40: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_0A728F44728F340B
  Unique ID: W__Q.SE1wIdpsiiC
  Parent ID: 3OOL.zqDXAFFi3vD
  SysFS ID: /class/block/sda/sda3
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda3
  Device Files: /dev/sda3, /dev/block/8:3, /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part3, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part3, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part3, /dev/disk/by-uuid/0A728F44728F340B, /dev/disk/by-label/Acer, /dev/disk/by-id/wwn-0x50000392f9181995-part3
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #37 (Disk)

41: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_b6a0eae2_ce1c_4ce0_9831_085826248369
  Unique ID: z9FV.SE1wIdpsiiC
  Parent ID: 3OOL.zqDXAFFi3vD
  SysFS ID: /class/block/sda/sda4
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda4
  Device Files: /dev/sda4, /dev/block/8:4, /dev/disk/by-id/ata-TOSHIBA_MK2565GSX_Z0A1B2BCB-part4, /dev/disk/by-id/scsi-SATA_TOSHIBA_MK2565G_Z0A1B2BCB-part4, /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part4, /dev/disk/by-uuid/b6a0eae2-ce1c-4ce0-9831-085826248369, /dev/disk/by-id/wwn-0x50000392f9181995-part4
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #37 (Disk)

42: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7_if0
  Unique ID: k4bc.9T1GDCLyFd9
  Parent ID: 5YuN.+6CxPyMngcA
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.35-28-generic ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.35-28-generic ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1d.7"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Driver Info #0:
    Driver Status: option is not active
    Driver Activation Cmd: "modprobe option"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (USB Controller)

43: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0_if0
  Unique ID: pBe4.v+N+B0xY+P6
  Parent ID: 1GTX.RSqlCcPC2F4
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.35-28-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.35-28-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1d.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (USB Controller)

44: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1_if0
  Unique ID: uIhY.gkSaZmjGyhD
  Parent ID: vayM.ysmVhAXvZd4
  SysFS ID: /devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
  SysFS BusID: 3-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.35-28-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.35-28-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1d.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (USB Controller)

45: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_2_if0
  Unique ID: zPk0.RTX9xWW_uz4
  Parent ID: mvRC.THjFAlec505
  SysFS ID: /devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
  SysFS BusID: 4-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.35-28-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.35-28-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1d.2"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (USB Controller)

46: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3_if0
  Unique ID: 2XnU.CCckIHJirFC
  Parent ID: eEx1._hf+eJmJdO5
  SysFS ID: /devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
  SysFS BusID: 5-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.35-28-generic uhci_hcd UHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.35-28-generic uhci_hcd"
  Device: usb 0x0001 "UHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1d.3"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (USB Controller)

47: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_64e_a219_HF1315_S32B_OV01_VA_R02_01_05_if0_logicaldev_input
  Unique ID: Uc5H.sWuUzJ4g1a5
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0
  SysFS BusID: 1-4:1.0
  Hardware Class: unknown
  Model: "Suyin 1.3M WebCam"
  Hotplug: USB
  Vendor: usb 0x064e "Suyin Corp."
  Device: usb 0xa219 "1.3M WebCam"
  Revision: "2.15"
  Serial ID: "HF1315-S32B-OV01-VA-R02.01.05"
  Driver: "uvcvideo"
  Driver Modules: "uvcvideo"
  Device File: /dev/input/event5
  Device Files: /dev/input/event5, /dev/char/13:69, /dev/input/by-id/usb-Suyin_1.3M_WebCam_HF1315-S32B-OV01-VA-R02.01.05-event-if00, /dev/input/by-path/pci-0000:00:1d.7-usb-0:4:1.0-event
  Device Number: char 13:69
  Speed: 480 Mbps
  Module Alias: "usb:v064EpA219d0215dcEFdsc02dp01ic0Eisc01ip00"
  Driver Info #0:
    Driver Status: uvcvideo is active
    Driver Activation Cmd: "modprobe uvcvideo"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #42 (Hub)

49: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_cf2_6250_606569746801_if0
  Unique ID: wkjR.eexAj+JCq_E
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0
  SysFS BusID: 1-5:1.0
  Hardware Class: unknown
  Model: "ENE UB6250"
  Hotplug: USB
  Vendor: usb 0x0cf2 "ENE Technology, Inc."
  Device: usb 0x6250 "UB6250"
  Revision: "1.00"
  Serial ID: "606569746801"
  Speed: 480 Mbps
  Module Alias: "usb:v0CF2p6250d0100dc00dsc00dp00icFFisc06ip50"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #42 (Hub)

50: PS/2 00.0: 10800 Keyboard
  [Created at input.161]
  UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input
  Unique ID: c3zD.+49ps10DtUF
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: 0x0001 
  Device: 0x0001 "AT Translated Set 2 keyboard"
  Compatible to: int 0x0211 0x0001
  Device File: /dev/input/event4
  Device Files: /dev/input/event4, /dev/char/13:68, /dev/input/by-path/platform-i8042-serio-0-event-kbd
  Device Number: char 13:68
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown

51: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.183]
  UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
  Unique ID: AH6Q.ZHI3OT7LsxA
  Hardware Class: mouse
  Model: "SynPS/2 Synaptics TouchPad"
  Vendor: 0x0002 
  Device: 0x0007 "SynPS/2 Synaptics TouchPad"
  Compatible to: int 0x0210 0x0002
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event6, /dev/char/13:70, /dev/input/by-path/platform-i8042-serio-1-event-mouse, /dev/char/13:32, /dev/input/by-path/platform-i8042-serio-1-mouse, /dev/char/13:63
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 2
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

52: None 00.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 6.28.10 "Intel(R) Atom(TM) CPU N455   @ 1.66GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,mtrr,pge,mca,cmov,pat,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,nx,lm,constant_tsc,arch_perfmon,pebs,bts,aperfmperf,pni,dtes64,monitor,ds_cpl,est,tm2,ssse3,cx16,xtpr,pdcm,movbe,lahf_lm,dts
  Clock: 1666 MHz
  BogoMips: 3324.37
  Cache: 512 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

53: None 01.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: wkFv.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 6.28.10 "Intel(R) Atom(TM) CPU N455   @ 1.66GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,mtrr,pge,mca,cmov,pat,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,nx,lm,constant_tsc,arch_perfmon,pebs,bts,aperfmperf,pni,dtes64,monitor,ds_cpl,est,tm2,ssse3,cx16,xtpr,pdcm,movbe,lahf_lm,dts
  Clock: 1000 MHz
  BogoMips: 3325.08
  Cache: 512 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

54: None 00.0: 10700 Loopback
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

55: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.AfcciKaOfeA
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "atl1c"
  Driver Modules: "atl1c"
  Device File: eth0
  HW Address: 1c:75:08:ba:16:6c
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #26 (Ethernet controller)

56: None 01.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: L2Ua.ndpeucax6V1
  Parent ID: JNkJ.QPcitGWhgh4
  SysFS ID: /class/net/eth1
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "wl"
  Driver Modules: "wl"
  Device File: eth1
  HW Address: 88:9f:fa:1c:24:3b
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #27 (Ethernet controller)

57: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: sG1U.ndpeucax6V1
  SysFS ID: /class/net/vboxnet0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Device File: vboxnet0
  HW Address: 0a:00:27:00:00:00
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```
Kernel is 2.6.38
I'll try the liveusb method.

---

### Post by MoebusNet on 2011-06-04
EDIT: I found this info that applies to Mint thus Ubuntu:

[http://community.linuxmint.com/tutorial/view/309](http://community.linuxmint.com/tutorial/view/309)

Since this has more to do with Ubuntu, I'll put it first. I'll leave the rest for reference.

If you need to stay with your current version of Ubuntu, there is a patch that gets the  EME card reader on my Acer AAO D255-2301 working under Puppy Linux, also. Running Puppy Linux 5.25, there is a pet package:

(keucr_2.6.33.2-lupu525.pet)

that gets it working on the older kernel in Lucid Puppy 5.25 (based on Lucid Lynx).

Dawnboy compiled the package, he might be able to help out. The discussion thread is at:

[http://www.murga-linux.com/puppy/viewtopic.php?t=65929&start=29](http://www.murga-linux.com/puppy/viewtopic.php?t=65929&start=29)

So anyway my card reader works in Natty narwhal & Lucid Puppy 5.25 now! :)

---

