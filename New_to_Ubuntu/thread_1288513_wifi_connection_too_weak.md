---
title: "wifi connection too weak"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by peterinmalaga on 2009-10-11
Hi! Below is my computer spec.
Fujitsu Siemens Amilo Li 3910
Processor Genuine Intel(R) CPU   T1600 @ 1.66GH 1662 Mhz
1MB cache.
3GB DDR2 RAM.
*18.4in screen size.
Resolution 1680 x 945 pixels.
Widescreen HD+.
*250GB SATA hard drive capacity. Partitioned C & D drives. 91.1 GB free of  146GB free on C drive: 66.8 GB free of 75.2GB on D drive.
*Multiformat dual layer DVD RW optical drive.
*Intel GMA 4500M graphics card.
Up to 1277MB graphics memory.
OS Windows Vista Home Premium, Service Pack 2 and Ubuntu Jaunty 9.04
32-bit Operating system
ADSL internet connection

I have a fairly new laptop, bought in the UK, though I live in Spain. I have installed Ubuntu on my computer from a downloaded CD (alongside Vista). I would like to move over to Ubuntu completely, when I sort out the teething problems. The Ubuntu setup seems to be fine but I have the following problems: I mention both in case they are interconnected.
1.I can access the internet via the ethernet cable but not via wifi, unless I am very close to the router. My computer is the 2nd computer in the household, so direct access via the ethernet cable is not possible most of the time. The wifi connection works fine with Vista. I should add that it appears that I have connected to the internet via wifi (icon at top right on desktop) but the intenet connection doesn't work. The internet icon (top right on desktop) shows 40% or less. This figure increases to 98% if I am very close to the router (3 feet away): then the internet connection works.
2.When I try to update the Ubuntu account or add anything to the set-up even adding a short document, I receive the message &#8220;not enough free disk space&#8221;.
I would be really grateful if you could suggest a solution.

---

### Post by swoody on 2009-10-12
Hello peterinmalaga, and welcome to the forums ):P

1) The first issue seems like it may be a driver issue. Have you looked into System>Administration>Hardware Drivers and looked for an available wireless driver? Could you also open a terminal (Applications>Accessories>Terminal) and give us the outputs of the following commands:
```
lspci
```
and
```
iwconfig
```

2) The second issue appears to be a case of a full hard disk. Do you remember offhand how much space you allocated to Ubuntu when you setup the dual-boot with Windows? For this issue can you also provide us with the output of:
```
df -h
```

---

### Post by PrePenguin on 2009-10-12
Have a similiar issue with my wifi in windows i have 100% signal strength anywhere within 100 feet of the house even outside but same locations in ubuntu even really close as upstairs shows 40% I have no driver issues and i know the hardware works .. Not sure what the issue exactly is on this one.

---

### Post by walt.smith1960 on 2009-10-12
I've had a problem with weak WiFi on an Asus Eee1005HA. Running Karmic NBR Beta.  I installed a RealTek USB network adapter in the same machine. The signal strength using the RealTek adapter was quite a bit stronger than the integral Atheros 9XXX WiFi adapter.  I installed  Linux Backports via Synaptic and that has increased signal strength indicated in Network Manager from around 40% to around 70% and signal strength is more stable. I hope this is of some help.

---

### Post by peterinmalaga on 2009-10-24
Hi Swoody, Thanks for replying. I have a strong suspicion that you know what my problem is. Here are the outputs of the 2 terminals you asked for. Sorry about the delay. Somehow I missed your reply!
 

 peter@peter-laptop:~$ lspci 
 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07) 
 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
 00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
 00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 
 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
 00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
 00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) 
 00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) 
 00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) 
 00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03) 
 00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) 
 00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) 
 00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) 
 00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
 00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03) 
 00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) 
 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03) 
 07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02) 
 peter@peter-laptop:~$  
 

 peter@peter-laptop:~$ iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 wmaster0  no wireless extensions. 
  
 wlan0     IEEE 802.11bg  ESSID:""   
           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
           Tx-Power=20 dBm    
           Retry min limit:7   RTS thr:off   Fragment thr=2352 B    
           Power Management:off 
           Link Quality:0  Signal level:0  Noise level:0 
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
  
 pan0      no wireless extensions. 
  
 peter@peter-laptop:~$  
 

 So do you have the solution? I really hope so. Thanks again for your response.
PS Ive no idea how those smilies got in my message and they disappear when I try to edit, only to reappear after again!

---

### Post by balkie99 on 2011-08-25
Hi,

My problem is similar

I have a thinkpad edge 13, intel wireless,

using iwlagn driver

i can connect

but only from a few feet from the hotspot

the signal is ok even in the other side of the flat, I used to use it

what coul i do?

thanks

---

