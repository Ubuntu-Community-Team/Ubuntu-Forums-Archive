---
title: "Wireless troubles after upgrading to 8.04 LTS"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by .haNk on 2008-05-13
I upgraded from 7.10 to 8.04 LTS the other night, and now I'm having some trouble connecting to my AP. I had to boot an older kernel to get online. Any help or general direction pointing would be greatly appreciated. :)


Here's a sample of dmesg (larger dump attached):

[  113.608000] wlan1: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  113.608000] wlan1: hfa384x_cmd_issue - timeout - reg=0x8000
[  113.608000] wlan1: hfa384x_cmd: entry still in list? (entry=c7c8e1c0, type=0, res=-1)
[  113.608000] wlan1: hfa384x_cmd: interrupted; err=-110
[  113.608000] wlan1: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fdc6, len=12)
[  113.612000] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[  113.612000] wifi0: hfa384x_cmd_issue - timeout - reg=0x8000
[  113.612000] wifi0: hfa384x_cmd: entry still in list? (entry=c7c8e1c0, type=0, res=-1)
[  113.612000] wifi0: hfa384x_cmd: interrupted; err=-110
[  113.612000] wifi0: hfa384x_get_rid: CMDCODE_ACCESS failed (res=-110, rid=fd51, len=6)


Here's the output from 'lspci -vvnn' for my adapter:

01:06.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)
	Subsystem: Netgear MA311 802.11b wireless adapter [1385:4105]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fdfff000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>


Let me know if anything else is needed

---

### Post by hermes0710 on 2008-05-13
It seems to be a driver problem especially when you say that switching to other kernels makes it possible to connect. Have you installed the backport modules?

---

### Post by chili555 on 2008-05-13
Please check post #3 here: [http://ubuntuforums.org/showthread.php?t=470980&highlight=prism2](http://ubuntuforums.org/showthread.php?t=470980&highlight=prism2)

---

### Post by .haNk on 2008-05-14
Thank you for the responses!

Unfortunately, there seem to be no prism modules running when I boot into the latest kernel on my system (2.6.24-16-generic). I have attached a dump of 'lsmod' for reference. When I boot into the older kernel and do a 'lshw', it shows that "hostap" is the driver used for my card. Edit: I see the same when I boot into the newer kernel.

I truly appreciate any suggestions that anyone may have. I have never had to deal with drivers/modules before, so this is a great learning experience for me.

Optimism... \\:D/

---

### Post by .haNk on 2008-05-14
I feel like an ***. I completely disregarded hermes0710's post, but that is the one that solved the problem.

Simply ran:

apt-get install linux-backports-modules-2.6.24-16-generic


...and the problem was fixed after a reboot. Thanks much!

---

