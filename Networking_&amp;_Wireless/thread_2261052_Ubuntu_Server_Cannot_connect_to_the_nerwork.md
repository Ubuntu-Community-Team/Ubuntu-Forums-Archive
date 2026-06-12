---
title: "Ubuntu Server: Cannot connect to the nerwork"
date: 2015-01-16
forum: Networking &amp; Wireless
---

### Post by sweeten.jacob on 2015-01-16
I have tried for hours to connect. I have checked everything.


eth0 static
iface eth0 inet static
address 192.168.254.16
netmask 255.255.255.0
gateway 192.168.254.254
resolvcfg DNS: I used opendns


I have tried DHCP. Nothing worked. I can't even ping another wired computer on my network or the modem. The Ethernet light blinks slow and constant. All pings turn up unable to resolve host. All ip pings say that cannot trace path.
I have Googled everything you can think of and tried everything and NOTHING worked. I think it may be the drivers I have for my on-board Ethernet adapter so I downloaded them and tried to run them but the make command has to be downloaded and I cant download it without internet. Plz help.

---

### Post by TheFu on 2015-01-16
Is that really the correct gateway? It is not the normal address.
Also - can you please follow this: [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) to determine where the issue is? Basically, use ip addresses for everything you test, not DNS names first. If all those things work, it is a DNS issue.

---

### Post by sweeten.jacob on 2015-01-16
My Windows PC is working normally on static and its gateway is 192.168.254.254. I use that for all static devices on this network. Never had a problem. I use it to change my modem's settings.

The instructions on that website gave me:

[IMG]http://i.imgur.com/EXtMFuZ.jpg[/IMG]

Also, here is some modem info.
DHCP Start address 192.168.254.15
DHCP End address 192.168.254.47
modem ip address 192.168.254.254
Subnet Mask 255.255.255.0

Ping to DNS says destination host unreachable

---

### Post by steeldriver on 2015-01-16
You appear to be trying to set a static IP that is **within** your router's DHCP pool - that allows the possibility of an address conflict / misrouted packets

---

### Post by TheFu on 2015-01-16
The fact that the NIC is GigE but connects at only 10base-tx tells me something is very wrong.  Normally, I'd expect a really bad cable, switch port, driver, but as steeldriver says, it could be a conflict with another system.

If would really, really, really, be helpful if you did the tests from the prior link AND posted the exact results back here.  We can't read minds. ;)

---

### Post by sweeten.jacob on 2015-01-16
Rounter ping **result:**
Destination host unreachable


ping 8.8.8.8 **result:**
Destination host unreachable


dmesg |grep eth0[0-9] **result:**
nothing.


sudo lshw -c newtork **result:**
shown in the picture above


ifconfig -a **result:**
eth0    link encap:Ethernet HWaddr 00:18:8b:81:c2:ee
    inet addr: 192.168.254.16 Bcast:192.168.254.255 Mask: 255.255.255.0
    UP BROADCAST MULTICAST MTU:1500 METRIC: 1
    RX packets: 431 errors: 19 dropped: 0 overruns: 0 frame: 0
    TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
    collisions: 0 txqueuelen:1000
    RX bytes:60162 (60.1 KB) TX bytes: 0 (0.0 B)
    Interrupt: 21


more /etc/resolv.conf **result:**
nameserver: 208.67.222.222
nameserver: 208.67.220.220


route **result:**
[TABLE="width: 500, align: left"]
[TR]
[TD]Destination[/TD]
[TD]Gateway[/TD]
[TD]Genmask[/TD]
[TD]Flags[/TD]
[TD]metric[/TD]
[TD]ref[/TD]
[TD]use[/TD]
[TD]iface[/TD]
[/TR]
[TR]
[TD]default[/TD]
[TD]192.168.254.254[/TD]
[TD]0.0.0.0[/TD]
[TD]UG[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]eth0[/TD]
[/TR]
[TR]
[TD]localnet[/TD]
[TD]*[/TD]
[TD]255.255.255.0[/TD]
[TD]U[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]0[/TD]
[TD]eth0[/TD]
[/TR]
[/TABLE]







Note: i'm not sure why there is no Genmask on default. There is a netmask set in /etc/network/interfaces. It is set to 255.255.255.0.

---

### Post by TheFu on 2015-01-17
If you cannot ping your local router, then you really aren't on any network. Swap the cable, try a different port, check the driver. Until you can **ping 192.168.254.254** - nothing else matters.

---

