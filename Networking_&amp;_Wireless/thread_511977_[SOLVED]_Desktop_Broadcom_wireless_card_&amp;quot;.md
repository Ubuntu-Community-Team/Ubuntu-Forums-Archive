---
title: "[SOLVED] Desktop Broadcom wireless card &amp;quot;disabled&amp;quot;"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by dylanologist on 2007-07-28
I know that plenty of threads exist regarding these tricky Broadcom wireless cards, but I'm a complete Newb to Linux, and the amount of info is somewhat overwhelming, expecially when I don't know most of the command line stuff.

I have a Celron 600mhz cpu w/ 256mb of RAM.  Installed Ubuntu just yesterday without problems except I can't connect to my wireless network.  I disabled both the firewall features and the WPA security on my wireless router but still no luck.

I believe the problem is related to the fact that my wireless network is listed as "DISABLED" when I use the prompt lshw.  I also tried installing ndiswrapper but didn't get anywhere.  I'm probably making some pretty basic mistakes because I have no previous knowledge of Linux.  I would like to learn as I go, but without an internet connection on that computer it's going to be pretty difficult.

Below are some results from some command line prompts I tried.  Their probably a bit random, but if somebody could at least give me an idea of what my problem might be I would greatly appreciate it.  I assume that "*-network:0 DISABLED" (just below) is a clear indication that something is wrong, but I don't know how to even diagnose the problem let alone fix it.

Please help me and help my computer.  Without an internet connection that baby's headed for the recycling plant.



brent@linux-desktop:~$ lshw
*-network:0 DISABLED
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: d
                bus info: pci@01:0d.0
                logical name: eth1
                version: 03
                serial: 00:0f:66:74:5d:24
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:f4112000-f4113fff irq:9



brent@linux-desktop:~$ lspci
01:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)



brent@linux-desktop:~$ lsmod
bcm43xx               125332  0



brent@linux-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



brent@linux-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:BA:23:E1:A2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x3400 

eth0:avah Link encap:Ethernet  HWaddr 00:50:BA:23:E1:A2  
          inet addr:169.254.8.220  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x3400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1432 (1.3 KiB)  TX bytes:1432 (1.3 KiB)



brent@linux-desktop:~$ ndiswrapper
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found



brent@linux-desktop:~$ sudo apt-get install ndiswrapper-common
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common

---

### Post by noob12 on 2007-07-28
I'd suggest this post  [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) 

Can you hook up wired for awhile?  Almost anything you do is going to require downloading.  

You can use another host to download and a USB flash drive to transfer packages in a pinch.

---

### Post by dylanologist on 2007-07-28
Yes, I do have access to another computer with internet access (on the network I'm trying to connect to with my Linux machine), and I do have a USB key for file transfers.  I'll take a look at the link you gave me - it's not a post I've seen before, but it does look relevant and I like the "EASY" moniker.  Thanks for the prompt reply.  I'll let you know if I have any luck (probably won't get at it again until tomorrow though).

---

### Post by dylanologist on 2007-07-29
Got my wireless card installed and I'm up and running on my wireless network.  Now I can get to work learning to operate in Linux, which an internet connection will make much easier.  Thanks noob12 for the great advice.  My introduction to the Linux community has been a very positive experience.

---

