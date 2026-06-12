---
title: "acer aspire 4530 wireless"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by pfeifferock on 2009-06-25
I can't seem to get my wireless to work on my acer aspire 4530 i looked into this online and it seemed like i needed to put three lines into the terminal but beyond that the directions in the threads i looked at are beyond me. Any help?
-MP

matthew@matthew-laptop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation Device [10de:075e] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)
00:09.0 SATA controller [0106]: nVidia Corporation Device [10de:0ad5] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0569] (rev a1)
00:13.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:15.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]
02:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 9100M G [10de:0844] (rev a2)
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
0b:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
matthew@matthew-laptop:~$ ishw -c Network
bash: ishw: command not found
matthew@matthew-laptop:~$ uname -m
i686
matthew@matthew-laptop:~$ ispci -nn
bash: ispci: command not found
matthew@matthew-laptop:~$

---

### Post by Divider on 2009-06-25
there is alot more than 3 commands needed. 

First you have to find out what driver is required. Then you most likely will have to NDISwrapper it if you already dont have support for it.

but try this in terminal. and repost the output.

```
iwconfig
```

---

### Post by pfeifferock on 2009-06-25
matthew@matthew-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

matthew@matthew-laptop:~$

---

### Post by TheLions on 2009-06-25
is your wirelles enabled?

Unfortunately indicator LED doesn't work you you have to enable it "on blind" if disabled.

(On my laptop LED is working only before loading X)

---

### Post by pfeifferock on 2009-06-27
um well when i right click on the wireless icon thing on the right side of my screen the box Enable Wireless is checked. 
-mp

---

### Post by TheLions on 2009-06-27
> **pfeifferock said:**
> um well when i right click on the wireless icon thing on the right side of my screen the box Enable Wireless is checked. 
-mp

i meant indicator on your laptop (you know some king of green or blue light showing that wireless is ON [ ((<o ])

---

### Post by pfeifferock on 2009-06-27
there are no leds that look like they are about wireless there is one that is a cube and it is green and it blinks occasionally. then there are 2 right next to the jack for wired internet one will blink yellow when i plug in the jack and the other will turn on green. then there are 2 icons of locks one that has a 1 inside it and the other the letter A. none of those seem like they are about wireless but idk. 
-mp

---

### Post by TheLions on 2009-06-27
> **pfeifferock said:**
> there are no leds that look like they are about wireless there is one that is a cube and it is green and it blinks occasionally. then there are 2 right next to the jack for wired internet one will blink yellow when i plug in the jack and the other will turn on green. then there are 2 icons of locks one that has a 1 inside it and the other the letter A. none of those seem like they are about wireless but idk. 
-mp

i had very similar situation, ubuntu had recognized wireless card, but it shoved that there hasn't been any wireless network around. Problem was that wlan was off. 
so try enable it, over keyboard (I think it is Fn + F2) or in BIOS (probably F2 or F10 on startup) before trying messing with drivers.

---

### Post by bichopro on 2009-06-27
same wifi working native on aspire 4220 on fresh jaunty 9.04

---

