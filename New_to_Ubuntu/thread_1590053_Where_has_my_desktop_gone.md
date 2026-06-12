---
title: "Where has my desktop gone"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by Phil Binner on 2010-10-07
I have an Ubuntu machine on a mixed network. I started this machine on 8.10, then migrated through 9.04, 9.10 and 10.04. I did this because of connection issues on both wired and wireless connections. 

This machine started in a corner of my office connected to an old Belinea CRT monitor. In this state it got to 9.10 with no issues. At this point, however, I brought it onto my desk, where the monitor is an AG Neovo F-417 flat screen. This is important, because the big old CRT will not fit on my desk. When I connect the flat screen, however, I loose the desktop. Not the whole image, just the desktop. Top and bottom menu bars are still there, but the centre is blank.

When I continued the upgrade to 10.04 yesterday I got the desktop back, but then I lost network connection, both wired and wireless, and the keyboard and mouse became erratic. At the time I was using a wireless keyboard and mouse. These did start to work later, but not well. I had to keep moving the wireless dongle to a new USB slot.

This all seems bizarre to me. Any suggestions as to what is happening and what I can do about it would be most welcome.

I am currently back at 9.10, with no desktop, but with Wicd loaded instead of network manager, and with a wired mouse and keyboard attached. I am about to have another crack at 10.04. Wish me luck.

This is later.

I have migrated to 10.04 again. I now have the desktop back, but I have totally lost network connectivity. It doesn't seem to even recognise that there is a wireless network card, and when I try to connect to the wired connection it fails to find the IP address. When I restarted after the upgrade I had lost the wired mouse, but not the keyboard. I plugged the wireless dongle back in, and immediately got the wireless mouse. The wireless keyboard came on after a few tries. The mouse is still clunky; by this I mean that if I am passing over an open window it tends to stutter in its movement.

I came to 10.04 for 2 reasons; firstly to get the desktop back, but also because I have a DVB-T card which I think was recognised when I had a dedicated MythBuntu system, but was not recognised in Myth-TV running inside 9.10. I reasoned that the dedicated Mythbuntu system was probably 10.04 - I'm not sure.

I need to do one of the following:

a. Make the desktop work in 9.10
b. Get network connection in 10.04

Please help. Thanks.

---

### Post by Phil Binner on 2010-10-08
Further information.

The output from ifconfig and iwconfig are following. It looks as if the internal wireless network card is not recognised at all in 10.04, but it was fine in 9.10 so it's not the card at fault. The wired connection goes straight to the motherboard slot. I don't know what the card is, but the motherboard is an ASUS P4S800D-X. I can't interrogate the card to find out what it is without going back to 9.10.


bigbin@bigbin-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:53:a8:39  
          inet6 addr: fe80::213:d4ff:fe53:a839/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:27 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xe400 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
wlan0     Link encap:Ethernet  HWaddr 00:11:50:14:d7:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
bigbin@bigbin-ubuntu:~$ iwconfig
lo       no wireless extensions.
eth0   no wireless extensions.
wlan0 IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by Hippytaff on 2010-10-08
whats the output of 
 
```

lspci

```

---

### Post by Phil Binner on 2010-10-08
Output from lspci


bigbin@bigbin-ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0b.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0c.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

---

### Post by Hippytaff on 2010-10-08
RaLink RT2500 - you might need to blacklist some drivers to allow this one to work.
 
check modprobe to see if the driver is listed.

---

### Post by Phil Binner on 2010-10-08
Hiya

Thanks for the help, It's really appreciated, but I'm not that literate. Can you please explain how to blacklist drivers, how to know what drivers to blacklist, how I check modprobe, and what modprobe is.

---

### Post by Hippytaff on 2010-10-08
Before you research that, you might need to just input the WAP details - go to network manager and see if it is picking up your wireless

---

### Post by Hippytaff on 2010-10-08
This might be worth a read, then any questions drop them here and I or someone will try to help you out :-)
 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Phil Binner on 2010-10-08
OK, thanks. I did find an article on Wiki which I will read too. It's probably the same one. I can answer your other question though. I'm using Wicd rather than network manager, and it doesn't see the wireless network at all. This is the second time I've been here, however, and last time I was using network manager and it did see the wireless network, but I couldn't connect to my router, either wired or wireless. I could connect to another wireless router, however. The one I could connect to is an Orange Livebox, and the main one I could not connect to is a DrayTek Vigor 2710Vn.

I'm going to keep trying to solve this problem, because I want the experience. On the other hand, 10.04 is still clunky compared to 9.10, so ultimately the problem I'm going to want to solve is how to get the desktop back. By clunky I mean that it's slow to open and close windows, and it keeps hesitating in the middle of operations. It's not a happy bunny.

Thanks again for your help. I'm going to have to leave it now, but I'll try to look again tomorrow.

---

### Post by Hippytaff on 2010-10-08
Sounds like driver issues with the wireless - theres lost of info about nsdiwrapper (sofware used to use a windows driver in linux) and blacklisting conflicting drivers (drivers competeing to rin the device) this usually solves the problem.
 
as far as the desktop goes, I'm not sure if I;ve understood correctly, but try typing startx, might kickstart gnome/KDE

---

