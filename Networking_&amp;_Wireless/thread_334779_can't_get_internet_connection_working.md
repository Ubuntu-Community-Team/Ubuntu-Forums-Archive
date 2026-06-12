---
title: "can't get internet connection working"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by jackuk12 on 2007-01-09
Hi,

I just installed Ubuntu on my PC and everything works except my internet connection.  I have an
ethernet NIC in the machine connected to a wireless router  which worked previously with both 
windows xp and win2K, although the driver needed to be installed on win2k (adm10-100lan).

Here is what I tried by reading through posts - any suggestions you have are appreciated.

Thanks
Jack

1.system,administration,networking
the interface eth0 is active, it's set up as DHCP
I don't have any entries in DNS servers..after a bunch of fiddling around I'm not sure what was originally there

2.the system has installed the ubuntu tulip driver and recognises the NIC as a 'Linksys NC100 Network Everywhere

3.I tried the following with no luck:

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

4.tried installing ndiswrapper and the winxp driver seems to install OK (note i tried to disable the tulip one--3)
but then the interface is not visible in number 1 above:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)


5.also tried running this
sudo ifdown eth0
sudo ifup eth0

logs....

$lspci
0000:00:10.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp





$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:E8:12:CA:54
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e8ff:fe12:ca54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47033 (45.9 KiB)  TX bytes:23220 (22.6 KiB)
          Interrupt:9 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6552 (6.3 KiB)  TX bytes:6552 (6.3 KiB)



netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

---

### Post by hal10000 on 2007-01-09
I'm not sure if i understand you right, do you have a wireless card connected to your router? (may be a dumb question, but some routers can serve both wireless and wired connections.

If you have a wireless card, can you post the manufacturer of your card, is it a pci card or an usb device or what else?
Do you have other network cards installed? (e.g. ethernet devices)

I suspect that the device listed by lspci is NOT your wireless device.

post the output of the command [COLOR="Red"]iwconfig[/COLOR]

---

### Post by jackuk12 on 2007-01-09
Hi,
I have a wireless router but the pc which I'm installing ubuntu on is connected via an ethernet PCI NIC (only ethernet device in the machine) directly to the router via standard network cable. I tested this with puppy linux CD and the wizard in that one finds the card & connects me to the internet. 

Here's output of iwconfig

lo     no wireless extensions

eth0   no wireless extensions

sit0   no wireless extensions

Thanks for your help - Jack

---

### Post by hal10000 on 2007-01-09
Ok, then i misunderstood you.
So your network card seems to be configured correct.

1. Can you ping to your router: [COLOR="Red"]ping 192.168.1.1 [/COLOR]?
If you get an answer from your router then the first step is ok.

2. if point 1. ok ok then try to ping another ip-address on the internet, e.g.:
[COLOR="Red"]ping 194.25.2.129 [/COLOR] (this is the address of the german telekom dns server
or [COLOR="Red"]ping 209.85.135.103 [/COLOR] this is [www.google.com](www.google.com).

If you get a positive answer from one of these servers then you have dns problem.

Then you have to edit the file /etc/resolv.conf

open it with sudo gedit /etc/resolv.conf

1. if your router provides a dns server then put in here:
```

nameserver 192.168.1.1

```
or

2. if your router doent have a dns-server then you usually have to put in here the ip address of the dns server(s) provided by your ISP. you can add up to
three [COLOR="Red"]nameserver XXX.XXX.XXX.XXX[/COLOR] directives to this file.

---

### Post by jackuk12 on 2007-01-09
Thanks Hal10000!  Option 2 worked...I had to put in my ISP's DNS servers

Much appreciated!
Jack

---

