---
title: "Problem connecting to Wireless Network"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by NaeturVindur on 2009-07-06
Ok, so I recently installed Ubuntu 8.04, and am having problems connecting to the internet. My computer is an Asus N90Sv with no modifications from factory settings., wireless card 802.11n+BT  It has yet to connect to the internet, and doesn't seem to recognize that I have the ability.  I have been trying to follow [Wireless trouble shooting]("https://help.ubuntu.com/8.10/internet/C/troubleshooting.html"), and it led me in a circle (I installed ndisgtk, and installed netathrx.inf from my Window's System23, and it still says "UNCLAIMED").  This is what I know (well, can think to show you, what it really means, I have no idea):
 ```
ben@ben-laptop:~$ lspci  
 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX  
 00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge  
 00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)  
 00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)  
 00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)  
 00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)  
 00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller  
 00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)  
 00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)  
 00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge  
 00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge  
 00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller  
 01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0652 (rev a1)  
 02:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)  
 ben@ben-laptop:~$ lshw -C network  
 WARNING: you should run this program as super-user.  
   *-network                
        description: Ethernet interface  
        product: 191 Gigabit Ethernet Adapter  
        vendor: Silicon Integrated Systems [SiS]  
        physical id: 4  
        bus info: pci@0000:00:04.0  
        logical name: eth0  
        version: 02  
        serial: 00:24:8c:a8:05:de  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical  
        configuration: broadcast=yes driver=sis190 driverversion=1.2 latency=0 module=sis190 multicast=yes 
   *-network UNCLAIMED  
        description: Network controller  
        product: Atheros Communications Inc.  
        vendor: Atheros Communications Inc.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        version: 01  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list  
        configuration: latency=0
```

---

### Post by NaeturVindur on 2009-07-07
Bump, seeing as I still have no idea what to do, and nothing has changed.

---

### Post by abhiroopb on 2009-07-07
Can you actually see anything happening on the network applet in the panel? Basically is your problem that the card is not detected or is that it is unable to pick up wireless signals?

Also it might be an idea to try out a newer version of ubuntu such as 9.04 as this problem may have been resolved.

---

### Post by NaeturVindur on 2009-07-07
The card is not detected/being used.  Its just an X.

I tried using 9.04, but I couldn't stand all the bugs (no audio, all the crashes...), so I thought one that was more established would be better.

---

### Post by abhiroopb on 2009-07-07
Ok fair enough. Unfortunately my knowledge on wireless cards is very limited, so you will have to wait for someone wiser to reply.

Good luck!

---

### Post by NaeturVindur on 2009-07-08
> **abhiroopb said:**
> Ok fair enough. Unfortunately my knowledge on wireless cards is very limited, so you will have to [b]wait for someone wiser to reply.[b]

Good luck!
still waiting...

(tying to get creative with my bumps)

---

### Post by NaeturVindur on 2009-07-10
So I found the problem... Apparently the driver I need is only supported by 8.10 and higher, and I have 8.04. :/

---

