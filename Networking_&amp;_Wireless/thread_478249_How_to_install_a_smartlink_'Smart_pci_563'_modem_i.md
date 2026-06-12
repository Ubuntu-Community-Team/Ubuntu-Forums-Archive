---
title: "How to install a smartlink 'Smart pci 563' modem in ubuntu?"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by hasannoori on 2007-06-19
Dear All.
 I Received An Edubuntu CD From Canonical.Ltd 
 It is Easy To install And Use  .
 It Supported All hardware on my system . :(
 i am a newbie to linux and ubuntu!  
Please help me to install, configure and use my modem to connect to internet.:)

---

### Post by hasannoori on 2007-06-20
Hey!
 Have any idea?
Help me!!!!!

---

### Post by hasannoori on 2007-06-20
delited

---

### Post by hasannoori on 2007-06-20
hey All!
 I think My Problem is'nt very Hard To you?!!!!:(

---

### Post by Bartender on 2007-06-20
> **hasannoori said:**
> hey All!
 I think My Problem is'nt very Hard To you?!!!!:(

First off, the problem can be very hard.

I've read several posts where the person went thru hell trying to get a winmodem such as the 537 to work.  I've got an Intel 536.  Looked at the directions and gave up.  Way too hard for me.

Are you sure you've entered username and password correctly?  If the ISP wants "johndoe@isp.com" and you just put in "johndoe" (or vice versa) you'll be kicked off with no clue of what went wrong.

You may be better off to leave your dad on Windows until you can research the source of the problem.  Most of the older generation who didn't grow up in the PC age have learned just enough to get around in Windows and can be very relusctant to start over again with another OS.

I hear that better winmodem support is a priority for the next Ubuntu.  Hopehopehope

---

### Post by hasannoori on 2007-06-24
hello all!
i am a beginner in linux and ubuntu, I install ubuntu dapper(ver 6.06) on my PC.
I want to install modem And connect to the Internet(by Dial-Up).
but i can't install modem and create a connection.
please help me.
my modem is Smartlink HCF 56k fax Voice Modem(This information show's in Ubuntu hardware manager)T
but in windows show me: Rockwell HCF 56k fax Voice Modem.
if i can instaall modem then i remove windows and all of them.

---

### Post by hasannoori on 2007-06-27
Hey 
any idea

---

### Post by Bachstelze on 2007-06-27
Please download scanModem, run it and post the results.

[http://linmodems.technion.ac.il/#scanModem](http://linmodems.technion.ac.il/#scanModem)

---

### Post by hasannoori on 2007-06-27
Okey 
Thanks
Follow it:
```
 Only plain text email is forwarded by the  DISCUSS@linmodems.org List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry 
Welcome to openSUSE 10.2 (i586) - Kernel  kernel 2.6.18.2-34-default 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org .
 Local Linux experts can be found through: http://www.linux.org/groups/index.html
--------------------------  System information ----------------------------
CPU=i686,  
Welcome to openSUSE 10.2 (i586) - Kernel 
Linux version 2.6.18.2-34-default (geeko@buildhost) (gcc version 4.1.2 20061115 (prerelease) (SUSE Linux)) #1 SMP Mon Nov 27 11:46:27 UTC 2006
 scanModem update of:  2007_May_11


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:0b.0	10b9:545a	201f:545a	Modem: ALi Corporation SmartLink SmartPCI563 56K Modem

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 00:0b.0 ----
ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 169
0000:00:0b.0: ttyS2 at I/O 0xd028 (irq = 169) is a 8250
0000:00:0b.0: ttyS3 at I/O 0xd040 (irq = 169) is a 8250
Couldn't register serial port 0000:00:0b.0: -28

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  00:0b.0
   Class 0703: 10b9:545a Modem: ALi Corporation SmartLink SmartPCI563 56K Modem
      Primary PCI_id  10b9:545a
 Support type needed or chipset:	slamr
 

The modem is supported by the Smartlink slamr driver
plus the slmodemd helper utility.  Read the
Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

Writing Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	 kernel-source-2.6.18.2-34-default

For Debian and some related distributions, a package kernel-kbuild-2.6-3 may be needed to support driver compiling


Checking pppd properties:
	-rwxr-xr-x 1 root dialout 295488 2006-11-25 16:50 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
         chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	 chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
noipdefault
noauth
crtscts
lock
modem
asyncmap 0
nodetach
lcp-echo-interval 30
lcp-echo-failure 4
lcp-max-configure 60
lcp-restart 2
idle 600
noipx
file /etc/ppp/filters

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/50-udev-default.rules:KERNEL=="mwave",		NAME="modems/%k", GROUP="uucp"
/etc/udev/rules.d/31-network.rules:SUBSYSTEM=="net", ENV{INTERFACE}=="ppp*|ippp*|isdn*|plip*|lo*|irda*|dummy*|ipsec*|tun*|tap*|bond*|vlan*|modem*|dsl*", GOTO="skip_ifup"
     Within /etc/modprobe.conf files:
/etc/modprobe.conf:# Linux ACP modem (Mwave)
/etc/modprobe.d/blacklist:# ALSA PCI sound/modem modules - should be configured via yast
/etc/modprobe.d/blacklist:blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist:blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


```

---

### Post by hasannoori on 2007-06-27
Deleted,
because I Repeating it.

---

### Post by hasannoori on 2007-07-07
hey any idea!

---

