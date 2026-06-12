---
title: "Problems with hardware and windows programs"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Nathroq on 2010-07-27
Hello, about 4 months I decided to quit windows for good. I had a friend developer helping me with my main laptop and installed Ubuntu 10.04, and got used in everything but some  office tools or compatibility of documents, so i kept using my old laptop with MSWin for working some o my documents. Finally, 3 days ago i decided to use just Ubuntu, so i formated the old one and installed Ubuntu 10.04 too.
Its a HP Pavilion Dv 6408nr, bus its giving me a hard time, the wireless broadcom is not always recognized, i installed the drivers from synaptics and the hadware driver too (now the wireless driver is gone from the list), another issue_ when i disable the touch pad the keyboard stops working till i reboot.  The forums had been extremely helpful, but i haven't find a way to solve this...
Another BIG issue, I installed Crossover and the MS Office suite (OHH NOOO!!!) I did it just for the serious compatibility issues with some of my documents, but i've lost documents i'm working on when I save them is MSO. I really wanna quit Ms, but still have compatibility  issues by working on Open Office, so I need MSO for now.
Im getting used to work with terminal, but as a begginer, takes time. 
Any advise???
I apreciate all tHe help you can give me. THANKS!!!

---

### Post by P4man on 2010-07-27
Is the wireless problem solved or not now? If not; some more details please.

As for the keyboard no longer working after you disable the touchpad; how are you disabling the touchpad?

---

### Post by VH-BIL on 2010-07-27
There may be a better solution but...

I have had problems with my wireless NextG modem sometimes not being recognized. I restart the modem manager when that happens. It happens so much I made a script for it and added an icon on my task bar.

```
#!/bin/bash
zenity --question --title "modem-manager reloader." --text "Are you sure you want to reload the modem manager?"
if [ $? = 0 ]
then
  gksudo killall modem-manager
fi
```

I do not use wireless lan but if you find the process that needs to be reloaded you may be able to edit and use this script. You may also need to reload the process in the script as the modem manager auto spawns.

---

### Post by Nathroq on 2010-07-27
Nope, wireless isn't working... just some times after i reboot, but is 1 of every 5 times. As for the touch pad, i disable it manually on the disable key of the hardware Right now, I've already deactivated from the mouse preferences, hope it works, it just happens on the DV6 I work also with a mini 2140 with Ubuntu 10.04 and use the mouse deactivation key with no problems...

---

### Post by Nathroq on 2010-07-27
Thnks, i tried. But i doesnt seem to work.Its like the wireless modem is banished, at first it appeares under hardware driver as propietary but now is gone...

---

### Post by P4man on 2010-07-27
First things first; is wireless networking enabled? Right click the network manager and see if its checked (or the option available).

if the option is not available; make sure you dont have a hardware switch thats turned off. Also can you post the ouput of

```
lspci
```

and 

```
lsusb
```

If all else fails; there is always ndiswrapper that lets you use windows drivers for the wireless card (please note if you use 64 bit ubuntu you will need 64 bit windows driver) but lets see about the rest first.

---

### Post by Nathroq on 2010-07-27
Network is enabled, i have been using it with mobile broadband, its just that wireless is not working 
I did as you said and this is my hardware
With lspci:

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


And lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 004: ID 05dc:a761 Lexar Media, Inc. 
Bus 001 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by P4man on 2010-07-27
> **Nathroq said:**
> Network is enabled,

I said wireless networking, like this:

[IMG]http://a.yfrog.com/img507/3963/screenshot005n.png[/IMG]

But I assume you dont have that option?
If not, then Im guessing you have a hardware switch for the wifi thats turned OFF? Or it could be a keyboard combination like Fn+F2.

---

### Post by Nathroq on 2010-07-27
Wireless switch is enabled, but even if i move it, it remains with the disable notification led, as I said, if reboot a couple of times it recognizes it, but just about 20% of the reboots.

---

