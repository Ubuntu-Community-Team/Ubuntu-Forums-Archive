---
title: "WIndows usb formatting problem"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-11-16
Im currently aqt college, and because all us young adults are "hackers" in the eyes of the IT dept. we have basic rights on the network. now i want to format my usb stick (because i want to fsck my netbook and ubuntu doesnt pick up my usb) to fat32 but i dont have the rights to do it. is there a way i can do it via the command prompt? as i have access to that (which is kinda wierd...right?)

---

### Post by my_key on 2009-11-16
You can try this: [http://ss64.com/nt/format.html](http://ss64.com/nt/format.html)

---

### Post by JamesParnell on 2009-11-16
could you give me a brief intro on the syntax, im still new with the terminal/command prompt side of things

---

### Post by JamesParnell on 2009-11-16
also, when i open the CMD, it points me straight to the H drive. which is one of the many network drives.

---

### Post by ukripper on 2009-11-16
Can you connect your usb to your ubuntu running notebook and run folowing commands and post output here:
```
sudo fdisk -l
```
```
sudo mount
```

this will give details about your usb

---

### Post by JamesParnell on 2009-11-16
if i connect it form boot ( i set it to boot form the usb first) it says missing OS (not bothered) then lopads grub and boots into 9.10, then for a few minutes the USB (named "stick) appears on the DT for about 2minutes, but when i try to format it, it vanishes, notmatter how many times i reconnect it,m it still doesnt read

---

### Post by JamesParnell on 2009-11-16
results of "sudo fdisk -l"
 
**Device Boot**
/dev/sda1 *
_/dev/sda2_
_^^^ (music parition)_
stick not read
results of sudo mount:
 
/dev/sda1 on / **ext4**
proc on /proc
none on /sys
none on /sys/fs/fuse
none on /sys/kernel/debug
...you get the idea
/dev/sda2 on /mnt/music **ext4**
binfmt_misc on /proc/sys/fs/binfnt_misc
gvfs-fuse-daemon on /home/james/.gvfs
 
 
**EDIT:**
 
this is form a post i made about the actual problem (ubuntu not liking the stick) before..here are the results of a log someone asked for, cant remember what log, i think  it was dmesg.
 
```
[ 2931.789867] ath5k phy0: unsupported jumbo
[ 3913.564070] usb 1-6: new high speed USB device using ehci_hcd and address 15
[ 3913.697236] usb 1-6: configuration #1 chosen from 1 choice
[ 3913.708552] scsi5 : SCSI emulation for USB Mass Storage devices
[ 3913.717704] usb-storage: device found at 15
[ 3913.717720] usb-storage: waiting for device to settle before scanning
[ 3928.716306] usb-storage: device scan complete
[ 3950.100070] usb 1-6: reset high speed USB device using ehci_hcd and address 15
[ 3955.224082] usb 1-6: device descriptor read/64, error -71
[ 3960.448064] usb 1-6: device descriptor read/64, error -71
[ 3960.664065] usb 1-6: reset high speed USB device using ehci_hcd and address 15
[ 3965.784063] usb 1-6: device descriptor read/64, error -71
[ 3971.008075] usb 1-6: device descriptor read/64, error -71
[ 3971.224068] usb 1-6: reset high speed USB device using ehci_hcd and address 15
[ 3976.636057] usb 1-6: device not accepting address 15, error -71
[ 3976.748076] usb 1-6: reset high speed USB device using ehci_hcd and address 15
```

---

### Post by ukripper on 2009-11-16
and output of below:
```
lsusb -v
```

---

### Post by JamesParnell on 2009-11-16
turned the thing off now, give me a minute, ah, this output is huge, after i finish here in 1/4 hour, ill leg it down to the library and post the output for you. sorry for the abbreviations, im actually on a windows machine because the netbook cant get the wifi access (i think they finally blocked me from the wifi that i shoulnt of been able to get on in the first place)

---

### Post by ukripper on 2009-11-16
> **JamesParnell said:**
> turned the thing off now, give me a minute, ah, this output is huge, after i finish here in 1/4 hour, ill leg it down to the library and post the output for you. sorry for the abbreviations, im actually on a windows machine because the netbook cant get the wifi access (i think they finally blocked me from the wifi that i shoulnt of been able to get on in the first place)

Leave the post for lsusb -v, looks like lsusb showed the error i was looking for.

---

### Post by ukripper on 2009-11-16
can you post the output of below command to see what kernel you are using:
```
uname -a
```

---

### Post by JamesParnell on 2009-11-16
aah ok. well in 15minutes hopefully i should be online in the library, so i will be able to try any fixes you may suggest.

---

### Post by JamesParnell on 2009-11-16
its 2.6.31.14-generic. i memorised it i post it that often
 
i upgraded to 15 (somehow) and my fn brightness keys stopped working, it was only after i reverted back to 14 that they wqorked again. my kernel shouldnt be the problem, as it was working before...*shrugs*. but then again, you know more than me.

---

### Post by ukripper on 2009-11-16
can you unplug all the usb devices you may have connected to your notebook and afterwards just plug this usb drive. then post the output of the below command;
```
lsusb
```

---

### Post by JamesParnell on 2009-11-16
Bus 001 Device 004: ID 1e3d:8246  
Bus 001 Device 003: ID 0ac8:c326 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



all the others are inbuilt, but i swear the top one is the usb

---

### Post by ukripper on 2009-11-16
> **JamesParnell said:**
> Bus 001 Device 004: ID 1e3d:8246  
Bus 001 Device 003: ID 0ac8:c326 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



all the others are inbuilt, but i swear the top one is the usb

yeh Z-star seems to be your webcam.and the top device seems to be your usb drive but not getting recognised.

Can you post output of this:
```
sudo fdisk -l
```

---

