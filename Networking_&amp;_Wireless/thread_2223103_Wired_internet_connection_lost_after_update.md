---
title: "Wired internet connection lost after update"
date: 2014-05-09
forum: Networking &amp; Wireless
---

### Post by Kingsrookie on 2014-05-09
As the post describes, I recently updated my Ubuntu 12.04 system after a fresh install and restarted. After restarting the system, I no longer have wired internet connection. I can't update through the update manager and going to Additional Drivers pulls up nothing. As a side note, I do not have wireless capabilities either. I should be able to fix this by downloading the broadcom driver but can't since ethernet is now out as well.

---

### Post by varunendra on 2014-05-09
A blind shot base purely on guess -

Please open a terminal (Ctrl-Alt-T) and do -
```
sudo apt-get purge bcmwl-kernel-source
```
..and reboot. Is the wired connection back? If yes, additionally do (on next boot, when you are connected to internet) -
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rv b43
sudo modprobe -v b43
```
Is wireless working too now?

If not, please post back the outputs of -
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
```
While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by slickymaster on 2014-05-09
Moved to the **Networking & Wireless** sub-forum.

---

### Post by Kingsrookie on 2014-05-09
Slicky, thanks for moving to the appropriate sub-forum.

Varu, thanks for the your response! I actually kept doing more research on the subject and got it working.(I'm currently doing updates so may have to wait until after they finish to know if it works or not) I got both wired and wireless working. You were on the right track of how to get it fixed so I will list here what I did to get it working for future people.

First things first, after installing 12.04 I had wired but no wireless. Installing updates and doing a reboot knocked out my wired and still had no internet. I decided to do a reinstall and negate doing updates during the process so that I could get wireless up in case wired would get knocked out.

I ran
sudo apt-get remove bcmwl-kernel-source

After removing the source I checked the type of wireless card and found it to be a Broadcom 4311. I then ran
sudo apt-get install firmware-b43-installer b43-fwcutter

This installed both packages needed to run the wireless driver but I still was blocked. I wanted to see if the module was loaded so ran.
cat /etc/modprobe.d/* | grep 'bcm'

This was how I actually found the type of wireless card I had. It was located in the blacklist.conf file.

A simple edit of the blacklist.conf and a reboot fixed the issue.

I located the line that held blacklist bcm43xx and put a comment(#) in front.

This worked for me and hopefully others. Varu, as I had said earlier, you were on the right track with your response but I was impatient and kept looking:). Thanks for your help!

---

### Post by varunendra on 2014-05-09
The "wl" driver blacklists the "b43" and "ssb" along with some other drivers. The "ssb" is required by the "b44" driver as well which is an ethernet driver. The command "apt-get remove.." without the "--purge" option only removes the driver, but not the blacklisting. Whereas the "apt-get purge..." or the "apt-get remove --purge..." command also removes any configurations done by a package, which means the blacklisting in case of the "wl" driver (or "bcmwl-kernel-source" package).

So.. the solution in its simplest form (where "b43" and "b44" both are needed) is -
```
sudo apt-get purge bcmwl-kernel-source
```
..reboot. This enables the ethernet, using which install the firmware package -
```
sudo apt-get install linux-firmware-nonfree
```
..which installs all the firmware files the "b43" driver may ever need. Reboot and done!
(rebooting is not necessary in both steps, it is just much simpler to remember than remembering three extra commands which can do what a reboot does. ;)

---

