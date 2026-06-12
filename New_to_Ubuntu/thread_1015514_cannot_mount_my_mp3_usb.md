---
title: "cannot mount my mp3 usb"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by smj0804 on 2008-12-18
heyy
ive got ubuntu very recently
so im very new to the way linux works...
its so COMPLICATED D:
im trying to mount my mp3 file
ive been doing some research to find the problem
but i dont get it...
i saw codes and others butl idontknow even know
where to put those

after i plug in my usb and i try to mount it
it says that file cannot be mounted
helpp.............D:
...
p.s. im a beginner
the veryvery beginnerrrr D: helpppel;easeeee

---

### Post by bumanie on 2008-12-18
Plug the player back into windows and make sure you 'safely remove' the device. Ubuntu should automount such a device, but if it has not been correctly removed from windows, ubuntu sees the filesystem as still in use and won't mount it. If that doesn't work post back with any errors you are getting.

---

### Post by smj0804 on 2008-12-20
well..
how can i remove it safely..?
when i right-click on the usb file
there's no eject
or anything like that....

---

### Post by StevenHarper on 2008-12-20
ok could you open the main system log **Before** you plug in the player.

Then post the results here.

To do this:

Click 
Applications
Accessories
Terminal

make the window big (full screen)

Enter
```
tail -f /var/log/syslog
```

After you have plug-ed in the player, use CTRL+C to stop the window scrolling, then cut an paste the log lines here.

---

### Post by smj0804 on 2008-12-22
well at first i typeed in the code before i plugged the sub in
and i got
Dec 22 23:04:32 yeonju-desktop kernel: [29591.802368] sdb: rw=0, want=4294967292, limit=7503872
Dec 22 23:04:32 yeonju-desktop kernel: [29591.802377] attempt to access beyond end of device
Dec 22 23:04:32 yeonju-desktop kernel: [29591.802380] sdb: rw=0, want=4294967292, limit=7503872
Dec 22 23:05:20 yeonju-desktop kernel: [29639.925056] usb 8-3: USB disconnect, address 2
Dec 22 23:05:20 yeonju-desktop NetworkManager: <debug> [1230005120.399979] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_327_BEBA35563299_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Dec 22 23:05:20 yeonju-desktop NetworkManager: <debug> [1230005120.408562] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Sony_WALKMAN_BEBA35563299'). 
Dec 22 23:05:20 yeonju-desktop NetworkManager: <debug> [1230005120.419744] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_327_BEBA35563299_if0_scsi_host_scsi_device_lun0'). 
Dec 22 23:05:20 yeonju-desktop NetworkManager: <debug> [1230005120.419847] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_327_BEBA35563299_if0_scsi_host'). 
Dec 22 23:05:20 yeonju-desktop NetworkManager: <debug> [1230005120.429218] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_327_BEBA35563299_if0'). 
Dec 22 23:05:20 yeonju-desktop NetworkManager: <debug> [1230005120.429299] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_327_BEBA35563299'). 
Dec 22 23:06:38 yeonju-desktop kernel: [29717.929358] usb 8-3: new high speed USB device using ehci_hcd and address 3
Dec 22 23:06:38 yeonju-desktop kernel: [29718.062463] usb 8-3: configuration #1 chosen from 1 choice
Dec 22 23:06:38 yeonju-desktop kernel: [29718.063066] scsi5 : SCSI emulation for USB Mass Storage devices
Dec 22 23:06:38 yeonju-desktop kernel: [29718.063492] usb-storage: device found at 3
Dec 22 23:06:38 yeonju-desktop kernel: [29718.063498] usb-storage: waiting for device to settle before scanning
Dec 22 23:06:38 yeonju-desktop NetworkManager: <debug> [1230005198.644853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_327_BEBA35563299'). 
Dec 22 23:06:38 yeonju-desktop NetworkManager: <debug> [1230005198.700434] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_54c_327_BEBA35563299_if0'). 


after i plugged it in ive gt Dec 22 23:06:44 yeonju-desktop kernel: [29724.256286] sdb: rw=0, want=4294967232, limit=7503872
Dec 22 23:06:44 yeonju-desktop kernel: [29724.256291] attempt to access beyond end of device
Dec 22 23:06:44 yeonju-desktop kernel: [29724.256292] sdb: rw=0, want=4294967284, limit=7503872
Dec 22 23:06:44 yeonju-desktop kernel: [29724.256294] attempt to access beyond end of device
Dec 22 23:06:44 yeonju-desktop kernel: [29724.256296] sdb: rw=0, want=4294967288, limit=7503872
Dec 22 23:06:44 yeonju-desktop kernel: [29724.256301] attempt to access beyond end of device
Dec 22 23:06:44 yeonju-desktop kernel: [29724.256302] sdb: rw=0, want=4294967292, limit=7503872
Dec 22 23:06:44 yeonju-desktop kernel: [29724.256307] attempt to access beyond end of device
Dec 22 23:06:44 yeonju-desktop kernel: [29724.256308] sdb: rw=0, want=4294967292, limit=7503872
Dec 22 23:06:44 yeonju-desktop NetworkManager: <debug> [1230005204.844894] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Sony_WALKMAN_BEBA35563299'). 
Dec 22 23:07:18 yeonju-desktop ntfs-3g[7587]: Version 1.2216 external FUSE 27 
Dec 22 23:07:18 yeonju-desktop ntfs-3g[7587]: Mounted /dev/sda1 (Read-Write, label "", NTFS 3.1) 
Dec 22 23:07:18 yeonju-desktop ntfs-3g[7587]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=ko_KR.UTF-8 
Dec 22 23:07:18 yeonju-desktop ntfs-3g[7587]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,noatime,fsname=/dev/sda1,blkdev,blksize=4096 
Dec 22 23:07:18 yeonju-desktop hald: mounted /dev/sda1 on behalf of uid 1000
...........
i tried to mount the file but...i still dont get it...sorry D:

---

### Post by StevenHarper on 2008-12-28
From the log we can see that the NTFS partition has been mounted by the HALD.  The device shows up as

```
/dev/sda1
```

Now if you run the command (in a terminal)

```
df -k
```

You will see all the mounts in your system

one should be something like

```
/dev/sda1        12331223  2132321  12321321  50%   /media/disk
```

the last column is where the disk was mounted

Open a file manager and browse to that location.

If your disk isn't in the df -k list, then you can try this to force mount it

First make a directory to mount the player at

```
sudo mkdir /media/player
```

Then lets mount it

```
sudo mount /dev/sda1 /media/player
```

to unmount

```
umount /media/player
```

hope this helps

---

