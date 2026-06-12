---
title: "Wireless disconnect after a while using Ndiswrapper"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by ShaiI769 on 2008-08-16
Hi There,
***Note: **I'm using ubuntu hardy with a Lenovo 300 N200 laptop. My network card is Intel 4965AGN. It works super-fine when I dual-boot with vista. no disconnections, slow connection or anything.*

After having an extremely slow wifi connection in my ubuntu, I started using Ndiswrapper. I installed the windows drivers using ndisgtk and my connection is pretty fast. problem, as it seems, was solved.

However, since then, I'm experiencing frequent disconnections of the internet. In the past I had to REBOOT my machine in order for it to connect again. Now, everytime I need to reconnect i'm using the following script, which I found here in the forums, that I activate from the GNOME panel:

> 
iwconfig wlan0 mode managed key open [MAC_ADDRESS] essid [ESSID]
dhclient wlan0


It "restrats" my network connection to normal, until the next disconnection, with the following output:

> 
There is already a pid file /var/run/dhclient.pid with pid 7134
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:e8:9c:48:d5
Sending on   LPF/wlan0/00:13:e8:9c:48:d5
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.4 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.4 from 192.168.0.1
bound to 192.168.0.4 -- renewal in 1236760 seconds.


(Note: ifup and ifdown works fine too)

However, this is very annoying because it happens every few hours. Sometimes even every 30 minutes or less, when I'm running aMule in the background.

I hate it that my wireless connection is not functioning. I know there are worse problems but I'm sick of having my downloads stop and my firefox failing all the time. I love Ubuntu but in windows (I dual-boot), I'm not having a single problem with my wireless connection.

I'm struggling with this problem for a month now, googled for days, searched in the forums here for people with the same problem as well, and no solution.

I would really appreciate any help regarding my wireless connection hanging up all the time. I really can't use my laptop like this.

Sorry for the long post and thanks in advance.

Shai

---

### Post by ShaiI769 on 2008-08-17
Bump

---

### Post by amele@carolina.rr.com on 2008-08-17
I am experiencing similar symptoms, however my wireless connection typically only lasts 5 to 15 minutes.  I am using the Netgear WNDA3100 wireless card and a Netgear WNDR3300 router.  I followed the tutuorial at [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) in creating an interfaces file as follows:

```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <my-ssid-here>
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <my-key-here>

```

I have been restarting the network with "sudo /etc/init.d/networking restart" rather than using the method mentioned by the poster above.  That results in the following message (and successful, albeit short-lived, connectivity):

```

Listening on LPF/wlan0/00:1f:33:e5:e8:1f
Sending on   LPF/wlan0/00:1f:33:e5:e8:1f
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
ioctl[SIOCSIWPMKSA]: Invalid argument
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072

```

In other random information, the router continues to show the affected machine as connected even when the connection is not working.

Hopefully someone has an excellent tip that will help us both!

---

### Post by ShaiI769 on 2008-08-19
Bump

---

### Post by ShaiI769 on 2008-08-20
Bump.

---

### Post by ShaiI769 on 2008-08-21
Bump.

Using dmesg I get the following lines regarding ndiswrapper and wlan0:
```

[   38.052577] ndiswrapper (NdisWriteErrorLogEntry:191): log: 40001B7C, count: 2, return_address: f8b915d2
[   38.052632] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x56524457
[   38.052686] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xdd
[   38.052763] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   38.074765] ndiswrapper: using IRQ 17
[   38.294812] wlan0: ethernet device 00:13:e8:9c:48:d5 using NDIS driver: netw4x32, version: 0x1000b, NDIS version: 0x501, vendor: 'Intel(R) Wireless WiFi Link 4965AG Driver', 8086:4230.5.conf
[   38.294875] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

```

Please help. I'm really desperate. I spend days trying to figure this out but nothing is working.
:(

---

### Post by tsali on 2008-10-28
I need help with this as well...

Connected via ndiswrapper

WPA security.

I connects but drops the connection every 3 minutes - exactly every three minutes.

Makes Ubuntu unusable...I'm having to write this from Vista

---

### Post by tsali on 2008-10-29
Bump

I should mention I'm using a Linksys WUSB600N wireless usb adapter to connect to a Linksys router via WPA

---

### Post by hughc1 on 2008-10-29
I'm experiencing the same problem running 64 AMD.  The ip address goes bad and "dhclient wlan0" will get it started again.  This is a pain.
Adding this info for help on troubleshooting.

Atheros 5007eg card.
My system

Linux Lion64 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64 GNU/Linux
Ubuntu

It worked perfectly for a while.
Now the software link just goes away.
It comes back when rebooted.
It comes back after hibernation.
Signal strength is still 89% but there is no wireless connection.
Here is the log...


Oct 15 13:20:41 Lion64 NetworkManager: <info>  Deactivating device eth1. 
Oct 15 13:20:41 Lion64 NetworkManager: <info>  eth1: Device is fully-supported using driver 'forcedeth'.  
Oct 15 13:20:41 Lion64 NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 15 13:20:41 Lion64 NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 15 13:20:41 Lion64 NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth1'. 
Oct 15 13:20:41 Lion64 NetworkManager: <info>  Deactivating device eth1. 
Oct 15 13:20:42 Lion64 ntpdate[10168]: adjust time server 91.189.94.4 offset -0.021887 sec
Oct 15 13:20:43 Lion64 ntpdate[10190]: adjust time server 91.189.94.4 offset -0.021367 sec
Oct 15 13:23:27 Lion64 avahi-daemon[5153]: Withdrawing address record for 192.168.15.8 on wlan0.
Oct 15 13:23:27 Lion64 avahi-daemon[5153]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.15.8.
Oct 15 13:23:27 Lion64 avahi-daemon[5153]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 15 13:23:27 Lion64 avahi-autoipd(wlan0)[10404]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 15 13:23:27 Lion64 avahi-autoipd(wlan0)[10404]: Successfully called chroot().
Oct 15 13:23:27 Lion64 avahi-autoipd(wlan0)[10404]: Successfully dropped root privileges.
Oct 15 13:23:27 Lion64 avahi-autoipd(wlan0)[10404]: Starting with address 169.254.1.219
Oct 15 13:23:33 Lion64 avahi-autoipd(wlan0)[10404]: Callout BIND, address 169.254.1.219 on interface wlan0

This is ifconfig when wireless is working

eth1      Link encap:Ethernet  HWaddr 00:1b:24:f8:7e:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25058 (24.4 KB)  TX bytes:25058 (24.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1E-4C-A2-7C-F1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:897 errors:0 dropped:0 overruns:0 frame:60
          TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:306661 (299.4 KB)  TX bytes:74041 (72.3 KB)
          Interrupt:19 

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:a2:7c:f1  
          inet addr:192.168.15.4  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fea2:7cf1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:459650 (448.8 KB)  TX bytes:65257 (63.7 KB)

I've been poking around and found a comment that suggests blacklisting ath_pci.  That is now blacklisted.

hughc@Lion64:~$ lsmod | grep ath 
ath_rate_sample        17152  1 
ath_pci               250176  0 
wlan                  254112  4 wlan_scan_sta,ath_rate_sample,ath_pci 
ath_hal               333200  3 ath_rate_sample,ath_pci 


This is ifconfig when  wireless fails

eth1      Link encap:Ethernet  HWaddr 00:1b:24:f8:7e:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19800 (19.3 KB)  TX bytes:19800 (19.3 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1E-4C-A2-7C-F1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12929 errors:0 dropped:0 overruns:0 frame:973
          TX packets:5823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:5758138 (5.4 MB)  TX bytes:1211842 (1.1 MB)
          Interrupt:19 

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:a2:7c:f1  
          inet6 addr: fe80::21e:4cff:fea2:7cf1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9903832 (9.4 MB)  TX bytes:1076952 (1.0 MB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1e:4c:a2:7c:f1  
          inet addr:169.254.1.219  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

Oct 26
Played with /etc/modules.d/blacklist.
	Blacklist didn't do what I expected.

Played with /etc/modules
	Putting an # in the line with ath_pci did stop it from loading.
	Removed duplicate lines.
	Will monitor.
	Well, that wasn't it!
	
run sudo dhclient wlan0   brings the link back!

---

### Post by neil_aky on 2008-10-31
Have you tried blacklisting the Linux drivers?

---

### Post by mizunoX on 2008-11-05
> **tsali said:**
> Bump

I should mention I'm using a Linksys WUSB600N wireless usb adapter to connect to a Linksys router via WPA


See my post about the WUSB600N here:
[]("http://ubuntuforums.org/showthread.php?p=6112069#post6112069")

Basically the WUSB600N is known to be a problem with ndiswrapper.
You can compile a driver from source and load it with the instructions in the post.  It's been working great for me.

---

### Post by nickinckin on 2008-11-05
I have the same problem. Sometimes the wlan disconnects. I need to disconnect the usb wireless key and to restart networking to have the wlan up again.

I'm using amule and it happens few minutes after i start amule. I tryed with amuled and with the classic amule. The version of amule is amule-adunanza 3.14b3, based on amule 2.2.2.
Now i installed the original amule 2.2.2 and the situation is the same, the network disconnects. Now i will try with mlDonkey. See you.

---

### Post by nickinckin on 2008-11-08
> **nickinckin said:**
> I have the same problem. Sometimes the wlan disconnects. I need to disconnect the usb wireless key and to restart networking to have the wlan up again.

I'm using amule and it happens few minutes after i start amule. I tryed with amuled and with the classic amule. The version of amule is amule-adunanza 3.14b3, based on amule 2.2.2.
Now i installed the original amule 2.2.2 and the situation is the same, the network disconnects. Now i will try with mlDonkey. See you.

The test with mlDonkey failed, also with mldonkey running the connection drops.

I use a wlan with ndiswrapper, the network provider is fastweb, i'm in italy. Perhaps is a problem of the network, but the emule on windows is running perfectly. I will try amule on windows.

---

### Post by nickinckin on 2008-11-08
> **nickinckin said:**
> The test with mlDonkey failed, also with mldonkey running the connection drops.

I use a wlan with ndiswrapper, the network provider is fastweb, i'm in italy. Perhaps is a problem of the network, but the emule on windows is running perfectly. I will try amule on windows.
I tryed with wine emule. The connections dropped again, but after more time.

---

### Post by nickinckin on 2008-11-09
> **nickinckin said:**
> I tryed with wine emule. The connections dropped again, but after more time.
I moved the wireless key nearest to the access point, and sometime using emule with wine, the wlan never disconnects. So i suggest to use the wined emule instead of amule.

---

### Post by Digger78 on 2008-11-09
Non of you mention which version of ndiswrapper your using.

compiling version 1.52 from source fixed it for me.

---

### Post by nickinckin on 2008-11-11
> **Digger78 said:**
> Non of you mention which version of ndiswrapper your using.

compiling version 1.52 from source fixed it for me.
Excuse me, i used the latest version of ndiswrapper the 1.53. But now i changed my wireless key. Now i'm using a wireless key with a ralink chipset an edimax ew7318ug. That has manifacturer support for linux. Now i'm connecting with it and using amule 2.2.2 and the connection never drops. (i deleted the ubuntu .ko modules in /lib/modules that don't work, and installed the latest driver from ralink).

---

