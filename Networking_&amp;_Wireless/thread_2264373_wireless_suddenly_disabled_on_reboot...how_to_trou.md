---
title: "wireless suddenly disabled on reboot...how to troubleshoot?"
date: 2015-02-07
forum: Networking &amp; Wireless
---

### Post by andrea b on 2015-02-07
I am a relative newbie, running 14.04 on a Thinkpad X60  (dual boot with XP). I've never had any problems with the wireless connection until rebooting today; the applet shows no networks. In System Settings, everything looks correct... Checked Wifi in XP - works fine (not that I'd go online with XP!)  I began researching how to troubleshoot this (rfkill, etc) and was confused by the options.

Any guidance much appreciated...Where do I begin?

---

### Post by ajgreeny on 2015-02-07
Have you just updated to a new 3.13.0-45 kernel that came very recently? It may have some problem with your wifi driver.

Let's see the output of ```
lspci -nnk | grep -iA2 net
``` in terminal to show us your wireless adapter, followed by ```
uname -a
``` to show the kernel in use.

---

### Post by andrea b on 2015-02-07
Thanks in advance, and here it is:
```
andrea@andrea-ThinkPad-uX60:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
	Subsystem: Lenovo ThinkPad X60s [17aa:207e]
	Kernel driver in use: e1000e
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
	Subsystem: Intel Corporation Device [8086:1010]
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b4)
andrea@andrea-ThinkPad-uX60:~$ uname -a
Linux andrea-ThinkPad-uX60 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:37:48 UTC 2015 i686 i686 i686 GNU/Linux
andrea@andrea-ThinkPad-uX60:~$ 



```

There were updates to packages...but I didn't intentionally update kernel, or wasn't aware of an update to kernel...  

For future replies - will using live disc give us what we need if I get wireless via live disc?  I'm cutting and pasting terminal output onto a flashdrive file.

Thanks again!

---

### Post by ajgreeny on 2015-02-07
Depending on how you update, the kernel my be simply updated along with everything else.  Only if you use ```
sudo apt-get update
sudo apt-get upgrade
```does it not happen by default.

Using a live systerm will still report the hardware properly but probably not the driver software, so you need to do that from the command line if you can.

For your ethernet problem have a look at [http://ubuntuforums.org/showthread.php?t=2222374](http://ubuntuforums.org/showthread.php?t=2222374) which was for the same card.

---

### Post by andrea b on 2015-02-07
I did both apt-get and apt-upgrade yesterday and today... 

The firmware thread is interesting...while it seems a different situation (fresh ubuntu install from live disc), maybe my update process fouled things up?   

Anyway ... just did it, and here's what came up:
```
andrea@andrea-ThinkPad-uX60:~$ sudo apt-get install --reinstall linux-firmware
[sudo] password for andrea: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 6 not upgraded.
Need to get 0 B/19.9 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 264504 files and directories currently installed.)
Preparing to unpack .../linux-firmware_1.127.11_all.deb ...
Unpacking linux-firmware (1.127.11) over (1.127.11) ...
Setting up linux-firmware (1.127.11) ...
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ trusty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
andrea@andrea-ThinkPad-uX60:~$
```

---

### Post by jeremy31 on 2015-02-07
Try ```
sudo modprobe -v iwl3945
```

---

### Post by andrea b on 2015-02-07
Ok - here we go:

```
andrea@andrea-ThinkPad-uX60:~$ sudo modprobe -v iwl3945
[sudo] password for andrea: 
modprobe: FATAL: Module iwl3945 not found.
andrea@andrea-ThinkPad-uX60:~$ 

```

---

### Post by jeremy31 on 2015-02-07
Reboot, and hold Shift key to get grub menu, select advanced option or previous version and then select the 3.13.0-44 kernel and see if wifi returns

---

### Post by andrea b on 2015-02-07
THANKS!!! (I do realize that all-caps is sort of like yelling - but I'm yelling thank-you!)  Wifi is back. 

The previous kernel seems to have been -40, not -44. Will I need to select this every time I reboot? 

Again ... thanks!

---

