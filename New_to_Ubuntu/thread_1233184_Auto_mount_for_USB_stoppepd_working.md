---
title: "Auto mount for USB stoppepd working"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-08-06
I'm using Hardy 8.04.

When I plug in a USB device, e.g. my external hard drive or my flash drive, the computer used to automatically recognise it and mount it.

However, it's stopped doing that. I can still mount them manually (sudo mount /dev/sdb1 /media/whatever), so there's no problem with the USB ports or devices. The computer just won't automatically mount.

I'm not aware of having done anything to cause this. Recently, I moved and resized the partitions using gparted; could that have caused the problem?

How can I solve this?

---

### Post by harry2006 on 2009-08-06
> **Paddy Landau said:**
> I'm using Hardy 8.04.

When I plug in a USB device, e.g. my external hard drive or my flash drive, the computer used to automatically recognise it and mount it.

However, it's stopped doing that. I can still mount them manually (sudo mount /dev/sdb1 /media/whatever), so there's no problem with the USB ports or devices. The computer just won't automatically mount.

I'm not aware of having done anything to cause this. Recently, I moved and resized the partitions using gparted; could that have caused the problem?

How can I solve this?
seems some issue with your udev rules for auto mounting the mentioned device. you might need to re-check the same. 
as you mentioned that the device can be mounted manually with ease and witout any issues, i guess udev rules has some issues...
btw, when you plug your device what msg you get from kernel i.e what is the outut of 
     dmesg |tail 
command?

---

### Post by ptn107 on 2009-08-06
Open Nautilus (Places -> Home Folder).  Click Edit -> Preferences -> and the Media tab.  At the bottom verify 'Browse media when inserted' is checked and that 'Never prompt or start programs on media insertion' is NOT checked.

---

### Post by Paddy Landau on 2009-08-06
> **ptn107 said:**
> ... verify 'Browse media when inserted' is checked and that 'Never prompt or start programs on media insertion' is NOT checked.
They were already as you describe.

---

### Post by Paddy Landau on 2009-08-06
> **harry2006 said:**
> what is the outut of dmesg |tail
```
[  143.991300] usb 5-1: new high speed USB device using ehci_hcd and address 5
[  144.143962] usb 5-1: configuration #1 chosen from 1 choice
[  144.145167] scsi3 : SCSI emulation for USB Mass Storage devices
[  144.145661] usb-storage: device found at 5
[  144.145667] usb-storage: waiting for device to settle before scanning
[  144.492464] usb-storage: device scan complete
[  144.498282] scsi 3:0:0:0: Direct-Access     TOSHIBA  USB 2.5"-HDD     100  PQ: 0 ANSI: 2
[  144.501076] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  144.503704] sd 3:0:0:0: [sdb] Write Protect is off
[  144.503714] sd 3:0:0:0: [sdb] Mode Sense: 38 00 00 00
[  144.503720] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  144.505696] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  144.508318] sd 3:0:0:0: [sdb] Write Protect is off
[  144.508327] sd 3:0:0:0: [sdb] Mode Sense: 38 00 00 00
[  144.508332] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  144.509065]  sdb: sdb1 sdb2
[  144.972123] sd 3:0:0:0: [sdb] Attached SCSI disk
[  144.972224] sd 3:0:0:0: Attached scsi generic sg2 type 0
```> **harry2006 said:**
> seems some issue with your udev rules for auto mounting the mentioned device. you might need to re-check the same.
I'll try to figure this out, but I definitely haven't changed any of these.

---

### Post by Paddy Landau on 2009-08-06
In the previous post, I should have mentioned that it was a USB hard drive with two partitions.

Here are the results for a USB flash drive with just the normal single FAT32 partition.
```
[  189.526914] usb 5-2: new high speed USB device using ehci_hcd and address 6
[  189.662251] usb 5-2: configuration #1 chosen from 1 choice
[  189.662922] scsi4 : SCSI emulation for USB Mass Storage devices
[  189.663420] usb-storage: device found at 6
[  189.663428] usb-storage: waiting for device to settle before scanning
[  189.930247] usb-storage: device scan complete
[  189.931420] scsi 4:0:0:0: Direct-Access     Ut163    USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[  189.941851] sd 4:0:0:0: [sdc] 1974271 512-byte hardware sectors (1011 MB)
[  189.942826] sd 4:0:0:0: [sdc] Write Protect is off
[  189.942829] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
[  189.942831] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  189.945809] sd 4:0:0:0: [sdc] 1974271 512-byte hardware sectors (1011 MB)
[  189.946698] sd 4:0:0:0: [sdc] Write Protect is off
[  189.946701] sd 4:0:0:0: [sdc] Mode Sense: 00 00 00 00
[  189.946703] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  189.946707]  sdc: sdc1
[  190.063356] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[  190.063408] sd 4:0:0:0: Attached scsi generic sg3 type 0
```

---

### Post by Paddy Landau on 2009-08-06
-> **harry2006 said:**
> seems some issue with your udev rules for auto mounting the mentioned device.
I found something in udev. I have no clue how important it is though...

Looking in /etc/udev/rules.d, I see one file modified since 2008 (the ctime indicates 2009-08-02, and the mtime 2009-07-12. The problem started less than a week ago).

  The file has the name 70-persistent-cd.rules.

I wonder whether it has anything to do with my Palm, as I recently got it to synchronize with Evolution (so that I could finally get rid of Windows). I didn't go to change anything in udev, however; I just used the built-in gnome-applet.

I've attached the file in case there's anything of significance. (I added .txt to the name, as the forum wouldn't allow me to load it otherwise.)

---

### Post by cwmoser on 2009-08-06
FYI, there were some **USB issues **with 8.04 - that was the primary reason I went with Jaunty.

But, I have observed with 9.04 Jaunty 64-bit, occassionally USB devices will not auto mount nor can I use the dmesg command to discern the device to mount.  I did find that a reboot will make things work normally.

Carl

---

### Post by wizard10000 on 2009-08-06
> **cwmoser said:**
> FYI, there were some **USB issues **with 8.04 - that was the primary reason I went with Jaunty.

But, I have observed with 9.04 Jaunty 64-bit, occassionally USB devices will not auto mount nor can I use the dmesg command to discern the device to mount.  I did find that a reboot will make things work normally.

What I did was change policykit to enable any console (not just the active one) to mount removable media - that solved it for me.

---

### Post by Paddy Landau on 2009-08-06
> **cwmoser said:**
> FYI, there were some **USB issues **with 8.04 - that was the primary reason I went with Jaunty.
And yet it has worked perfectly for me until a few days ago. I must have done something wrong; if only I knew what!

---

### Post by Paddy Landau on 2009-08-06
> **wizard10000 said:**
> What I did was change policykit to enable any console (not just the active one) to mount removable media - that solved it for me.
What's a policykit and how do I change it?

---

### Post by wizard10000 on 2009-08-06
System --> Administration --> Authorizations

Find the setting that allows you to mount removable media and set 'console' to yes.  Sorry, I'm on a Windows box right now or I could tell you exactly what it said.

---

### Post by Paddy Landau on 2009-08-06
> **wizard10000 said:**
> System --> Administration --> Authorizations

Find the setting that allows you to mount removable media and set 'console' to yes.  Sorry, I'm on a Windows box right now or I could tell you exactly what it said.
Thanks, I couldn't figure it out with the search engines.

This is what I did:

[LIST]
[*]System > Administration > Authorizations > org > freedesktop > hal > storage > Mount file systems from removable drives.
[*]The settings were "*Anyone:* No. *Console:* No. *Active Console:* Yes"
[*]I changed this to "*Anyone:* No. *Console:* Yes. *Active Console:* Yes"
[/LIST]
Sadly, I still have the problem. I tried rebooting in case that was necessary (Windows-think, yes?) and of course that made no difference.

---

### Post by Paddy Landau on 2009-08-07
Solved!

But...

Why?

I've solved this, and I know how, but I have no idea why!

On a hunch, I changed my /etc/fstab and this solved the problem.

Take a look at the two attached fstabs below. The only difference is that the old fstab used UUID to find the partitions, whereas the new fstab uses the device names.

For some reason, the old fstab prevented automatic mounting, whereas the new one allows it.

Can anyone explain the reason to me?

**Old fstab:**
```
proc                                      /proc         proc        defaults                    0 0
# The root partition:
UUID=2720857a-7ee9-4beb-ad09-fec472fe5e7c /             ext3        relatime,errors=remount-ro  0 1
# The /home partition:
UUID=3febb30c-9bd2-45c9-b783-9425fd03984e /home         ext3        relatime,errors=remount-ro  0 2
# The swap partition:
UUID=1d998dca-fb63-46c1-9219-3c02d315f0a0 none          swap        sw                          0 0
/dev/scd0                                 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8       0 0
LABEL=paddy1                              /media/paddy1 ext3        user,dev,exec,suid,relatime 0 0
```**New fstab:**
```
proc                                      /proc         proc        defaults                    0 0
# The /home partition:
/dev/sda3                                 /             ext3        relatime,errors=remount-ro  0 1
# The /home partition:
/dev/sda5                                 /home         ext3        relatime,errors=remount-ro  0 2
# The swap partition:
/dev/sda6                                 none          swap        sw                          0 0
/dev/scd0                                 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8       0 0
LABEL=paddy1                              /media/paddy1 ext3        user,dev,exec,suid,relatime 0 0
```

---

