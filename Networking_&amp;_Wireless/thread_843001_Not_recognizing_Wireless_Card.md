---
title: "Not recognizing Wireless Card"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by Pu1se on 2008-06-27
Hi, this is my first post. I just installed Kubuntu not to long ago and I'm trying to get my wireless card to work. I have the appropriate drivers for my card too. But when I do sudo lshw -C network and I get this.

 *-network UNCLAIMED
       description: Ethernet controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 12
       serial: 00:03:25:2a:93:d8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.69 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s


and as you see my wireless card doesn't list the full product name. This notebook is an Alienware Aurora M9700 and the wireless card is a Realtek RTL8185 ABG. So if anyone could help me that would be great. Because I have no idea how to get it to recognize the card name because when I install the drivers it says no hardware for those drivers. I would appreciate any help. Thanks in advance.

---

### Post by Pu1se on 2008-06-28
**bump**

---

### Post by scoopyb on 2008-06-29
Hi, I have a problem that is very similar to that, let's hope someone can help us! I posted a reply here in forums some time ago but it was in the archive section, eh =)
So here is my previous entry, now in a better place:

Hi,

I have a thinkpad t41 and I'd like to get my wireless working too. Problem is, since my laptop is bought used, I don't know what wireless card I have (I haven't installed windows at all, so that doesn't help either). I quess I have one since there's a MAC address for 802.11b in the bottom.

I modified the blacklist-file but it didn't help and the "sudo lshw -C network" -command only lists my wired ethernet controller. I also tried "lspci" that I found from a guide, but it didn't find any wireless device either.

I found this list from the support pages, I suppose mine should be one of those.
# Intel 802.11b wireless LAN on selected models
# ThinkPad High Rate 802.11a/b/g Wireless on selected models
# Cisco Aironet Wireless 802.11b on selected models

Any ideas for this problem?

-scoopyb

--------------


Since then I did what was suggested, I opened the case and looked for the chipset. It should be Intel and based on that I can get the drivers and it should be supported by NDISwrapper.

So if someone knows any tricks how to make my ubuntu see the card, I'd be very thankful.

-scoopyb

---

### Post by buccaneere on 2008-06-29
> **scoopyb said:**
>  I don't know what wireless card I have 

That's the first most important thing in diagnosing, I think...

Bring up the terminal, and enter:
> lspci

That will tell you the chipset for the wireless card...

If the wireless card doesn't come up, enter lsusb (pray that that's NOT the case).

---

### Post by scoopyb on 2008-06-29
Thanks for the reply buccaneere.

I have tried lshw and lspci but it seems nothing finds the wireless card. I was then given advice to open up the case of my laptop to manually check the chipset. I did it and found out that it is Intel. I then checked IBM's site and found that the card should be either Intel 2100 3B or 2200 BG.

And I still have no idea what is the exact model of my laptop (other than T41) =(

---

### Post by jualin on 2008-06-29
When you type lspci in the terminal, what do you get as a result?

---

### Post by Pu1se on 2008-06-29
Okay, I didn't do anything that I know of but when I booted up my system today it finally recognized my wireless card. But my new problem is that it doesn't detect any wireless access points in the area. So does this have to do with software or my card?

---

### Post by scoopyb on 2008-06-30
> **jualin said:**
> When you type lspci in the terminal, what do you get as a result?

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)

---

### Post by jualin on 2008-06-30
> **scoopyb said:**
> 00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)

From what I am looking at I don't thing you have a wireless card, maybe someone more experienced might confirm it.

---

### Post by jualin on 2008-06-30
Scoopyb what are the results of > lshw? 
This will give us more information to see if you have a wireless card

---

### Post by scoopyb on 2008-06-30
> **jualin said:**
> From what I am looking at I don't thing you have a wireless card, maybe someone more experienced might confirm it.
> **scoopyb said:**
> I quess I have one since there's a MAC address for 802.11b in the bottom.

And that's the problem I'm having here, I should have that wireless but it cannot be found =(



> **jualin said:**
> Scoopyb what are the results of lshw? 
This will give us more information to see if you have a wireless card

The output of "sudo lshw -C network" (which apparently lists only network hardware) is:

  *-network
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:5f:9b:bf
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=N/A ip=10.125.0.61 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s





And btw, what was that site where you could paste your long outputs etc?

---

### Post by jvalec on 2008-07-02
I have the same problem with my IBM T41. What is weird is that wireless connection was working perfectly with Ubuntu v.7.10 and when I installed v.8.04 it is not recognizing the wireless card.
This is the output of command: lshw  
*-network:1
                description: Network controller
                product: Cisco Aironet Wireless 802.11b
                vendor: AIRONET Wireless Communications
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=airo latency=64 maxlatency=4 mingnt=4

what do i need to do to make it work?
Thanks
jv

---

### Post by jualin on 2008-07-02
Do you have one of the blacklisted wireless card such as RTL8187?

---

### Post by alb8735 on 2008-07-02
I have a similar problem to many of the other posters here.  I have a Gateway T 1616 laptop with a 6008038R - Integrated Realtek 802.11b/g Wireless Networking (CRU/EURP) wireless card.  I have Ubuntu 8.04 LTS installed on it.  It seems to not recognize my wireless card at all.  
When I type in lspci, I get
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

which appears to have no mention of a wireless device.
When I type in lshw -C network, I get

WARNING: you should run this program as super-user.
  *-network              
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:4f:b9:94
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=140.209.121.40 latency=0 module=r8169 multicast=yes

which also has no mention of a wireless device.  I would appreciate any suggestions.
thanks.

---

### Post by jualin on 2008-07-02
Try this [page]("http://wireless.kernel.org/en/users/Download")If you have one of those wireless cards they can be enable by using the correct drivers found on the page. Hope it helps!

---

### Post by jvalec on 2008-07-02
Thanks Jualin, but at least for me it is too technical.

What I don't understand is why my wireless connection worked with v.7.10 without any additional configuration and now with v.8.04, supposedly more robust, etc, it doesn't work. It doesn't make sense.

Thanks
jv

---

### Post by jualin on 2008-07-02
Ok, 8.04 blacklisted some drivers because they were having problem with them but you can activate most of them at your own risk. If you have a Realtek wireless card disabling the blacklist will make them work most the time. Run this in the terminal and tell me how it goes. > sudo modprobe r818x
sudo modprobe r8187
[This]("http://ubuntuforums.org/showthread.php?t=684495") sticky talks about it with more detail, and explains how to make that command work everytime the computer boots up if this solution fixes your problem.

---

### Post by alb8735 on 2008-07-02
I tried both of the things you mentioned and neither worked for me.  There is still no recognition of my wireless device.  When I try the sudo modeprobe r818x I get the message FATAL: Module r818x not found.

---

### Post by jvalec on 2008-07-02
Jualin - My network card is "Cisco Aironet Wireless 802.11b".

should I try the same commands:
sudo modprobe r818x
sudo modprobe r8187

thanks
jv

---

### Post by jualin on 2008-07-02
those commands only work with Realtek Wireless chipsets, so unless you have that you shouldn't try them. The first step is make sure the exact model of your wireless card so you can make a thread more specific so that someone can help you. To find out the model of your wireless card please type > lspci
lshw -C networkand copy and paste the results. You can also try the suggested solution on [this thread]("http://ph.ubuntuforums.com/showpost.php?p=4797200&postcount=21") which explains how to enable the modules for most Cisco wireless cards, which says to type > sudo modprobe padlock_aes
sudo modprobe geode_aes hope this helps!

---

### Post by jvalec on 2008-07-03
Jualin - these are the results of the commands you suggested to execute.
Many thanks for your support.

jvalec@jvalec-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b

jvalec@jvalec-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:2f:2a:89
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A ip=192.168.1.104 latency=64 mingnt=255 module=e1000 multicast=yes
  *-network:1
       description: Network controller
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=airo latency=64 maxlatency=4 mingnt=4

jvalec@jvalec-laptop:~$ sudo modprobe padlock_aes
[sudo] password for jvalec: 
FATAL: Error inserting padlock_aes (/lib/modules/2.6.24-16-generic/kernel/drivers/crypto/padlock-aes.ko): No such device

jvalec@jvalec-laptop:~$ sudo modprobe geode_aes

---

### Post by chili555 on 2008-07-03
I believe the correct solution is to *sudo gedit /etc/modprobe.d/blacklist* and add two lines:```
blacklist geode-aes
blacklist padlock-aes
```Proofread, save and close gedit. Reboot and detach the ethernet cable and see if your wireless works.

---

