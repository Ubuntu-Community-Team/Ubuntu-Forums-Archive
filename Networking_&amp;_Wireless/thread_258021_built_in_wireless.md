---
title: "built in wireless"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by adidaskid810 on 2006-09-15
i have a compaq presario v2000 laptop with the wireless built in...im a 100% newbie when it comes to linux and really wanting to learn.

i tried to open network settings to see how to connect to the internet and it makes me input a password for the admin login

i need the password and any and all help to connect to the internet...thanks in advance

edit: just need to know how to get the internet connected

---

### Post by NetworkGuy on 2006-09-15
The password it is looking for is the same password you sign in with.

Check it out and let us know.

---

### Post by adidaskid810 on 2006-09-15
yes that worked... now i just need to know how to get my internet connected thanks.

---

### Post by NetworkGuy on 2006-09-15
Well, you can check the wiki for wireless.  There are a lot of helpful articles in there.  

You can also get it working by posting here in the forums.  The most important thing about wireless in Linux is the chipset of the card in your laptop so....

From a terminal can you post the output from these commands.
```
lspci
``````
iwconfig
``````
ifconfig
```

These commands will tell us what chipset wireless card you have, if the drivers for this card are loaded and working, and if your laptop has an IP address.

---

### Post by adidaskid810 on 2006-09-15
im a complete newbie so when you say from a terminal to post those codes where do i go

sorry if these are stupid questions

---

### Post by NetworkGuy on 2006-09-15
I'm not on my distro right now (actualy in a training class) but click on accessories --> terminal.

This will bring up a terminal window where you can type in these commands.

---

### Post by adidaskid810 on 2006-09-15
once i get these codes is there a way to save them or copy them so when i restart into xp i can paste it here

---

### Post by NetworkGuy on 2006-09-15
You can copy and paste the output into the text editor, but unless you have something like a USB memory stick, it may be difficult to get that information moved over to XP.   Can you connect up to your wireless router with the Ethernet connection on your laptop and get to the Internet that way?

---

### Post by adidaskid810 on 2006-09-15
i can in xp but not ubuntu ill get those codes to my flashdrive and post them here for you...

---

### Post by adidaskid810 on 2006-09-15
dont know how much of this you need but here is all of it


anfge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
0000:05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:05:09.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
andrew@andrew-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"jamesgang"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

andrew@andrew-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:07:71:B8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2740 (2.6 KiB)  TX bytes:2740 (2.6 KiB)

---

### Post by NetworkGuy on 2006-09-15
Ok,

You have a Broadcom 4318 chipset

Use these following howtos to try and get that card working in ubuntu

[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

One of these two should be what you need.

---

### Post by adidaskid810 on 2006-09-15
will give them a try..thanks i will let you know how it goes

---

### Post by adidaskid810 on 2006-09-15
neither worked and i also tried a link from another users to one that worked for someone else. still not working hmmm :(

---

