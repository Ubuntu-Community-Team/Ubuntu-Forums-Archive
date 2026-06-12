---
title: "install audio drivers in jaunty"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by siddhuc on 2009-08-19
I am just new to ubuntu.. can anyone guide me through steps to install enable audio in ubuntu jaunty?:)

---

### Post by swoll1980 on 2009-08-19
It should do it for you. What kind of card you have?

---

### Post by nikhilbhardwaj on 2009-08-19
they are already installed

---

### Post by jrlii on 2009-08-19
For the common audio cards, they should be detected and the default drivers should work.

Now, if you are trying to use a multi-track recorder card, things get a lot more complicated, and in some cases you may have to compile the drivers, or edit some configuration files.

ALSA has pretty good directions for compiling ALSA drivers, which is necessary when cards need to have firmware loaded to work, which is not part of the normal version of the driver.

---

### Post by siddhuc on 2009-08-24
can u tell me how to check wat card am i using?

---

### Post by halitech on 2009-08-24
can you post the output of
```
lspci
```

---

### Post by siddhuc on 2009-08-24
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by siddhuc on 2009-08-25
can u say wat i ve to do next?

---

### Post by halitech on 2009-08-25
open a terminal and run
```
aplay -l
```and see if it gives any results. if it does, run ```
alsamixer
```and make sure nothing is muted

---

### Post by barnex on 2009-08-25
When your sound is not working, check out the documentation on this issue. E.g., you can visit:

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)


It seems you have an nVidia MCP67 High Definition Audio card, you could also google on this...

---

### Post by siddhuc on 2009-08-25
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital Audio [Conexant Digital Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Conexant HSF Modem [Conexant HSF Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by siddhuc on 2009-08-25
checked alsamixer and nothing is muted

---

### Post by siddhuc on 2009-08-25
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital Audio [Conexant Digital Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Conexant HSF Modem [Conexant HSF Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7842840") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7842840")

---

