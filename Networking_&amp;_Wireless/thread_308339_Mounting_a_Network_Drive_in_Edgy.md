---
title: "Mounting a Network Drive in Edgy"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by theh3brewhammer on 2006-11-27
I tried following [this guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite") to mount an NTFS network drive at boot up. But I get the following error when I try to remount:
```

mount: wrong fs type, bad option, bad superblock on //192.168.0.110/E$/,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Thanks a lot for the help.

---

### Post by koenn on 2006-11-28
> mount: wrong fs type, bad option, bad superblock on //192.168.0.110/E$/,
- how did you mount it ?
-what is the output of ```
dmesg | tail 
```

---

### Post by theh3brewhammer on 2006-11-28
The output of "dmesg | tail":
```

[17187484.392000] usb 4-1: new high speed USB device using ehci_hcd and address 6
[17187484.524000] usb 4-1: configuration #1 chosen from 1 choice
[17187484.524000] hub 4-1:1.0: USB hub found
[17187484.528000] hub 4-1:1.0: 4 ports detected
[17188036.548000] usb 4-1: USB disconnect, address 6
[17189089.428000] usb 4-1: new high speed USB device using ehci_hcd and address 7
[17189089.560000] usb 4-1: configuration #1 chosen from 1 choice
[17189089.564000] hub 4-1:1.0: USB hub found
[17189089.564000] hub 4-1:1.0: 4 ports detected
[17189144.892000] smbfs: mount_data version 1684370019 is not supported

```

I'm using "sudo mount -a" to mount, a reboot doesn't work either.  The line in /etc/fstab is:
```

//192.168.0.110/E$    /media/Hammer smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

```

---

### Post by phazon. on 2006-11-29
I've basically got the same issue, see [this]("http://www.ubuntuforums.org/showthread.php?t=298313") thread.

This is my dmesg output;

>  [17282330.728000] smbfs: mount_data version 1936029031 is not supported

Pretty similar, an

---

### Post by santo on 2006-11-29
Before you can use smbfs, you should install the smbfs package which isn't installed by default.

```

sudo aptitude install smbfs

```

I admit the error message you get isn't poiting in that direction :( 
They could make it a bit more user friendly in my opinion

---

### Post by theh3brewhammer on 2006-12-05
I'm really sorry I didn't say thanks sooner santo, but that fixed the problem completely, now I'm having trouble [writing]("http://ubuntuforums.org/showthread.php?t=313365") but at least it's mounted.

---

### Post by santo on 2006-12-06
I'm glad i can help somebody :)

For the writing permissions:
Try changing the permissions of the folder before mounting.
In your case that would be:
```

sudo umount /media/Hammer
sudo chmod a+w /media/Hammer
sudo mount /media/Hammer

```

That should solve it.

---

### Post by theh3brewhammer on 2006-12-06
Yep, that worked, thanks again.

---

