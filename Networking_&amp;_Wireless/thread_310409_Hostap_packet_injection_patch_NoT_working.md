---
title: "Hostap packet injection patch NoT working"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by qedqed on 2006-12-01
Hi all,

   I was trying to patch my hostap drivers for packet injection but i had many problems and seems there is no way to make it works.
I have a senao 2511CD ext2 pcmcia card. Used firmware 1.7.4 and 1.8.2. and I'm trying with my DWL-2100AP firmware 2.10eu. I also use a bcm4306 on my notebook.

1) Downloaded kernel source 2.6.18.3, downloaded [hostap-kernel-2.6.18.patch]("http://patches.aircrack-ng.org/hostap-kernel-2.6.18.patch") and patched successfully the kernel. Compiled and no problems.
When i use packet injection just nothing, likes with the not patched drivers.

2) Downloaded [hostap-driver-0.4.9.tar.gz]("http://hostap.epitest.fi/releases/hostap-driver-0.4.9.tar.gz") and [hostap-driver-0.4.7.patch]("http://patches.aircrack-ng.org/hostap-driver-0.4.7.patch") as i found on the aircrack patching tutotiral. If i do make i got 
"
*** Can't build for 2.6 with a non-2.6 source!
make: *** [2.6] Error 1
"
If i replace the kernel driver i got a lot of compiling errors.


Anyone has the same problem? Another strange thing is that i have 2 interfaces: eth3 and wlan0_rename
eth3 is working but NoT on any WEP network, setting the key there is useless.

---

### Post by yeehawjared on 2006-12-02
hey man i have the same card... i have the card working in ubuntu - not sure if packet injection is working though.  I usually pop in the backtrack2 liveCD for that.  I recently reformatted and decided not to dual book backtrack.  Here's what i've done so far to get my card detected as wlan0 and prism2.


nano /etc/modprobe.d/blacklist
add these lines
blacklist orinoco_plx
blacklist orinoco_cs
blacklist orinoco_pci
blacklist orinoco


nano /etc/kismet/kismet.conf
edit this line:
source=hostap,wlan0,hostap

that should get your kismet working, and hopefully your card will get detected with hostap drivers.  Your best bet is to downgrade your card to 1.7.4 in XP and pop in the backtrack2 cd.  Use this aircracking script:

[http://airoscript.aircrack-ng.org/](http://airoscript.aircrack-ng.org/) - official site
[http://forums.remote-exploit.org/showthread.php?t=3590&page=18](http://forums.remote-exploit.org/showthread.php?t=3590&page=18) -discussion on a pre beta version

Also, you'll want to get the latest aircrack-ng tools (aireplay-ng, airodump-ng, airmon-ng).  Go the the website, download, extract, make, and make install.  apt-get install aircrack-ng will work, but its a slightly outdated version

I'll update my injection progress in this thread, and hopefully other senao users can use this to figure things out.


edit:  if you have problems still, copy and paste your dmesg and iwconfig outputs.

---

### Post by qedqed on 2006-12-03
I fixed it :)

The problem was the kernel source without the *include/linux/version.h*.

The best thing to make it works is:

[LIST]
[*]Get the kernel source 2.6.18.3 (not 2.6.19 for many reasons, not the hostp drivers btw), patch it with [hostap-kernel-2.6.18.patch]("http://patches.aircrack-ng.org/hostap-kernel-2.6.18.patch").

[*]Compile and install it (make-kpkg is handy).

[*]Be sure that *udev* AND *Network-Manager* is not fxxxing your interfaces. You can #/etc/init.d/udev stop, #cardctl eject, #cardctl insert. If you dont see wlan0 and wifi0 check it again.

[*]You have to put in monitor mode in Monitor mode wlan0 and/or wifi0, but you can inject ONLY from wlan0. Dont trust *airmon*!!!

[*]Cheers :)
[/LIST]

EDIT: Packet injection is working very good.

---

### Post by yeehawjared on 2006-12-03
question man...  I'm following the following guides to compiling an updated kernel:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
[http://www.ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel](http://www.ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel)

Like you said, I'm upgrading to kernel source 2.6.18.3

How do i patch it with hostap-kernel-2.6.18.patch before compiling?


I also saw your thread here:
[http://tinyshell.be/aircrackng/forum/index.php?PHPSESSID=ad3e5f33989c82f92cc15a37cf7fa5c6&topic=875.0](http://tinyshell.be/aircrackng/forum/index.php?PHPSESSID=ad3e5f33989c82f92cc15a37cf7fa5c6&topic=875.0)

I'll continue to search forums for a howto for patching kernels prior to compiling... also, I read that I may run into problems upgrading the kernel with NVIDIA drivers?  Did you run into any problems?  Thanks again for your help :)

---

### Post by yeehawjared on 2006-12-03
so i think this is how to patch before compiling

cd /usr/src/linux-2.6.18.3/drivers/net/wireless/hostap
patch -p1 < /full/path/to/patch

I get problems:

```
root@jaredtop:/usr/src/linux/drivers/net/wireless/hostap# patch -p1 < /root/Desktop/hostap-kernel-2.6.18.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -ur linux-2.6.18-gentoo/drivers/net/wireless/hostap/hostap_80211_tx.c linux-2.6.18-gentoo-rawtx/drivers/net/wireless/hostap/hostap_80211_tx.c
|--- linux-2.6.18-gentoo/drivers/net/wireless/hostap/hostap_80211_tx.c  2006-09-21 01:26:27.000000000 -0400
|+++ linux-2.6.18-gentoo-rawtx/drivers/net/wireless/hostap/hostap_80211_tx.c    2006-09-21 01:30:18.000000000 -0400
--------------------------
File to patch: 

```

what's all this gentoo stuff?  Am I using the correct patch?  I used the one you linked to above


[COLOR="Red"]EDIT:  got it to work.  you need to be in /usr/src/linux-2.6.18.3

root@jaredtop:/usr/src/linux-2.6.18.3# patch -p1 < /root/Desktop/hostap-kernel-2.6.18.patch[/COLOR]

---

### Post by yeehawjared on 2006-12-03
yup, had NVIDIA problems when trying to startx with the new kernel.  Time to re-compile, but following this guide instead of howto.org's.

[http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657)

---

### Post by qedqed on 2006-12-05
Good, but if you used "make oldconfig" it's hard that you have problems.

After compiling the new kernel you have to *REINSTALL* NV drivers while running the new kernel.

I also suggest you to disable the Preemption, i rly cant undestarnd what's for. My applications are slower than ever and even the screen redraw is incredibly slow.

Last thing, you will get a lot of problems with 2.6.19 if you have to compile external modules. 2.6.18.3 is working perfect... check the changelog and think if it worth it.

---

### Post by yeehawjared on 2006-12-05
I got the kernel re-compiled and nvidia drivers working.  I haven't yet verified that packet injection works.  I'll try later tonight using daouid's airoscript:

[http://airoscript.aircrack-ng.org/](http://airoscript.aircrack-ng.org/)
[COLOR="Red"]
edit:  packet injection now works like a champ.  sexy time! /borat[/COLOR]

---

### Post by eddietop on 2006-12-13
Also got this working on the 2.6.18.3 kernel with hostap patch. Injection is nice and fast ;)

---

