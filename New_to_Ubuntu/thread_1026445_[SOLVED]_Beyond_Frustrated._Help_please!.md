---
title: "[SOLVED] Beyond Frustrated. Help please!"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by CCCody on 2008-12-31
I'm tired of making threads on this, and I have yet to solve it after two days. I've reinstalled Ubuntu 8.10 Twice now. Downloaded 8.04 (Same problem) And reinstalled Windows.

My internet connection DOES NOT WORK (In Ubuntu.) ](*,)

It works fine in Windows, and my (neighbors) wireless works. 1Mbit, sloooooow.

I don't know if this helps but:

> eth0      Link encap:Ethernet  HWaddr 00:1d:09:54:43:1d  
          inet addr:76.210.36.139  Bcast:76.210.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21d:9ff:fe54:431d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1554 errors:0 dropped:0 overruns:0 frame:0
          TX packets:241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86474 (86.4 KB)  TX bytes:51589 (51.5 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:44:c6:80:4d  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fec6:804d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1235 errors:0 dropped:0 overruns:0 frame:1700
          TX packets:1410 errors:40 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1123080 (1.1 MB)  TX bytes:269079 (269.0 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15700 (15.7 KB)  TX bytes:15700 (15.7 KB)

pan0      Link encap:Ethernet  HWaddr c2:4d:5c:66:63:7c  
          inet6 addr: fe80::c04d:5cff:fe66:637c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)


ifconfig

Also, my modem lights are on. Even the activity light blinks :confused:

Please help me figure this out, I really would like to try this out but the no internet connection is driving me nuts..

---

### Post by Michael.Godawski on 2008-12-31
hi CCCody, 

can you please post the outputs of these terminal commands too?

```
iwconfig
sudo iwlist scan
sudo lshw -C network
cat /etc/network/interfaces
```

So either your wired connection nor you wlan does not work in Ubuntu?

---

### Post by mikewhatever on 2008-12-31
Assuming eth0 is wired and eth1 is wireless, you seem to be getting ips on both. What model is the modem? Ethernet or USB? Can you also post the output of <sudo lshw -C network>.

On the second thought, perhaps it's better to let it go for a while. It's very hard to solve such problems under emotional pressure.

---

### Post by albandy on 2008-12-31
type sudo route -n and post it. 
I see two ip's one from eth0 and one from eth1. It's possible that you've defined two default gateways to 0.0.0.0.

---

### Post by CCCody on 2008-12-31
iwconfig:

> lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated  

sudo iwlist scan

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:50:C8:E2:26
                    ESSID:"wns"
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:1/5  Signal level:-88 dBm  Noise level:-30 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:1B:5B:53:C3:99
                    ESSID:"2WIRE837"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-21 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s


sudo lshw -c network

>   *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:54:43:1d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=76.210.43.22 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:c6:80:4d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.2.7 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c2:4d:5c:66:63:7c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


cat /etc/network/interfaces

> auto lo
iface lo inet loopback


There are those commands.

I'm not quite sure what wlan is. If it's like LAN I'm still not too sure.

I'm connected directly to the internet

Laptop -- Modem

Wireless works but it is not my wireless. I do not pay for it, the only I pay for is Wired and I'd like to get my own working thanks. :)

---

### Post by CCCody on 2008-12-31
> **mikewhatever said:**
> Assuming eth0 is ethernet and eth1 is wireless, you seem to be getting ips on both. What model is the modem? Ethernet or USB? Can you also post the output of <sudo lshw -C network>.

On the second thought, perhaps it's better to let it go for a while. It's very hard to solve such problems under emotional pressure.

Modem model is Motorolla, Ethernet.

Output of sudo lshw -c network:

>   *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:54:43:1d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=76.210.43.22 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:c6:80:4d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.2.7 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c2:4d:5c:66:63:7c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Sudo Route -n 

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
76.210.0.0      0.0.0.0         255.255.0.0     U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1


---

### Post by stevoo on 2008-12-31
it seems that you are connected on both at the same time. 

Since you only want the wired on, disable your wireless. This can be done if you on a laptop with funciton key and the appropriate f(button).

When you do that, try accessing the internet again.
or use this command
ping [www.google.com](www.google.com)

---

### Post by albandy on 2008-12-31
eth0 is your wired connection and eth1 is your wireless one.
Stop you wifi card and do 
sudo dhclient eth0

if you've not a wifi button to disable it, type sudo ifconfig eth1 down

---

### Post by CCCody on 2008-12-31
Output of Sudo dhclient eth0:

> There is already a pid file /var/run/dhclient.pid with pid 13403
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1d:09:54:43:1d
Sending on   LPF/eth0/00:1d:09:54:43:1d
Sending on   Socket/fallback
DHCPREQUEST of 76.210.43.22 on eth0 to 255.255.255.255 port 67
DHCPACK of 76.210.43.22 from 192.168.1.254
SIOCADDRT: No such process
bound to 76.210.43.22 -- renewal in 59 seconds.


And I couldn't ping [www.google.com](www.google.com)

> ping: unknown host [www.google.com](www.google.com)


---

### Post by albandy on 2008-12-31
could you do 
cat /etc/resolv.conf 
and put it here. I think your ISP is not giving you the correct DNS entries

---

### Post by CCCody on 2008-12-31
> **albandy said:**
> could you do 
cat /etc/resolv.conf 
and put it here. I think your ISP is not giving you the correct DNS entries

# Generated by NetworkManager
domain RDS
search RDS
nameserver 192.168.1.254
nameserver 192.168.2.1

Is the output.

Thank you for your help.

---

### Post by albandy on 2008-12-31
This is very strange, your ISP is giving you a public IP: 76.xx.xx.xx, but your DNS entries are private 192.168.xx.xx

What do you have connected to your router?

---

### Post by CCCody on 2008-12-31
> **albandy said:**
> This is very strange, your ISP is giving you a public IP: 76.xx.xx.xx, but your DNS entries are private 192.168.xx.xx

What do you have connected to your router?


I don't use a router, I'm connected directly to the modem.

---

### Post by mikewhatever on 2008-12-31
Cody, make sure you don't set any DNS addresses for eth0 in Network Manager's Edit Connections window. The ones you have may be OK for the router, but not for the modem.

As for the wireless card, AFTER you get the wired working, check under System->Admin->Hardware Drivers for the wireless driver.

---

### Post by CCCody on 2008-12-31
> **mikewhatever said:**
> Cody, make sure you don't set any DNS addresses for eth0 in Network Manager's Edit Connections window. The ones you have may be OK for the router, but not for the modem.

I actually don't know what this means, sorry. I don't use a router either.

I haven't messed with any DNS settings either, if that's what you meant.

---

### Post by albandy on 2008-12-31
Have you disabled wifi?

Try ping this 66.102.9.147

ping 66.102.9.147

---

### Post by mikewhatever on 2008-12-31
> **CCCody said:**
> I actually don't know what this means, sorry. I don't use a router either.

I haven't messed with any DNS settings either, if that's what you meant.

Right click on the network manager icon, select Edit Connections and check there are no DNS entries for eth0. The connection has to be set to Atomatic DHCP.

---

### Post by CCCody on 2008-12-31
> **albandy said:**
> Have you disabled wifi?

Try ping this 66.102.9.147

ping 66.102.9.147

It was off, it's on now so I can communicate.

PING 66.102.9.147 (66.102.9.147) 56(84) bytes of data.
64 bytes from 66.102.9.147: icmp_seq=1 ttl=237 time=144 ms
64 bytes from 66.102.9.147: icmp_seq=2 ttl=237 time=145 ms
64 bytes from 66.102.9.147: icmp_seq=3 ttl=237 time=145 ms
64 bytes from 66.102.9.147: icmp_seq=4 ttl=237 time=145 ms
64 bytes from 66.102.9.147: icmp_seq=5 ttl=237 time=145 ms
64 bytes from 66.102.9.147: icmp_seq=6 ttl=237 time=145 ms
64 bytes from 66.102.9.147: icmp_seq=7 ttl=237 time=149 ms
64 bytes from 66.102.9.147: icmp_seq=8 ttl=237 time=145 ms
64 bytes from 66.102.9.147: icmp_seq=9 ttl=237 time=144 ms
64 bytes from 66.102.9.147: icmp_seq=10 ttl=237 time=141 ms
64 bytes from 66.102.9.147: icmp_seq=11 ttl=237 time=146 ms
etc.

Edit:

> **mikewhatever said:**
> Right click on the network manager icon, select Edit Connections and check there are no DNS entries for eth0.

Mine looks just like the one in the screenshots.

---

### Post by mikewhatever on 2008-12-31
Can you also check what DNS addresses the ISP gives you. Right click on the NM, select Connection Ifo. What's the Primary DNS there?

Perhaps you could try putting Open DNS addresses there.
208.67.222.222
208.67.220.220

---

### Post by CCCody on 2008-12-31
> **mikewhatever said:**
> Can you also check what DNS addresses the ISP gives you. Right click on the NM, select Connection Ifo. What's the Primary DNS there?

Perhaps you could try putting Open DNS addresses there.
208.67.222.222
208.67.220.220

Primary DNS is 192.168.1.254

---

### Post by mikewhatever on 2008-12-31
> **CCCody said:**
> Primary DNS is 192.168.1.254

That seems to be the problem, because that is a private address. Try using the ones from Open DNS.

---

### Post by CCCody on 2008-12-31
> **mikewhatever said:**
> That seems to be the problem, because that is a private address. Try using the ones from Open DNS.

Eh.. How exactly do I do that? Thanks again.

---

### Post by mikewhatever on 2008-12-31
Edit eth0 through the NM, under Method select 'Auto DHCP address only' and enter open DNS addresses separated by a coma. Make sure Connect Automatically box is checked.

---

### Post by CCCody on 2008-12-31
Would it require a restart? I turned off the wireless and it doesn't seem to work.

I'll go ahead and restart now and post the results.

---

### Post by mikewhatever on 2008-12-31
> **CCCody said:**
> Would it require a restart? I turned off the wireless and it doesn't seem to work.

I'll go ahead and restart now and post the results.

Oh, I forgot to post that. A restart will probably do the job, but <sudo ifconfig eth0 down && sudo ifconfig eth0 up> was what I did.

---

### Post by albandy on 2008-12-31
and remember to stop the wifi. Also in every test

---

### Post by CCCody on 2008-12-31
The command didn't seem to work.

I should also mention when I rebooted the settings were returned to normal, as if I never even did the editing.

This was a normal reboot, not a hard one.

---

### Post by cb951303 on 2008-12-31
> **CCCody said:**
> The command didn't seem to work.

I should also mention when I rebooted the settings were returned to normal, as if I never even did the editing.

This was a normal reboot, not a hard one.

it's a bug with network manager. After restart it resets settings. Change your dns numbers to opendns then disable and reenable your connection from network manager without restarting computer. See if it works. If yes then there is a workaround to make your settings stick after reboot. I'll walk you through it

---

### Post by albandy on 2008-12-31
I think you should do a bit of manual configuration.
Edit your /etc/network/interfaces and add this:

sudo gedit /etc/network/interfaces

[I]auto eth0
iface eth0 inet dhcp
dns-nameservers 208.67.222.222 208.67.220.220[/I]

save and reboot

---

### Post by CCCody on 2008-12-31
> **albandy said:**
> I think you should do a bit of manual configuration.
Edit your /etc/network/interfaces and add this:

sudo gedit /etc/network/interfaces

[I]auto eth0
iface eth0 inet dhcp
dns-nameservers 208.67.222.222 208.67.220.220[/I]

save and reboot

I did that and now it just says, "Device is unmanaged" I can't even edit anything now.

---

### Post by mikewhatever on 2008-12-31
When you put stuff into /etc/network/interfaces, the interface is not managed through the NM. It should work one way or the other though. Double check you are dealing with the right interface, it should be eth0 (zero, not o) and not eth1.

---

### Post by CCCody on 2008-12-31
It's Eth0. Also when I try to edit through NM it's called ifupdown (eth0) And when attempting to edit I get a read only error.

---

### Post by cb951303 on 2008-12-31
> **CCCody said:**
> I did that and now it just says, "Device is unmanaged" I can't even edit anything now.

Okay take a deep breath :) Because of the network manager bug the best wayfor you to try OpenDNS numbers is to create new connection. And then select it from NM applet.

Here is hows my setup looks like. Notice that 192.168.1.1 is my routers IP address. By default routers only allow local IP's ranging from x.x.x.1 (router's IP) to x.x.x.255. So I chose 192.168.1.101 as my local IP.

---

### Post by CCCody on 2008-12-31
> **cb951303 said:**
> Okay take a deep breath :) Because of the network manager bug the best wayfor you to try OpenDNS numbers is to create new connection. And then select it from NM applet.

Here is hows my setup looks like. Notice that 192.168.1.1 is my routers IP address. By default routers only allow local IP's ranging from x.x.x.1 to x.x.x.255. So I chose 192.168.1.101 as my local IP.

Alright dumb question. I know what the IP address on the bottom oIt's Eth0. Also when I try to edit through NM it's called if my modem is. That's local gateway correct? Also how do I choose a local ip?

Thanks.

Edit:

I think I get it.

I'll report back.

---

### Post by cb951303 on 2008-12-31
> **CCCody said:**
> Alright dumb question. I know what the IP address on the bottom oIt's Eth0. Also when I try to edit through NM it's called if my modem is. That's local gateway correct? Also how do I choose a local ip?

Thanks.

If you are using automatic DHCP the gateway IP is given you by your internet provider and it's not a local IP.
what's the brand/model of your modem? I'll tell you what you should choose as the gateway and local ip

---

### Post by CCCody on 2008-12-31
My Modem is a motorolla.

---

### Post by cb951303 on 2008-12-31
> **CCCody said:**
> My Modem is a motorolla.

what model

---

### Post by CCCody on 2008-12-31
> **cb951303 said:**
> what model

You know it doesn't matter :)

I did what you said earlier, used the local IP from the bottom of my modem, picked one. Unedited the thing the guy told me to earlier, rebooted. And.. Oh sweet sexy non-slow internet.

I have a headache.. But the internet is FINALLLLLLLYYYY working.

I'd like to jump through the screen and hug each and every one of you.

Thank you oh so very much.

You have no idea how happy I am!

Now I can get some sleep!

Happy New Years :popcorn:

---

### Post by cb951303 on 2008-12-31
> **CCCody said:**
> You know it doesn't matter :)

I did what you said earlier, used the local IP from the bottom of my modem, picked one. Unedited the thing the guy told me to earlier, rebooted. And.. Oh sweet sexy non-slow internet.

I have a headache.. But the internet is FINALLLLLLLYYYY working.

I'd like to jump through the screen and hug each and every one of you.

Thank you oh so very much.

You have no idea how happy I am!

Now I can get some sleep!

Happy New Years :popcorn:

Glad it worked. remember if network manager resets its settings it's a bug. You're not doing anything wrong.
:popcorn:

---

