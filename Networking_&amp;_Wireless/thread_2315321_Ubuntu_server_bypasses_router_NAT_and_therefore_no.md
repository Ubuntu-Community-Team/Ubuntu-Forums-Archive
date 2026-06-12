---
title: "Ubuntu server bypasses router NAT and therefore not visible on LAN, has own public IP"
date: 2016-02-27
forum: Networking &amp; Wireless
---

### Post by pwnzornoob on 2016-02-27
I honestly didn't know this was even possible and all of my google searches seem to come up with either the reverse issue/unrelated.
But starting with the hardware:

Networking hardware:
Zyxel VMG3326-D20A (ISP tailored model, basically the P-2812HNU-F1 without VoIP, [datasheet link]("ftp://ftp.zyxel.com/P-2812HNU-F1/user_guide/P-2812HNU-F1_1.00.pdf")), basically it's a VDSL2 modem+router.
It's pretty much on default settings with some port forwardings etc. nothing special, and configured as address 192.168.10.1 in the local subnet. NAT and DHCP are enabled on the router with 192.168.10.33 as the starting address for the IP pool. DNS servers are set to fetch from the ISP and work normally. Also the DMZ and UPnP are off.

Server hardware:
MB: Asrock N3150DC-ITX with integrated Intel Celeron N3150.
Integrated NIC with Realtek RTL8111GR.
Running Ubuntu Server 15.10.

Now to the actual issue, all of my devices are behind NAT as normal and so they share the same local network as illustrated:
[ATTACH=CONFIG]267544[/ATTACH]
However, as you can see the server is not in the picture and the only wired device is my personal PC.
But when inspecting from the connections screens you can see two LAN ports in use, as they should because the server also is connected via cable.
[ATTACH=CONFIG]267545[/ATTACH]
This had me puzzled for a second because I could download and install updates on the server normally, so the server definitely had internet connectivity.

Running the following command on the server produces an IP starting with 88.112.x.x, while all the other devices report 88.114.x.x.
```
dig +short myip.opendns.com @resolver1.opendns.com
88.112.xx.xx
```

The server somehow bypassed the NAT & DHCP on the router and requested its own IP from my ISP's DHCP?

ifconfig produces the following:
```

ifconfig
enp3s0    Link encap:Ethernet  HWaddr d0:50:99:a2:xx:xx
          inet addr:88.112.xx.xx  Bcast:88.112.yy.255  Mask:255.255.240.0
          inet6 addr: fe80::d250:99ff:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:36238 (36.2 KB)  TX bytes:34982 (34.9 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I'm new to the networking in Linux and I've tried to scourge for information, but I'm a bit puzzled by this. How can the server bypass the router in this way or is this actually desired behavior?
The purpose of the server is to be a NAS running Samba, Mumble, Git etc. and if possible also Kodi to act as a HTPC. I would therefore like the possibility of connecting via LAN to access the shared files.

I see two options to continue towards to:
[LIST=1]
[*]Somehow make the server request a new IP from my router's DHCP server and therefore get it included in the LAN as with the other devices. Then forward necessary ports for the services I intend to run on the Zyxel for outside connectivity.
[*]I actually like the idea of the server having a separate public IP, but I doubt it is possible to achieve this AND get the LAN connectivity? Or is it possible if I bought another NIC cheaply so that the server has two physical network adapters, where one is connected straight to the internet on the current mystery configuration, and the other one would be the "LAN card"?
[/LIST]

Any ideas on the situation, and furthermore am I just totally lost and over my head in this?
Also is there something else I should tell about the system? I tried including everything I could think of.
Thanks for the responses!

---

### Post by chili555 on 2016-02-27
Yikes! Just Yikes!!

I hate to answer a thread where I don't know or, at least suspect the answer, however, I do have a suggestion. In a server, to which you normally need to ssh and ftp, it is customary to set a static IP address. I suggest you set up /etc/network/interfaces to force an address in the expected 192.168.10.x network; something like:```
auto lo
iface lo inet loopback

auto enp3s0 
iface enp3s0 inet static
address 192.168.10.150
netmask 255.255.255.0
gateway 192.168.10.1
dns-nameservers 192.168.10.1 8.8.8.8
```Reboot and tell us if it is fixed.

---

### Post by pwnzornoob on 2016-02-28
Thanks for the reply!
I was beginning to do this, but my friend with a similar modem pointed this in the Zyxel settings:
[ATTACH=CONFIG]267571[/ATTACH]
For some reason I can't understand, in the Broadband > Internet Setup > VDLSWAN1 > Enable Concurrent WAN > Bridge Port 1 [X] was checked by default... Hnnnnnnngh, no wonder it goes directly through. Though it makes a lot of sense now on how it worked while not appearing on LAN.

Anyhow, after a little tinkering to get the networking running, the server is now behind NAT like the rest of the devices and pingable on LAN.

I got interested though about the possibility of it having a separate public IP, so that no one tries to connect to my other devices even my accident. I'll doubt it's possible to do this while having the device on LAN, but I'll try to search for it.
If it isn't possible to do this via the router on the current config, I'd imagine it would be possible if I'd add another NIC. So that one NIC is connected to the LAN and another to the outside world via a bridged router port, so that the server is in two different subnets?

**Edit:**
There is a setting to address IPs inside NAT to different Global IPs, but the problem is that I can't input 0.0.0.0 or 255.255.255.255 to the Global IP to make it dynamically address it from the ISP. My contract doesn't include static IPs (only that I have a pool of 5 dynamic IPs) so this route doesn't seem possible for the moment.

**Edit2:**
Well I ordered another NIC for only 15&#8364; to try and test the two subnet system, I'll mark the current issue as solved at the same time because now I have the server on LAN.

---

