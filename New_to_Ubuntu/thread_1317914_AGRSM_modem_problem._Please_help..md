---
title: "AGRSM modem problem. Please help."
date: 2009-11-07
forum: New to Ubuntu
---

### Post by Epiclow on 2009-11-07
Hello, this is my first time on these forums. I need some help badly!
 
I have Ubuntu 8.04, I updated the kernel to 2.6.24.19.
 
I want to get my Agere Systems Soft Modem installed, I already ran scanModem and found out I can get a agrsm drivers for it.
 
Now heres where my problem kicks in:
 
I downloaded agrsm-ubuntu8.04.1-2.6.24-19-generic.tar.gz, as thats for my kernel.
I unzipped it, went to the directory and ran "sudo ./setup" and a lot of errors popped up. I have a .txt file attached below of the output I got when I ran it.
 
Also when I ran "sudo modprobe agrmodem" it said "FATAL: Error inserting agrmodem (/lib/modules/2.6.24-19-generic/extra/agrmodem.ko): Unknown symbol in module, or unknown parameter (see dmesg)".
 
And on top of that the setup couldn't get into the root directory to backup the files, AND the setup couldn't install the serial driver snd-hda-intel.ko.
 
This is what it said when it tried to install snd-hda-intel.ko "ls: cannot access /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko: No such file or directory".
 
I checked to try to find the directory and there is no "ubuntu" directory.
I only got as far as "/lib/modules/2.6.24-19-generic/. There was NO ubuntu directory.
 
This is what it said about the root directory: Saving existing driver to /root/
cp: missing destination file operand after `/root/'
Try `cp --help' for more information.
Copying snd-hda-intel.ko to
cp: missing destination file operand after `snd-hda-intel.ko'
Try `cp --help' for more information.
chown: missing operand after `root:root'
Try `chown --help' for more information.
 
Did I install the wrong kernel update or something?
Please help as this is driving me up the wall.
 
If you need to see the ModemData.txt file for any reason then tell me.
 
EDIT: If this is in the wrong place then can a mod or admin move it?

---

### Post by lkraemer on 2009-11-07
You're best bet is to contact the folks at linmodems.org and let
Marvin and those folks help you with those questions.

But, why spend 3 to 7 days fiddling with that when you can buy a
good external Hardware US Robotics modem and be online in 30 minutes.
Search on ebay for a used Hardware Modem.

lk

---

### Post by Epiclow on 2009-11-08
> **lkraemer said:**
> You're best bet is to contact the folks at linmodems.org and let
Marvin and those folks help you with those questions.
 
But, why spend 3 to 7 days fiddling with that when you can buy a
good external Hardware US Robotics modem and be online in 30 minutes.
Search on ebay for a used Hardware Modem.
 
lk
 
I would buy one in a heartbeat, but I don't have any money to get one with after I quit Walmart.
 
Thanks anyway, I'll see if I can get in touch with them.

---

