---
title: "Windows wireless driver"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by gabway on 2008-10-06
Hi,

I'm new to the whole Linux thing and I have a small problem. I installed Ubuntu (Hardy Heron) on a PC and I installed the driver for my wireless card using Nsdiswrapper. I had my card up and running but when I turned off the computer and tried to reboot I got a black screen with fsck 1.40.8 and a list of things ending by starting bluetooth and a cursor.

What should I do ?

---

### Post by willca on 2008-10-07
Could be a lot of things. 

1- Trying to reboot that computer again, did it do the exact same thing?
2- Can you paste what were the last few lines, especially the part with the fsck stuff.

You might want to try to load your livecd and see if it loads up just fine. If it does, I would try to do the following (if indeed this was was hard drive related).

sudo fsck /dev/hda2 
or 
sudo fsck /dev/sda2

Not sure how your computer is setup but its likely that your root partition is hda2 or sda2. Otherwise, just put the right one and run it.

---

### Post by gabway on 2008-10-08
Sorry for the late reply,

I was doing everything wrong ! I didn't need to use ndiswrapper. I reinstalled Ubuntu and plugged my wireless card and everything was fine. After reboot the card would not work again ! Here are a few responses from different command lines in the terminal.

gabway@Big-Bertha:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:0a:e6:2f:41:6d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:06:25:1a:17:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=1.101.4-84 ip=192.168.0.103 wireless=IEEE 802.11b
gabway@Big-Bertha:~$ 






gabway@Big-Bertha:~$ lsusb
Bus 004 Device 003: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter
Bus 001 Device 001: ID 0000:0000  






gabway@Big-Bertha:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Plogue sur le fuzz"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:11:4F:AE:B7   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality=92/100  Signal level=92/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



gabway@Big-Bertha:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e6:2f:41:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20500 (20.0 KB)  TX bytes:20500 (20.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:06:25:1a:17:3f  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:25ff:fe1a:173f/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:2050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:699331 (682.9 KB)  TX bytes:12152 (11.8 KB)




Hope you can help me !

---

