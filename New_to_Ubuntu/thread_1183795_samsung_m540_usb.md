---
title: "samsung m540 usb"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by sandyd on 2009-06-10
i seem to be having a problem with the mass storage thingy. it connects to the computer in serial mode, but not in mass storage mode

---

### Post by diablozx9 on 2009-06-26
bump.. just bought one

---

### Post by diablozx9 on 2009-08-14
Anyone know how to get Ubuntu to connect to Samsung M540 phone ?

---

### Post by sandyd on 2009-08-14
i gave up... and bought a bluetooth dongle. pretty useful b/c/ i have an app that automatically locks my computer once the bluetooth signal from my phone isn't detected :D

---

### Post by diablozx9 on 2009-09-08
I also bought a dongle.
I didn't find it easy to connect.
Also, I still haven't been able to transfer files.
Am I slow ?
Help?

---

### Post by sandyd on 2009-09-23
for those having the same problem, i found something that completely fixed the problem

[http://ubuntuforums.org/archive/index.php/t-1145846.html](http://ubuntuforums.org/archive/index.php/t-1145846.html)

add
```

usb-storage option_zero_cd=2 

```
to /etc/modules

also applies to other quallcom based chipset phones that don't connect.

---

### Post by sandyd on 2009-09-23
except that this creates a problem. if you have a USB printer, don't expect it to work.


help?

EDIT: i mean, don't expect the USB printer to work.

---

### Post by 3rdalbum on 2009-09-24
All I can suggest is the fix for certain Sony Walkmans that get improperly mounted as MTP.

Plug in the device, run the command:

```
killall gvfs-gphoto2-volume-monitor
```

Unmount the device if possible, unplug it, and plug it back in again.

---

### Post by kameron on 2009-10-13
adding
```
usb-storage option_zero_cd=2
```

to /etc/modules worked for me in jaunty. now i upgraded to karmic and it's no longer working for me. the /etc/modules file was completely empty before i added that line, with the upgrade it now lists "sbp2" and "lp". i tried commenting both of those out, reboot and try. no luck. left them in then i commented out the "usb-storeage.." line, rebooted, no luck.

is anyone having their m540 connect properly with the new release? thanks :)

---

### Post by Epidural on 2009-10-22
Using 9.04 Jaunty with a Samsung "Slyde" (m540). Adding```
usb-storage option_zero_cd=2
```to the /etc/modules file worked great. A reboot and using the "Tools->Mass Storage->Connect To PC" on the phone showed my MicroSD 2GB as a mass storage on Ubuntu. (PS: Koodo phone, so it's not locked down by Telus. Not sure if that would make any difference.)

---

### Post by alphalux on 2009-11-03
kameron, 

I am also having the same problem after upgrading to karmic. Previously, I used the same solution you mentioned on Jaunty, and it worked perfectly. I'm still poking around for an answer. Perhaps someone can shed some light.

---

### Post by kameron on 2009-12-28
bump?...

---

### Post by lucid_suren on 2010-06-18
Hi

Running Lucid, having the same problem. Editing /etc/modules did nothing, and only lp showed as a line in that file. 

Is there any other way to get this to work? 

Thanks.

---

### Post by alphalux on 2010-06-24
lucid_suren, see the bug listing here and pay attention to comment #9. This worked for me. [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/477031](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/477031)

---

### Post by tjwilli on 2010-07-01
> **alphalux said:**
> lucid_suren, see the bug listing here and pay attention to comment #9. This worked for me. [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/477031](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/477031)
I had this problem after upgrading from 9.04 to 9.1 with my LG CU920. The suggestion works for me too. Thanks!

---

