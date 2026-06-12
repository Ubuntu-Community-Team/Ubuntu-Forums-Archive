---
title: "Wireless just stopped working"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by tmos22 on 2009-05-04
I installed ubuntu today and i was online all day with it but all of a sudden i got cut off and now i cant get online with it, i can get online with vista just not with ubuntu, i have an Acer laptop 5520

---

### Post by RedSingularity on 2009-05-04
So it just stopped?  Do you see  any wireless networks to connect to in the network manager?  Oh and type "lspci" in the terminal and post the output.

---

### Post by tmos22 on 2009-05-04
It just stopped. i was just browsing and it stopped. when i click it, it shows where ican put vpns and it says wired network disconnected. it is working on vista on the same laptop, when i type that command it says command not found

---

### Post by RedSingularity on 2009-05-04
Did you try restarting the computer?  And i assume you didnt update ubuntu prior to the failure?

---

### Post by tmos22 on 2009-05-04
Yes i tried restarting it, i updated but that  was about 3 hours prior to getting disconnected, i have googled it and it seems like a pretty common problem but no1 has any answer

---

### Post by RedSingularity on 2009-05-04
Ok, type "lspci" in terminal and post the output.

---

### Post by tmos22 on 2009-05-04
command not found

---

### Post by RedSingularity on 2009-05-04
Oh wow thats not good!  Thats part of the system install.  It is one of many commands included in linux.  Now it sounds like your install is corrupted.  Check the install by running "sudo  touch /forcefsck[FONT=Verdana]" then restart the computer.  At boot you will get an error check dialog.  Just let it do its thing.[/FONT]

---

### Post by tmos22 on 2009-05-04
i got nothing from that but when i typed iwconfig in the terminal.i got this

lo             no wireless extensions ( i got that result for the other 3 as well)

eth0

vboxnet0

pan0

---

### Post by RedSingularity on 2009-05-04
You got nothing from the other command either??!!??  Would you consider reinstalling?  Its sounds to me as if you have alot of essential scripts missing from the system.

---

### Post by tmos22 on 2009-05-04
I think i might have to, but it was all working perfectly earlier for about 6 hours

---

### Post by RedSingularity on 2009-05-04
Maybe you messed up some essential files while running a command as super user.

---

### Post by tmos22 on 2009-05-05
I dont think i did anything , must have been install, the only thing that i can think of is it happened just after i installed the "cheese" webcam app, so maybe it could be that??

---

### Post by TheNosh on 2009-05-05
just to clarify, thats an L at the start of lspci, just making sure you're not mistaking it for an I

---

### Post by RedSingularity on 2009-05-05
> **tmos22 said:**
> I dont think i did anything , must have been install, the only thing that i can think of is it happened just after i installed the "cheese" webcam app, so maybe it could be that??


Na that wouldn't mess with any of your scripts that come with the install.

---

### Post by tmos22 on 2009-05-05
Wow i feel like a noob, i thought it was an I

heres the log


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
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M G (rev a1)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by RedSingularity on 2009-05-05
LOL there was the problem!  

Follow [this](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/) guide.

---

### Post by tmos22 on 2009-05-05
Lol, thanks man, ill report back after i try the guide :D Will be in a few hours, need some sleep, its 5.40am here and havnt slept yet!

---

### Post by tmos22 on 2009-05-05
That guide got it working again, hopefully it will stay connected now , cheers for all the help mate

---

### Post by RedSingularity on 2009-05-05
No problem:)

---

