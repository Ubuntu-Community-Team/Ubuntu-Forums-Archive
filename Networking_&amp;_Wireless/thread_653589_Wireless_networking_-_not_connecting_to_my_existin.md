---
title: "Wireless networking - not connecting to my existing network at all"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by usone123 on 2007-12-30
HI, OK I just installed Ubuntu 7.10 and it seems to be working fine but after finally getting the usb network adapter installed, it won't connect to the web. It's a Belkin Wireless G network adapter F5D7050 version 3002. I tried a different belkin one that went into the motherboard but i think its defective. This usb one was fine and i used that nsidwrapper thing to get it installed and it shows that my device is installed and everything when i go to system>administration>networks but it won't connect to my network I have existing. I have a laptop separate from this computer that is on that wireless network and it connects fine. This one just will not connect and after troubleshooting its definitely a linux issue and not an issue with my linksys access point....

I have this computer hooked up to both LAN and WLAN so that I would be able to get the terminal info copied and pasted properly. My ethernet is working fine, so its just wireless......

this is what I get when I did a few commands that I saw on some of the other help files: Thanks in advance....

rae@LT-Destop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
00:11.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)
rae@LT-Destop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:07:95:C3:D1:E5
          inet addr:65.86.99.114 Bcast:255.255.255.255 Mask:255.255.255.240
          inet6 addr: fe80::207:95ff:fec3:d1e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:1284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1424334 (1.3 MB) TX bytes:180644 (176.4 KB)
          Interrupt:11 Base address:0xcc00

lo Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1408 (1.3 KB) TX bytes:1408 (1.3 KB)

rae@LT-Destop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11g ESSID:""
          Mode:Managed Channel:0 Access Point: Not-Associated
          Retry min limit:7 RTS thr:off Fragment thr=2346 B
          Link Quality:0 Signal level:0 Noise level:0
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0

rae@LT-Destop:~$ CAT /etc/network/interfaces
bash: CAT: command not found
rae@LT-Destop:~$ CAT/etc/network/interfaces
bash: CAT/etc/network/interfaces: No such file or directory
rae@LT-Destop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0
rae@LT-Destop:~$

---

