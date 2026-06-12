---
title: "[SOLVED] Wireless driver Enabled but Not In Use"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by lost09 on 2008-07-18
Upon installing the most recent set of updates for Hardy, my wireless no longer functions. According to Hardware Drivers, support for my Atheros 802.11 (?) wireless card driver is enabled, but _not in use_. Does anyone know why? Or, especially, how to fix this?

Many thanks,
l

---

### Post by lost09 on 2008-07-19
I tried disabling and re-enabling it, to no avail. The linux person at my university suspects the problem is in /sbin, but I've no idea why/what to look for.

---

### Post by lost09 on 2008-07-20
The above mentioned linux person asked for the output of ifconfig. I don't know why, but here it is:

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:20:38:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64300 (62.7 KB)  TX bytes:64300 (62.7 KB)

Can anyone tell me what to get out of this?

Thanks,
l

---

### Post by Tigin on 2008-07-20
what is the model of your card ?

---

### Post by MrFSL on 2008-07-20
it sounds like it is failing loading the "driver" (module). Some error output would be helpful - Disable then re-enable again then post the output of dmesg

> dmesg | tail

---

### Post by lost09 on 2008-07-22
"dmesg | tail" yields the following:

[   39.536680] Bluetooth: HCI device and connection manager initialized
[   39.536685] Bluetooth: HCI socket layer initialized
[   39.602361] Bluetooth: L2CAP ver 2.9
[   39.602369] Bluetooth: L2CAP socket layer initialized
[   39.723671] Bluetooth: RFCOMM socket layer initialized
[   39.723694] Bluetooth: RFCOMM TTY layer initialized
[   39.723696] Bluetooth: RFCOMM ver 1.8
[   50.890815] NET: Registered protocol family 10
[   50.891454] lo: Disabled Privacy Extensions
[   50.892147] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by lost09 on 2008-07-22
There were various "disabled", "failed", etc notices throughout the full output of "dmesg". I can post the entirety of it if necessary. 

Thanks, 
l

---

### Post by mickeyree on 2008-07-22
> **lost09 said:**
> Upon installing the most recent set of updates for Hardy, my wireless no longer functions. According to Hardware Drivers, support for my Atheros 802.11 (?) wireless card driver is enabled, but _not in use_. Does anyone know why? Or, especially, how to fix this?

Many thanks,
l

I have had the exact same experience after allowing Update Mgr to load and install updates today. Where the wireless icon showed in the upper right it does not now. When I originally loaded Ubuntu it flawlessly loaded and connected. This is discouraging. Was there something in the past week that has caused this?

---

### Post by mickeyree on 2008-07-22
> **mickeyree said:**
> I have had the exact same experience after allowing Update Mgr to load and install updates today. Where the wireless icon showed in the upper right it does not now. When I originally loaded Ubuntu it flawlessly loaded and connected. This is discouraging. Was there something in the past week that has caused this?
I ran this and received this result. It looks like it recognizes the wireless but it is "UNCLAIMED" whatever that means. I am able to connect on the hard line and wireless light is on but the little icon that used to appear on the top right of the window is gone since the updates I downloaded and instaaled earlier today. If anyone can help me figure this out I would be grateful:

-Laptop:~$ sudo lshw -C network
[sudo] password for harold: 
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:d9:e0:ae
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.95 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

---

### Post by lost09 on 2008-07-23
Something in the past week *may* have indeed been responsible, but I think it's more likely caused by the updates, since the wireless functioned until the most recent (as of a few days ago) batch was installed.

---

### Post by tigerplug on 2008-07-23
Would it be possible that there is a conflict with another driver?

Maybe try blacklist other drivers?

---

### Post by lost09 on 2008-07-23
"Blacklist"... may I request elaboration? Also, I don't know how to check for driver conflicts (I'm still not very good at this).

Thanks,
l

---

### Post by Kindrel on 2008-07-23
That is the exact same thing that's happened to me, and I'm hoping someone can help me.  I have never seen anything like this.  

It is indeed disappointing.  At least I'm not alone.

---

### Post by lost09 on 2008-07-23
Are updates and the like stored in any specific location? I'm wondering if I could perhaps find the updates, locate which one deals with wireless LAN cards, and investigate/delete it. 

Thanks,
l

---

### Post by lost09 on 2008-07-24
Kindrel, I'm communicating with the Linux guru at my university. Response time is rather poor, but I'll upload any useful tidbits here. 

Meantime, I'm open for suggestions from the community. Anyone? Anyone?

Thanks,
l

---

### Post by lost09 on 2008-07-25
No one? *sigh*

---

### Post by lost09 on 2008-07-25
The person with whome I have spoken suspects that "ifconfig" is not revealing certain things in "/sbin." She mentioned something about prefixing the command so as to show files which are not in the path, but her explanation was less than clear. Can someone please shed light on this?

Thanks, 
l

---

### Post by Kindrel on 2008-07-25
I'm still trying to figure this thing out as well.  I wish someone somewhere has SOME answer.

---

### Post by eamann on 2008-07-26
Hi all!

Just to say that I too am in the same position: wireless was working fine and then overnight it no longer works! I have a Dell Inspiron 1520 laptop and Ubuntu 8.04

The wireless icon that looks like a stairway in the top right-hand corner has been replaced with an icon of two monitors.

I cannot connect either with an Ethernet cable.

But in WinXP I have no problems. For what it is worth, here is the print-out of ifconfig and iwconfig.

Let's hope that one of the experienced members of the community can help us!

Eamann

 ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1c:23:b4:ee:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:1c:23:b4:ee:06  
          inet addr:169.254.6.85  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1772 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1772 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:88904 (86.8 KB)  TX bytes:88904 (86.8 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:36:bc:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1c:bf:36:bc:bc  
          inet addr:169.254.8.217  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-36-BC-BC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

eamann@eamann-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:""  Nickname:"" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by lost09 on 2008-07-26
Did you experience this problem after installing updates, or did something else cause this?

---

### Post by eamann on 2008-07-27
Hi all!

I spent a few hours surfing around the forums and I found a solution to my problem. I hope it will work for you too! Not being a techie, I do not know how this solution works nor what it does. Simply type in a terminal:

echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces

Hope it helps!

---

### Post by Kindrel on 2008-07-27
Hey Lost,

My wireless problem is now fixed.  I want to thank you for offering help, though I don't know how I fixed it.  It was with the help of kind people on these forums and craziness that it alll worked out.  

Thank you!  And good luck!

---

### Post by lost09 on 2008-07-27
Glad to hear it! Can you offer any hints as to how you fixed it, or at least your terminal entries? I'm going to try the solution offered by eamann, but I'd still like a better grasp of what's going on. 

Thanks, 
l

---

### Post by lost09 on 2008-07-27
eamann, may I request the output of "ifconfig"? Now that your problem is resolved, I'd like to compare the output with that of my  computer. I don't expect to gain anything from it, but I cling to a slight hope that doing so will be mildly instructive. 

Thanks, 
l

---

### Post by lost09 on 2008-07-27
Sad to say, eamann's command didn't work. :(

---

### Post by eamann on 2008-07-28
Hi Lost 09,

Sorry that my command did not help.

Here's the output of my ifconfig now that the wifi is working:

eamann@eamann-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:b4:ee:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:136386 (133.1 KB)  TX bytes:136386 (133.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:36:bc:bc  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe36:bcbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7800 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15957726 (15.2 MB)  TX bytes:943289 (921.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-36-BC-BC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I hope that that helps.

Best wishes,

Eamann

---

### Post by lost09 on 2008-07-28
I greatly appreciate the output, but I'm happy to say it wasn't necessary after all. I finally cornered the resident linux guru and managed to solve the problem. Apparently, the driver was misplaced/corrupted/whatever during the installation of the aforementioned updates. In the event that anyone else has this problem, here's basically what fixed it (note: requires wired connection):

1) Go to Hardware Drivers and disable the driver for your wireless card (if it isn't disabled already).

2) Restart the computer.

3) Ensure everything is up-to-date.

4) Enter ```
sudo modprobe ath_pci
``` at a shell prompt (note: "ath_pci" pertains to my Atheros card. If you're using a different card, you'll obviously need to substitute the name of your driver).

I believe this is the sum total of what worked (we spent an hour trying various things, so I may have forgotten something important). 

Thanks to everyone who contributed,
l

---

