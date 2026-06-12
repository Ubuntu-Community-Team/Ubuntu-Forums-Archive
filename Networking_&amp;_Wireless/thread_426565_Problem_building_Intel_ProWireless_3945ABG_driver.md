---
title: "Problem building Intel Pro/Wireless 3945ABG driver"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by Chalain on 2007-04-28
After much googling about the Intel Pro/Wireless 3945ABG adapter in my laptop, It looks like I may have to rebuild the kernel. The Ubuntu pages on rebuilding the kernel are quite clear about my not wanting to ever do this. A friend pointed me to a set of stable drivers direct from Intel, and after studying them it looked like they would install without a kernel rebuild. Yay!

This turns out not to be the case.

I did a make && make install of ieee80211-1.2.17 from Intel, and told it to go ahead and remove conflicting files. When I attempted to make the ipw3945-1.2.0 driver, make failed with this error:
```

/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.


-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
```

So, if I'm reading this right, I need to either rebuild the kernel or undo the damage I did to the existing wireless subsystem.

I don't know how to do either. Which do I want, and how do I do it?

EDIT: I forgot to mention: Kubuntu 7.04 Feisty Fawn, on a HP Pavilion dv8333cl laptop.

---

### Post by chili555 on 2007-04-28
I wonder why the driver and firmware built in to the the Feisty restricted modules isn't working for you? For most of us 3945 zombies, it works perfectly.

---

### Post by Chalain on 2007-04-28
I may honestly have been too dumb. It may have been working, and I just couldn't get it TO work.

So.... ::innocent whistle:: how do I restore the old ieee802.11 modules....?

---

### Post by chili555 on 2007-04-28
There may be more elegant ways to do it, but here's my suggestion:
#Reboot computer
#As it's booting, press ESC and select a previous kernel. For example, the top listing may be 2.6.20-14.23 and the next one down may be 2.6.20-14.12. Select .12.
#Go into Synaptic and right-click, mark for reinstall linux-image-generic, select the .23 version. Do the same with linux-restricted-modules and, for good measure, linux-headers.
#Reboot. You are now fixed up like new.

Then, do iwconfig and you should see eth1 ready to go. On my laptop, connecting was as simple as:```
sudo iwconfig eth1 essid myrouter
sudo iwconfig eth1 key 0123456789
sudo dhclient eth1
``` Good luck and post back if you get stuck.

---

### Post by Chalain on 2007-04-28
WONDERFUL!

I installed new from a 7.04 Feisty Fawn CD, but I was able reboot into the recovery mode kernel. Aptitude let me reinstall the kernel image and the file dates on the 802.11 files are now reset to 4/15.

I am posting this from my wireless connection. In other words, it worked.

I realize we need to let the thread die but I wanted to post back the hinky bit about using the recovery kernel. But since I'm posting anyway...

THANK YOU!

---

### Post by atd85 on 2007-04-30
i'm running 6.10 edgy and my drivers were working, but i thought it'd be a good idea to try to upgrade... well i got the same exact error as the original poster.. i dont have an option to boot to an older kernel so i'm not sure what to do.. i dont want to do a fresh install either.. can someone please help? thanks!

---

### Post by DagMan on 2007-04-30
I don't know if this will work from one kernel version to the next and it could be a little dangerous doing at such.   This is the easiest thing for me though when I recompile a kernel because I'm left with a kernel of a name 2.6.20***ubuntu-custom and it's looking for firmware of the same name of the kernel, but all that's on the drive is firmware of the old driver, so while in the new kernel I do this 
cd /lib/firmware
ls
and usually there's a folder in there of my previous kernel's name.
sudo cp -r previous-name `uname -r`
and that was enough for my old laptop with ipw2200 but with my new one with ipw3945 I had to additionally do
sudo cp /sbin/ipw3945d-old-kernel /sbin/ipw3945d-`uname -r`
and then reboot

Most recently for example it was 
sudo cp -r  /lib/firmware/2.6.20-15-generic  /lib/firmware/`uname -r`
and
sudo cp /sbin/ipw3945d-2.6.20-15-generic  /sbin/ipw3945d-`uname -r`

I don't know if the firmware from edgy is compatible with the firmware that feisty uses or if it can be damaging to the hardware if it is a differant version.

---

### Post by chili555 on 2007-05-01
atd85-

Please try:```
 sudo apt-get install --reinstall linux-restricted-modules-generic
```See if your ipw3945 works again.

---

