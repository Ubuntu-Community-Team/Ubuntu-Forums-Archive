---
title: "SLModem: init script broken?  No Carrier problem..."
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by bkudria on 2006-08-22
Hi, I have a winmodem which is purportedly supported by slmodem..but I have two problems:

Problem 1 - 
    The init script doesn't work.  It prints:

Starting SmartLink Modem driver for: slamr0.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.

But it isn't actually running!  The is no slmodemd process, and /dev/ttySL0 doesn't exits.  I can start it manually, though, with "sudo slmodemd --alsa -c USA hw:0,0", and it works!  I can query my modem fine with KPPP.  

Question 1: how do I fix the init script?

Problem 2 - 
    If I start slmodemd as above, with "sudo slmodemd --alsa -c USA hw:0,0", I can query the modem correctly with KPPP...but trying to dial gets me a "No Carrier"  error.  My PPP log looks like this:

ug 22 20:35:42 [pppd] pppd 2.4.4b1 started by bkudria, uid 1000
Aug 22 20:35:43 [chat] abort on (BUSY)
Aug 22 20:35:43 [chat] abort on (NO CARRIER)
Aug 22 20:35:43 [chat] abort on (VOICE)
Aug 22 20:35:43 [chat] abort on (NO DIALTONE)
Aug 22 20:35:43 [chat] abort on (NO DIAL TONE)
Aug 22 20:35:43 [chat] abort on (NO ANSWER)
Aug 22 20:35:43 [chat] abort on (DELAYED)
Aug 22 20:35:43 [chat] send (ATZ^M)
Aug 22 20:35:43 [chat] expect (OK)
Aug 22 20:35:43 [chat] ATZ^M^M
Aug 22 20:35:43 [chat] OK
Aug 22 20:35:43 [chat] -- got it_
Aug 22 20:35:43 [chat] send (ATDT3298888^M)
Aug 22 20:35:43 [chat] expect (CONNECT)
Aug 22 20:35:43 [chat] ^M
Aug 22 20:35:43 [chat] ATDT3298888^M^M
Aug 22 20:35:43 [chat] NO CARRIER
Aug 22 20:35:43 [chat] -- failed
Aug 22 20:35:43 [chat] Failed (NO CARRIER)
Aug 22 20:35:43 [pppd] Connect script failed
Aug 22 20:35:44 [pppd] Exit.

Question 2:  How do I get dialing to work?

Any help with either of these is greatly appreciated!  Thanks!

ModemData.txt contents:
```
 
Only plain text email is forwarded by the  DISCUSS@linmodems.org List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.06.1 LTS  kernel 2.6.15-26-386 
 This will alert cogent experts, and  distinguish cases in the Archives 
 YourCounry is not essential, but will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org
--------------------------  System information ----------------------------
 Ubuntu 6.06.1 LTS 
Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
 scanModem update of:  2006_August_22

	Checking for ALSA (Advanced Linux Sound Architecture) 
compatible modem cards with:  aplay -l | grep -i modem
---------------------------



Checking /proc/asound/  folders for modem support.
	/proc/asound/pcm
-------------------------
00-00: HDA Generic : HDA Generic : playback 1 : capture 1

A candidate ALSA low level modem driver is:    snd-hda-intel
               The node for modem setup is:    modem:


=======================================================
 For candidate modem in PCI bus 0000:00:10.1, System summary: 
                    -----PCI_IDs-------                    --CompilerVer- 
    Feature List:   Primary  Subsystem Distr  KernelVer   kernel default CPU
   ./scanModem test 10de:026c 103c:30b7 Ubuntu 2.6.15-26-386 4.0.3 4.0.3 i686 
 ------------------------------
 Chipset or support type: 

 With modem hardware:
   0403: nVidia Corporation MCP51 High Definition Audio 
   with Primary PCI_id  10de:026c
    and a SubSystem_id  103c:30b7
   using interrupt (IRQ) 9 , with sharing reported from /proc/interrupts:
         5:     165982          XT-PIC  libata
  9:     364450          XT-PIC  acpi, HDA Intel
 10:    3737562          XT-PIC  ohci1394, sdhci:slot0, ndiswrapper, nvidia

====== Writing residual advice ========

 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.0
   kernel_headers base folder /lib/modules/2.6.15-26-386/build


Checking pppd properties:
	-rwsr-xr-- 1 root dip 257720 2006-07-05 09:00 /usr/sbin/pppd
To enable dialout without Root permission do:
	$ su - root
        # chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	$ SUDO chmod a+x /usr/sbin/pppd
Checking settings of:	/etc/ppp/options
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

Read Modem/YourSystem.txt concering other COMM channels: eth1
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

# start/stop the daemon when the USB modem is connected
KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   lrwxrwxrwx 1 root root 6 2006-08-22 19:25 /dev/modem -> ttySL0
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
/etc/udev/rules.d/030_sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/rules.d/030_sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
/etc/udev/sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/sl-modem-daemon.modutils:install slamr modprobe --ignore-install ungrab-winmodem ;  modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0) 
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


```

---

### Post by bkudria on 2006-08-23
Bump?  Anyone have any idea?

---

### Post by robihun on 2007-10-21
I also have NO CARRIER problem but already solved by installing
linex-kernel-devel
linux-libc-dev
libc6-dev

---

### Post by mickeyWD on 2008-01-04
Why this should solve problem?

---

### Post by jbernardo on 2008-02-17
I also have the "NO CARRIER" problem, with a modem that is identified by "aplay -l" as a Si3054. As it shows as device #6, the parameters I had to put in /etc/default/sl-modem-daemon were 'SLMODEMD_DEVICE="hw:0,6"'.

---

