---
title: "Using ndiswrapper with Atheros driver..??"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by Robert.Zapata on 2006-11-14
Hello there:

What I'm missing here..?? I'm not getting the final output as explained per magicfab thread explaining the process..!!!

I follow the instructions in the following link:

**[http://ubuntuforums.org/showthread.php?t=9454](http://ubuntuforums.org/showthread.php?t=9454)**

but I'm getting this:

> 
rob@Thinkpad:~$ sudo ndiswrapper -i WiFi/NET5211.INF
Installing net5211
rob@Thinkpad:~$ ndiswrapper -l
Installed ndis drivers:
net5211         driver present, hardware present
rob@Thinkpad:~$ sudo modprobe ndiswrapper
rob@Thinkpad:~$ sudo dmesg | grep ndis
[17181772.412000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
rob@Thinkpad:~$


I got the driver from here:

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-66449](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-66449)

This is for a Thinkpad R60e

The WiFi card is using the Atheros AR5212

Per the "lspci" command:

> 
0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)


Thanks

---

### Post by FrodoB on 2006-11-14
What kind of card it this? (PCI, mini-PCI) 

If it is not USB then it should just work in Ubuntu 6.10 Edgy Eft out of the box. At least my Atheros card does.

---

### Post by Robert.Zapata on 2006-11-14
Is mini-PCI.

Thanks!

---

### Post by FrodoB on 2006-11-15
The way mine worked is that I just plugged in my PC Card and then I  did the setup in the Networking control panel and everything was happy, just like it should be.

Best of luck. mini-PCI should be the same. Let us know if it was.

---

### Post by Robert.Zapata on 2006-11-15
Forgot to mentioned that after re-starting the machine and doing the modprobe and dmesg commands I get the following:

> 
rob@Thinkpad:~$ sudo modprobe ndiswrapper
rob@Thinkpad:~$ sudo dmesg | grep ndis
[17179802.212000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[17179802.300000] ndiswrapper: driver net5211 (,04/18/2006,4.1.102.147) loaded
[17179802.300000] ndiswrapper (NdisWriteErrorLogEntry:230): log: C0001389, count: 4, return_address: e075e674
[17179802.300000] ndiswrapper (NdisWriteErrorLogEntry:233): code: 3393951416
[17179802.300000] ndiswrapper (NdisWriteErrorLogEntry:233): code: 40
[17179802.300000] ndiswrapper (NdisWriteErrorLogEntry:233): code: 3395878912
[17179802.300000] ndiswrapper (NdisWriteErrorLogEntry:233): code: 3395878912
[17179802.300000] ndiswrapper (miniport_init:240): couldn't initialize device: C000009A
[17179802.300000] ndiswrapper (pnp_start_device:479): Windows driver couldn't initialize the device (C0000001)
[17179802.300000] ndiswrapper (miniport_halt:271): device ca4b92a0 is not initialized - not halting
[17179802.300000] ndiswrapper: device eth%d removed
[17179802.300000] ndiswrapper: probe of 0000:03:00.0 failed with error -22
rob@Thinkpad:~$


I'm almost ready to wipe the machine and perform a fresh install of 6.10. *(presently is 6.01LTS)* If 6.10 does not work well I'll try SuSE 10.1.

---

### Post by Robert.Zapata on 2006-11-15
> **FrodoB said:**
> What kind of card it this? (PCI, mini-PCI) 

If it is not USB then it should just work in Ubuntu 6.10 Edgy Eft out of the box. At least my Atheros card does.

FrodoB:

You are right...!!! I wipe out the whole HD and fresh install the latest and greatest (6.10) and IT WORKS....!!!!

Everything worked out of the box...!!! I was afraid of installing 6.10 due to all the bad crap but I guess you need to try first and check for yourself.

Mods: This thread can be closed.

Thank you very much.

---

### Post by dannyboy79 on 2006-11-15
my netgear atheros 5212 chip pcmcia card worked out of the box on dapper xubuntu right now so I am not sure why you were having problems. at least you got it working now with edgy.

---

