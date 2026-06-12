---
title: "Wireless Driver Problem"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by curbsidesteak on 2008-04-21
[COLOR="Blue"]I have just installed Ubuntu 7.10. All seems well except i have a wireless card, and the driver is giving me trouble.
It is a d-link Xtreme N DWA-522 wireless PCI card

 I followed completely the instructions on

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and have found myself stuck on 3.5 

after entering "tail /var/log/messages" my response was no errors but then after entering "ifconfig" and "iwconfig" here was the response[/COLOR]

eth0 Link encap:Ethernet HWaddr 00:11:11:17:51:A7
inet addr:71.56.48.198 Bcast:255.255.255.255 Mask:255.255.255.0
inet6 addr: fe80::211:11ff:fe17:51a7/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:8240 errors:0 dropped:0 overruns:0 frame:0
TX packets:1746 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2684353 (2.5 MB) TX bytes:309210 (301.9 KB)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)



 lo no wireless extensions.

eth0 no wireless extensions.

[COLOR="Blue"]No wireless "wlan0" appears. 
At this point the instructions assume that a wireless network will appear in the drop-down list from the Network Manager Icon on my desktop, but this is not the case. All that shows is the wired and modem.

I looked further into troubleshooting and found a help section suggesting to check to make sure the wireless card was "turned on" 

You'll see below what I entered and what was the response. [/COLOR]

joel@joel:~$ sudo lshw -C network
  *-network:0 UNCLAIMED  
       description: Network controller
       product: AR5416 802.11a/b/g/n Wireless PCI Adapter
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:17:51:a7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.0.160 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

[COLOR="Blue"]This is where I am stuck. Don't know what to try from here as there was nothing in the forums I could find about how to actually turn on the card if it is not on. I do not think this is the problem however, but am not sure as I am fairly new to this. 

Any help or suggestions would be appreciated.[/COLOR]

---

### Post by chili555 on 2008-04-21
Your problem may be NetworkManager: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) especially, this: > The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themYour wired is cconnected and has an IP address, so NM is not going to activate wireless.

However, I am confused. Your ifconfig says:```
eth0 Link encap:Ethernet HWaddr 00:11:11:17:51:A7
inet addr:71.56.48.198
```This suggests you are connected directly to the DSL or cable modem. However, your lshw says:```
ip=192.168.0.160 latency=64 link=yes
```This suggests you are connected to a router.

Please detach the wire, restart networking:```
sudo /etc/init.d/networking restart
```Then see if your wlan0 has emerged from hiding.

---

### Post by curbsidesteak on 2008-04-21
Thanks for the help. I'll try it and let you know what i find out.

---

### Post by curbsidesteak on 2008-04-23
Tried it, didn't make a difference. Wlan0 is still hiding and the wireless network is still not available in ndiswrapper. 
Any other ideas?

---

### Post by fsmithred on 2008-04-23
> **curbsidesteak said:**
> 

       description: Network controller
       product: AR5416 802.11a/b/g/n Wireless PCI Adapter
       vendor: Atheros Communications, Inc.
       


Won't the madwifi driver work with this chipset?

---

### Post by curbsidesteak on 2008-04-24
I just was reading on that in another thread. Thanks for the input though. I'll post if I am able to make it work.

---

