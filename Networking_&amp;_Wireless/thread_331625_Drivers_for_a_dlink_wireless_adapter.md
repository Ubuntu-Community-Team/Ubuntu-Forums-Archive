---
title: "Drivers for a dlink wireless adapter"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by gagnon6 on 2007-01-04
Hi guys, I'm new to Ubuntu and Linux in general. I'm trying to get my WDA-2320 D-Link wireless adapter to work. I was wondering if anyone knew where I could get some drivers for it....Thanks

---

### Post by Floppyjoe on 2007-01-04
Can you enter the following into the terminal and post the results?
```
lspci
iwconfig
```

---

### Post by gagnon6 on 2007-01-04
Sorry for the total noobness but where do I go to enter that code you gave me?

---

### Post by Floppyjoe on 2007-01-04
Applications/accessories/terminal

Enter one command at a time.

---

### Post by gagnon6 on 2007-01-05
Here are the results you wanted.

dartanian@dartanian-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)
02:09.0 Ethernet controller: Winbond Electronics Corp W89C940
02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
02:0b.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
02:0c.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
dartanian@dartanian-desktop:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"admin"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

---

### Post by tturrisi on 2007-01-05
Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

Your dlink adapter has an Atheros chipset, which means you need the madwifi driver.  This driver is included in the linux-restricted-modules package in Ubuntu.  To install the package using Synaptic:
1. start Synaptic
2. go to Settings > Repositories
3. enable the multi-universe repositories (put a check next to them)
4. click the OK button.
5. click tne Reload button.
6. click Search button
7. search for linux-restricted-modules
8. install the linux-restricted-modules that match your kernel.
9. reboot

to find out what kernel you have type this command in a terminal:
uname -r

---

### Post by gagnon6 on 2007-01-05
Thanks so much I did what you said and it works perfectly. I appreciate the help. :)

---

### Post by YoungCthulhu on 2007-02-07
Thanks Tturrisi too,

I also am a Linux newbie. I have been getting by installing a driver for my D-Link 520 from [www.ralink.com](www.ralink.com) manually and did not know about repositories or the power of Synaptic package manager till I read your post at work with interest, printed it out and came home and tried it.  It works fine! :) 

I am running a slow old P3 and have recently changed to the xubuntu desktop in an effort to lighten up and make it go faster.  Using 386 Ubuntu + Gnome desktop my system went slower than it does on Win2000 (I run a dual boot so I can load up my Toshiba Gigabeat  :( ).  I also installed a 686 kernel as advised on another thread but found that the Ra-link driver no longer worked.  Now it does using the madwifi driver that was available all along in the Linux restricted modules.

Thankyou for the help!

---

