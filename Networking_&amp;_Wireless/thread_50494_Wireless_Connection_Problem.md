---
title: "Wireless Connection Problem"
date: 2005-07-20
forum: Networking &amp; Wireless
---

### Post by jordanj1969 on 2005-07-20
I have a HP Pavilion zv5037wm Laptop with built-in Broadcom 802.11b/g WLAN card.  Not for the lack of trying, I can not get it to connect to my USR8054 Wireless router.  It works fine when I'm logged on under Windows XP.  I have Ubuntu with Kubuntu-Desktop installed.  Can anyone assist me?

---

### Post by skyboy on 2005-07-20
hi, copy paste your iwconfig, ifconfig and /etc/network/interfaces

---

### Post by jordanj1969 on 2005-07-20
jjordan@ubuntujj:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr (My Mac Address)
          inet addr:192.168.123.102  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fe6c:6a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:701789 (685.3 KiB)  TX bytes:107787 (105.2 KiB)
          Interrupt:19 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25123 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2264384 (2.1 MiB)  TX bytes:2264384 (2.1 MiB)

wlan0     Link encap:Ethernet  HWaddr (My Mac Address)
          inet6 addr: fe80::290:4bff:fe4c:fb38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Memory:d0204000-d0205fff

jjordan@ubuntujj:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management: off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



jjordan@ubuntujj:/etc/network$ cat interfaces | more
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface ppp0 inet ppp
provider ppp0


iface wlan0 inet dhcp
wireless-essid jordan
wireless-key (My Key)

auto wlan0

---

### Post by skyboy on 2005-07-21
obviously, you opened another post ...

---

### Post by Cyberman on 2005-08-08
This one is on google though.  :smile: 

Perhaps someone could type something up about Ubuntu/Kubuntu and setting up Broadcom 802.11 b/g wireless cards?

I found this little article on the m6811 emachine laptop for it's broadcom chipset:
[Review of the Laptop with Linux Installed](http://www.linuxquestions.org/hcl/showproduct.php?product=1734&sort=8&cat=all&page=1) 

This also may be of interest to people:
[Click here to view thread](http://ubuntuforums.org/showthread.php?t=53822&highlight=m6811) 

[IMG]http://img217.imageshack.us/img217/822/rofflewaffles8lr.jpg[/IMG]

---

