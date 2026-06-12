---
title: "Wireless card not showing up."
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by erikcw on 2006-08-28
Hi all,

I just setup Dapper, and my wireless card isn't showing up in network-admin.  However the card is showing up in the device manager.

> 
Vendor: Marvell Technology Group Ltd.
Device: 99w8335 [Libertas] 802.11b/g Wireless
Status: Status
Bus Type: PCI
Device Type: Unkown
Capabilities: Unkown


eth0 is my wired ethernet card.  How do I get this one to show up as eth1?

Thanks!
Erik

---

### Post by erikcw on 2006-08-30
I'm learning more and more.  Here is some output that may help someone help me....

ifconfig
> 
eth0      Link encap:Ethernet  HWaddr 00:13:D4:E0:F1:68  
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fee0:f168/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4841 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3692823 (3.5 MiB)  TX bytes:831437 (811.9 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:832 (832.0 b)  TX bytes:832 (832.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.223.1  Bcast:192.168.223.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.53.1  Bcast:172.16.53.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


NOTE the vmnet devices are from VMWare...

> 
$ iwconfig > iwconfig.txt
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.


dmesg - see atached .txt - output to long for forum...


How do I make Ubuntu detect eth1?
Thanks for your help!

---

### Post by Blacktalon on 2006-08-30
Ok, heres an idea.  This is how I got mine to work properly, since I use BlueTooth I have bcm43xx drivers.  You need to do is open up your terminal, type in:  sudo modprobe <driver name (for mine it would be bcm43xx)> 

then you will see the eth1, and if your wireless doesn't work straight up find your driver at [https://wiki.ubuntu.com/WifiDocs/Driver/](https://wiki.ubuntu.com/WifiDocs/Driver/)  and follow those instructions they usually work and help.

Good luck to ya.
  ~BT

---

### Post by erikcw on 2006-09-24
Hey everyone - I finally got it working!

For the sake of anyone else in my boat, here is what I did.

I followed this HowTo:
[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

I ended up having to use ndiswrapper to get my card working.  Now I have wlan0 up and running!

NOTE:  It doesn't mention this in the HowTo, but when I restarted my computer, it froze at "configuring network devices", after letting it sit for 30 minutes, I did a hard reboot and this time it started right up!

---

