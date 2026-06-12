---
title: "external HD won't mount"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-11-23
Hi Ubuntu Community:

:P

My son has a nice WD external hard disk that mounts with with his Windows 7 laptop. You can see the files, and folders.

However, when I connect it to my Ubuntu machine, it does not mount.

What should I do to make the external drive mount and let me read the files on it?

:D

Thanks!
Phil Smith
Duluth, GA

---

### Post by surfer on 2010-11-23
check what /var/log/messages says when you plug in the device. i.e open a shell, type
```
$ tail -f /var/log/messages
```
and plug in the drive.

---

### Post by CharlesA on 2010-11-23
You'd probably have to run chkdisk on the Windows box before you are able to mount the drive. NTFS on linux is tricky sometimes.

---

### Post by Old Jimma on 2010-11-23
Hi Surfer:

Here is the tail:

Phil



philipsmith@philipsmith-desktop:~$ tail -f /var/log/messages
Nov 23 09:59:22 philipsmith-desktop kernel: [401535.514085] scsi9 : SCSI emulation for USB Mass Storage devices
Nov 23 09:59:27 philipsmith-desktop kernel: [401540.532046] scsi 9:0:0:0: Direct-Access     WD       2500BEV External 1.75 PQ: 0 ANSI: 4
Nov 23 09:59:27 philipsmith-desktop kernel: [401540.534473] sd 9:0:0:0: Attached scsi generic sg3 type 0
Nov 23 09:59:27 philipsmith-desktop kernel: [401540.535157] sd 9:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Nov 23 09:59:27 philipsmith-desktop kernel: [401540.535906] sd 9:0:0:0: [sdc] Write Protect is off
Nov 23 09:59:27 philipsmith-desktop kernel: [401540.546930]  sdc: sdc1
Nov 23 09:59:27 philipsmith-desktop kernel: [401540.596929] sd 9:0:0:0: [sdc] Attached SCSI disk
Nov 23 10:01:23 philipsmith-desktop kernel: [401656.282640] usb 1-9: USB disconnect, address 18
Nov 23 11:41:44 philipsmith-desktop kernel: [407677.302812] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
Nov 23 11:42:17 philipsmith-desktop kernel: [407711.039923] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)

---

### Post by amjjawad on 2010-11-23
Before you unplug it from Windows, make sure to click "Safely remove" not just unplug it. Hope that would help :)

---

### Post by CharlesA on 2010-11-23
The dmesg looks fine outside of the disconnect message.

What is the error you were getting when trying to mount the drive?

---

### Post by Jetso on 2010-11-23
You probably tried this but, it looks like this could do something:
```
sudo mount /dev/sdc1 /media/<What ever the name is of the hard drive.> 
```Just replace <> With what it says... Hopefully it will work!

---

### Post by wilee-nilee on 2010-11-23
> **CharlesA said:**
> You'd probably have to run chkdisk on the Windows box before you are able to mount the drive. NTFS on linux is tricky sometimes.

+1 just noticed the signature, some times it is a light dope tap, sometimes it is the adz eh.;)

---

### Post by CharlesA on 2010-11-23
> **wilee-nilee said:**
> +1 just noticed the signature, some times it is a light dope tap, sometimes it is the adz eh.;)

That actually made me lol. ;)

As for the problem, the exact error message would help greatly, but I figured it's probably unable to mount it because the drive is "locked" due to an "unsafe" disconnect.

---

### Post by wilee-nilee on 2010-11-23
> **CharlesA said:**
> That actually made me lol. ;)

As for the problem, the exact error message would help greatly, but I figured it's probably unable to mount it because the drive is "locked" due to an "unsafe" disconnect.

Hey your a mod and I think I have had the pleasure without looking of that dope tap from you and others, well deserved "I must say" ed grimely ;) Actually from a few forum members as well, all were helpful.

---

