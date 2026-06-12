---
title: "In Desperate Need of Assistance (Agere Systems Modem)"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by AnthonyG on 2006-11-28
Hello everyone , I've been having quite a time attempting to get my Agere Systems PCI 56K Soft Modem to work in Ubuntu. I am completely out of ideas, So please, Any assistance would be appreciated. I'm quite familiar with compiling C/C++ programs , build-essential is installed :).

Edit: Apologies for not stating what exactly I needed assistance with, Dialing will be no problem, Drivers are my main problem.

```

 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
 Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2006_November_07


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 03:0b.0	11c1:048c	11c1:044c	Communication controller: Agere Systems V.92 56K WinModem 

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 03:0b.0 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  03:0b.0
   Class 0780: 11c1:048c Communication controller: Agere Systems V.92 56K WinModem
      Primary PCI_id  11c1:048c
 Support type needed or chipset:	Agere.SV2P
 Under Linux 2.6.n kernels, the chipset is NOT SUPPORTED . Read InfoGeneral.txt about alternatives.


 Vendor 11c1 is Lucent Technologies or subsidiary Agere Systems, Inc. Their Linux
 code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its 
 continued maintenance is only initiated at the request of a major chipset buyer,
 or comparable sponsor. Several different  modem chipset types  are produced, 
 and two have support under Linux:
 Device ID  Support        Name           Comment
 ---------  -------------  -----------    -----------------------------
 0480       serial drivers Venus           controller chipset 1673JV7
 0440-045d  martian        Mars/Apollo     DSP (digital signal processing) chipsets
 0462       none           56K.V90/ADSL Wildwire 
 048(c,d,f) none           SV2P            soft modem 
 0600       none                           soft modem, very few in the field.
 062(0-3)   none           SV92PP,Pinball  soft modem, in some HP desktop PCs

-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   kernel_headers base folder /lib/modules/2.6.17-10-generic/build


Checking pppd properties:
	-rwsr-xr-- 1 root dip 260920 2006-07-10 15:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

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


 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

```

---

### Post by AnthonyG on 2006-11-29
Hm... I'm aware modems are black magic when it comes to Linux , But I simply cannot find any more solutions , I'm going in circles ](*,) .

Here is a dump of lspci -vv for my modem.

```

03:0b.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
	Subsystem: Agere Systems Unknown device 044c
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (63000ns min, 3500ns max)
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at fddff000 (32-bit, non-prefetchable) [size=256]
	Region 1: I/O ports at bc00 [size=8]
	Region 2: I/O ports at b800 [size=256]

```

---

### Post by trubblemaker on 2006-11-29
did you [read the pinup?]("http://www.ubuntuforums.org/showthread.php?t=308098")

---

### Post by AnthonyG on 2006-11-29
Yes, And as I said; Circles :(

---

### Post by AnthonyG on 2006-11-29
What about these "SmartLink" drivers , According to the description it supports other chipsets.

---

