---
title: "[SOLVED] Internet issues in Ubuntu 7.10"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by jonomayo on 2007-12-14
Hi

I have a dual boot windows xp/ubuntu 7.10 laptop which i am having problems with the internet connection issues with.

After a clean install in a new partition on my laptops main hard drive of Ubuntu 7.10 i tried to use the internet through the firefox web browser but it didnt work. I then rebooted into windows on the same machine and used the same internet connection (direct lan connection to a router) to search online for a fix. I then located the ipv6 issue. I disabled ipv6 through firefox and that worked however the internet did not work through other programmes such as apt get. Thinking that this must be the isuue i used the fix to globaly disable ipv6. This however did not fix the issue.

I am now clueless as to what to do and wondered if anyone here has a fix for this?

Thanks in advance 
Jonathan

P.S.
This also happened in an installation of Xubuntu on the same pc.

---

### Post by PreviousN on 2007-12-14
Posting "ifconfig" and "lspci"'s output from a terminal might help others troubleshoot your hardware.

Also, try opening a terminal and pinging google or some other site. If you get something like "no route to host" or similar, its likely a routing issue. Type this:
"route -n" into a terminal. This'll list your gatways, etc: for example, here's mine: 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

---

### Post by ishapian on 2007-12-15
Hi! I'm having identical problems. I've spent several hours today trying to fix it, but I can't make it work.

Issue:
- can't connect to the internet with 7.10 (7.04 works fine)
- firefox works if i disable ipv6 but other apps don't even if i disabled ipv6 globally ([http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/](http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/))
- at some point I was able to ping google.com, but that stopped working too

```

ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:E6:4C:70  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28161 (27.5 KB)  TX bytes:12034 (11.7 KB)
          Interrupt:11 Base address:0xc020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1008 (1008.0 b)  TX bytes:1008 (1008.0 b)


lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)


route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.2.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.2.2        0.0.0.0         UG    0      0        0 eth0

```

I'd be very grateful for any help!
Tomas

---

### Post by jonomayo on 2007-12-15
Solved!!

I changed my dns server to open dns and that solved all of my internet related problems.

Thanks for the help anyway.

---

### Post by Loan_Refi on 2007-12-18
Can you tell me how you set your DNS to open? I have the same problem and want to try what you did.

---

