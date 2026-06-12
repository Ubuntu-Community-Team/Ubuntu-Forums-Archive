---
title: "Cannot download files"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by tirititran on 2007-02-21
Hi everybody,

  Some days ago, I decided to install Ubuntu Dapper Drake in my Toshiba Satellite M40-145 laptop. The installation was OK, and after rebooting everything seemed to work perfectly (including LAN internet connection) until I tried to update. It doesn't matter whether I use Synaptic or directly apt-get in the terminal, it starts downloading the packages but after few seconds the download freezes. After cancelling the download, the internet connection keeps blocked (neverending looking ups), so I have to deactivate and re-activate it and then it works fine (until I try to download again, of course). I experienced similar problems with downloads in general, not only with updates from the repositories. I spent days searching the forums and trying to find out how to fix the problem, but I didn't manage (I am new to linux and although I try to learn as much as I can, I still cannot understand most of the posts I read). Among all the messages I get from dmesg, the ones that I suspect could be related to the problem are:

*) ACPI: Looking for DSDT ... not found!
*) PCI: Cannot allocate resource region 0 of device 0000:06:06.0
*) sky2 0000:02:00.0: No interrupt was generated using MSI, switching to INTx mode. Please report this failure to the PCI maintainer and include system chipset information.
*) eth0: no IPv6 routers present
*) ACPI-0240: *** Error: Cannot release Mutex [MUT1], not acquired


 Somebody please help [-o< , it would be really sad to give up and go back to windows now :-(. 

Further information: 
dual boot ubuntu 6.06-windows XP home (the latter working perfectly)

----from lspci:
*) Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
*) Ethernet controller: Marvell Technology Group Ltd. 88E8036 Fast Ethernet Controller (rev 10) 


Thank you very much in advance.

---

### Post by gradedcheese on 2007-02-21
there seem to be some ACPI problems on that laptop, here's a similar story (with some solutions) that may help: [http://www.cantrip.org/toshiba-m45.html](http://www.cantrip.org/toshiba-m45.html)

---

