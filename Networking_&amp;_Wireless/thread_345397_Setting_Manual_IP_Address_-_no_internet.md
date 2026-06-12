---
title: "Setting Manual IP Address - no internet"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by robertpolson on 2007-01-24
I want to manually setup my eth1 wireless network and set the IP myself.

I have a linksys router which has a 192.168.1.1 IP and the usual mask of 255.255.255.0

I want to give my laptop this IP:  192.168.1.3

Here is what I have in my eth1 wireless setup set manually and IT DOES NOT  give me Internet connection (although skype does connect):


Manual

IP Address:	192.168.1.3
Netmask:	255.255.255.0

Checked: Activate when the computer starts 


Advanced Device information:

Description:	Ethernet Network Device
Broadcast: 192.168.1.255
Gateway: 192.168.1.1



Please help.

---

### Post by dbott67 on 2007-01-24
Can you please post the output of the following commands:

```
cat /etc/network/interfaces
```

Here's mine as an example:

```
dbott@dapper:~$ cat/etc/network/interfaces
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
wireless-essid bott
wireless-key s:mysecretwepkey
```

Suppose I want to make my eth1 interface static.  I would need to edit the /etc/network/interfaces file:

```
gksudo gedit /etc/network/interfaces
```
and then modify the eth0 section to read:
```
auto eth1
iface eth1 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1
```

If you're still having troubles, can you post the output of the following commands:
```
route -n
```
```
ifconfig -a
```

-Dave

---

### Post by robertpolson on 2007-01-24
So how would I set this up with a WPA Wireless protection:

> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.1.3
netmask 255.255.255.0
wireless-essid Psychedelic

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


My IP: 192.168.1.3
Router IP: 192.168.1.1
SubnetMask: 255.255.255.0

Gateway is same as router I think: 192.168.1.1

DNS - No idea what to put here

WPA TKIP: 123456


Thank you.

---

### Post by dbott67 on 2007-01-25
This thread should get you going for WPA (my D-Link only supports WEP): 
[http://www.ubuntuforums.org/showthread.php?t=318539](http://www.ubuntuforums.org/showthread.php?t=318539)

The DNS setting for most home-based NAT routers (i.e. D-Link, Linksys, Netgear, et al) would be the IP address of the router itself (192.168.1.1).  Most NAT routers have a DNS-forwarding service that will pass all DNS requests to your ISP's DNS server.

If you have a no-name router, you may experience DNS resolution or IPv6 issues.  Check this thread (posts #3 & #5) for more details:
[http://www.ubuntuforums.org/showthread.php?t=323747](http://www.ubuntuforums.org/showthread.php?t=323747)

-Dave

---

### Post by robertpolson on 2007-02-01
I tried to followed the guide several times and could not get my wireless wpa static ip working.

Can you please tell me what exactly should I put into my networ interfaces file?

Now it looks like this:

> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto ath0

I want to have this:

IP: 192.168.1.3
IP of my linksys router: 192.168.1.1
wpa key: 12435
SSID: Home - Discoverable (would be great if I knew how to make it so that linux can find none discoverable ssid too)

Please help.

---

### Post by wieman01 on 2007-02-02
We'll have to see what's going on first of all, so it will help if you posted the results of these 2 commands:
> iwlist scan
> iwconfig
That's all. 

What kind of WPA do you plan to use? WPA1 with TKIP or WPA2 with AES? Are you sure WPA is supported by your card? And have you tried **dbott67**'s advice in the first place? Try to connect to an unsecured network first and ensure your card is working properly.

---

### Post by robertpolson on 2007-02-04
I want to use:WPA1 with TKIP

My current wireless works just fine with WPA and dynamic ip managed by KnetworkManager, however KnetworkManager does not support static IP and that is what I need:


iwconfig

> lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Psychedelic"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:7B:99:3C
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=23/94  Signal level=-72 dBm  Noise level=-95 dBm
          Rx invalid nwid:393336  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


istlist scan
bash: istlist: command not found

---

### Post by wieman01 on 2007-02-05
Typo... This is the right command (sorry!):
> iwlist scan
If you want to use static IP, the HOWTO in my signature can help. But you need to uninstall kde-network-manager first of all, otherwise it won't work. Not sure if you want to do that. If you want to have a crack at it, try the HOWTO first and post here if you get stuck.

_**EDIT:**_
And please post the contents of **"/etc/network/interfaces"**...

---

