---
title: "I'm connected, but can't ping? What the...?"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by Vaughands on 2008-09-30
[IMG]http://img525.imageshack.us/img525/4766/screenshotconnectioninfhk8.png[/IMG]

Well, that displays once I boot into Ubuntu and am on Roaming mode. I can't access the internet though... so therefore I attempt to fiddle with the settings, set myself to something else... nothing. So back to roaming.. but wait. 0.0.0.0!? Why won't you go back to the orignal settings!?

 Anyways, it'll do this till I reboot. no big, the million dollar question, if I'm connected why can't I do anything...

---

### Post by Vaughands on 2008-09-30
Someone must know?

---

### Post by caljohnsmith on 2008-09-30
How about posting:
```
ifconfig
```
And also, have you tried pinging an IP instead of a host name? Try:
```
ping -c3 209.85.171.99
```

---

### Post by Vaughands on 2008-10-01
> vaughan@vaughan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:43:81:16  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe43:8116/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3112 (3.0 KB)  TX bytes:4734 (4.6 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6800 (6.6 KB)  TX bytes:6800 (6.6 KB)

vaughan@vaughan-desktop:~$ ping -c3 209.85.171.99
PING 209.85.171.99 (209.85.171.99) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=1 Destination Host Unreachable
From 192.168.1.101 icmp_seq=2 Destination Host Unreachable
From 192.168.1.101 icmp_seq=3 Destination Host Unreachable

--- 209.85.171.99 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2000ms
, pipe 3
vaughan@vaughan-desktop:~$ 
vaughan@vaughan-desktop:~$ 




There we are :)

---

### Post by Iowan on 2008-10-01
This is a static address... Is there a router, modem, etc., on the network?  I presume *something* is at 192.168.1.1.  Can you ping it? Does that *something* have a DHCP server?  It'd be interesting to see if the machine could get a DHCP address - and what it might be.

---

### Post by Vaughands on 2008-10-01
Linksys WRT150N Router:

[IMG]http://img396.imageshack.us/img396/6195/firefoxwd5.png[/IMG]

---

### Post by caljohnsmith on 2008-10-01
Are you using an ADSL modem, or what are you connected to? 

How about also posting:
```
sudo lshw -C network
dmesg | grep -e eth0 -ie error -ie warning
ping -c3 192.168.1.1
route -n
cat /etc/network/interfaces
```

---

### Post by Vaughands on 2008-10-01
> vaughan@vaughan-desktop:~$ sudo lshw -C network
[sudo] password for vaughan: 
  *-network               
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:43:81:16
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
vaughan@vaughan-desktop:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

vaughan@vaughan-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
vaughan@vaughan-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback







#iface eth0 inet ipv4ll

#auto eth0












There you go. :)

It appears I'm not actually connected.

---

### Post by caljohnsmith on 2008-10-01
So are you trying to use your wireless card with your router, or are you just trying to connect via ethernet right now? Also, post the output of:
```
dmesg | grep -e eth0 -ie error -ie warning
```

---

### Post by Vaughands on 2008-10-01
I don't mind either really, I just want internet in general. I have ethernet and wireless support. I rare do use my wireless, so its no biggie. Whatever I can get to work the fastest and easiest would be wonderful :) One second, I'mma reboot back into Linux and I'll post the output of that commad.

Output:

> vaughan@vaughan-desktop:~$ dmesg | grep -e eth0 -ie error -ie warning
[   28.064314] eth0: RealTek RTL8139 at 0xa000, 00:1b:24:43:81:16, IRQ 16
[   28.064317] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   45.866181] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   53.873571] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   83.187004] eth0: no IPv6 routers present
vaughan@vaughan-desktop:~$ 
vaughan@vaughan-desktop:~$ 












---

### Post by cariboo on 2008-10-01
The picture just shows the first page of the management interface, A screenshot of the status page would help a whole lot more. At least then we can see if you have a proper ip address and have dns set up properly. From the looks of it your computer is working ok, but you have a problem with the router setup.

If you do post a screenshot of the status page renew the ip address before posting it.

Jim

---

### Post by Vaughands on 2008-10-01
Sure thing, here you go:

[IMG]http://img353.imageshack.us/img353/4076/firefox2jw6.png[/IMG]

---

### Post by caljohnsmith on 2008-10-01
So basic sanity check: have you gone into System > Admin > Networking, click unlock, type password, enable only your eth0 ethernet interface, click it to select it, hit "properties", and you have "roaming mode" enabled here? And you are hooked up to your linksys router via an ethernet cable?

---

### Post by Vaughands on 2008-10-01
Basic sanity check, check. Thats all done of course, and the ethernet is 100% working as I'm using it on Windows.

---

### Post by caljohnsmith on 2008-10-01
OK, open your interfaces file:
```
gksudo gedit /etc/network/interfaces
```
And add the following lines at the end:
```
auto eth0
iface eth0 inet dhcp

```
Then do:
```
sudo ifdown eth0
sudo ifup eth0
```
And it might also take a networking kick-start:
[HTML]sudo /etc/init.d/networking restart[/HTML]

---

### Post by Vaughands on 2008-10-01
> vaughan@vaughan-desktop:~$ gksudo gedit /etc/network/interfaces
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:82: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:111: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:140: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:176: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:210: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:111: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:140: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:176: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:210: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
vaughan@vaughan-desktop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
vaughan@vaughan-desktop:~$ sudo ifup etho0
Ignoring unknown interface etho0=etho0.
vaughan@vaughan-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:24:43:81:16
Sending on   LPF/eth0/00:1b:24:43:81:16
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
vaughan@vaughan-desktop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
vaughan@vaughan-desktop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
vaughan@vaughan-desktop:~$ 



Not... configured?

---

### Post by caljohnsmith on 2008-10-01
If you do:
```
cat /etc/network/interfaces
```
Does it show those lines I asked you to add to that file? If so, try the following:
```
gksudo gedit /etc/network/interfaces
```
And replace the lines I gave you with:
```
iface eth0 inet static
address 192.168.1.25
netmask 255.255.255.0
gateway 192.168.1.1
```
Save the file, quit, and then do the ifdown/ifup commands I gave previously, and if those don't work, then the networking restart.

---

### Post by Vaughands on 2008-10-01
> vaughan@vaughan-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback







#iface eth0 inet ipv4ll

#auto eth0




auto eth0
vaughan@vaughan-desktop:~$ gksudo gedit /etc/network/interfaces
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:82: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:111: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:140: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:176: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:210: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:111: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:140: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:176: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:210: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
vaughan@vaughan-desktop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
vaughan@vaughan-desktop:~$ sudo ifup eth0
vaughan@vaughan-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
vaughan@vaughan-desktop:~$ /etc/network/interfaces
bash: /etc/network/interfaces: Permission denied
vaughan@vaughan-desktop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback







#iface eth0 inet ipv4ll

#auto eth0




iface eth0 inet static
address 192.168.1.25
netmask 255.255.255.0
gateway 192.168.1.1
vaughan@vaughan-desktop:~$ 



Conclusion is? No internet with that.

---

### Post by caljohnsmith on 2008-10-01
The ifup command and networking restart look like they completed successfully. Try pinging your router again:
```
ping -c3 192.168.1.1
```
Also do:
```
dmesg | tail 
```

---

### Post by Vaughands on 2008-10-01
> pvaughan@vaughan-desktop:~$ ping -c3 192.168.1.1
connect: Network is unreachable
vaughan@vaughan-desktop:~$ dmesg | tail
[   44.052383] Bluetooth: L2CAP socket layer initialized
[   44.124224] Bluetooth: RFCOMM socket layer initialized
[   44.124532] Bluetooth: RFCOMM TTY layer initialized
[   44.124535] Bluetooth: RFCOMM ver 1.8
[   61.560160] NET: Registered protocol family 10
[   61.560654] lo: Disabled Privacy Extensions
[   61.899259] hda-intel: Invalid position buffer, using LPIB read method instead.
[   70.604007] ISO 9660 Extensions: Microsoft Joliet Level 3
[   70.604884] ISOFS: changing to secondary root
[   72.386207] eth0: no IPv6 routers present
vaughan@vaughan-desktop:~$ 
vaughan@vaughan-desktop:~$ 





IpV6.. I'm pretty sure I got an IPV4 or something, problem found?

---

### Post by Vaughands on 2008-10-01
Bump.

---

### Post by Iowan on 2008-10-01
> **Vaughands said:**
> IpV6.. I'm pretty sure I got an IPV4 or something, problem found? That "no IPv6 routers present" message is more informative than warning...
All this "stuff" > ...
auto eth0
vaughan@vaughan-desktop:~$ gksudo gedit /etc/network/interfaces
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:82: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:111: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:140: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
...isn't embedded in your **/etc/network/interfaces** file... is it?
My **interfaces** file is too big - it contains:```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


iface eth0 inet dhcp

```Feel free to copy/paste it into a fresh (empty) copy of your **interfaces** file.

---

### Post by Vaughands on 2008-10-01
Yeah, I disabled IPv6 with no successs... do you think the new interface file will be of any use?

---

### Post by Vaughands on 2008-10-02
Bump.

---

### Post by Vaughands on 2008-10-02
Nobody has ANY idea?

---

### Post by doas777 on 2008-10-02
do you have a firewall on your host? does it allow traffic to and from your wifi?

also what do you when you run
```

route

```

---

### Post by Vaughands on 2008-10-02
There is no firewall between me and the router.

---

### Post by doas777 on 2008-10-02
> **Vaughands said:**
> There is no firewall between me and the router.

well, I think most ubuntu boxes have IPtables on by default, but I believe the ruleset is permissive.

can you ping the loopback and the address that your adapter shows in the op?

---

### Post by Vaughands on 2008-10-02
No, I cannot reach my router. As shown in these previous posts.

---

### Post by cariboo on 2008-10-02
Just a question, when you are typing eth0 are you typing capital o or zero?

Jim

---

### Post by Vaughands on 2008-10-02
Zero, that is correct right?

---

### Post by Vaughands on 2008-10-02
Bump.

---

### Post by Iowan on 2008-10-02
> **Vaughands said:**
> ... do you think the new interface file will be of any use? If the quote in post #18 was an accurate representation of what is in your **/etc/network/interfaces** file, then it's not surprising that DHCP doesn't work... and *maybe* why networking in general has problems.  You can strip away all the unnecessary lines from your file, or use mine.  If you prefer static address, leave the last section of your file.  You need only one line each of **auto lo** and **auto eth0**. The commented lines (begin with #) won't hurt, but there are two lines defining "iface lo inet loopback", also two "auto lo" lines... unless that entire quote is NOT the contents.  Otherwise, there are two different versions:
```
auto lo
iface lo inet loopback







#iface eth0 inet ipv4ll

#auto eth0




auto eth0
``` ```
auto lo
iface lo inet loopback







#iface eth0 inet ipv4ll

#auto eth0




iface eth0 inet static
address 192.168.1.25
netmask 255.255.255.0
gateway 192.168.1.1
```The first version has no definition for eth0, the second has no (uncommented) **auto eth0** line.

---

### Post by Vaughands on 2008-10-02
What exactly is wrong with my file...?

---

### Post by Iowan on 2008-10-02
Which one? > **Iowan said:**
> The first version has no definition for eth0, the second has no (uncommented) **auto eth0** line.I think I was misreading post #18 - thinking all these lines were contained in the file: > /usr/share/themes/Human-Murrine/gtk-2.0/gtkrc:82: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.

---

### Post by Vaughands on 2008-10-02
Nope, that is not contained within the interfaces file. That is simply my theme giving off a warning.

---

### Post by doas777 on 2008-10-02
> **Vaughands said:**
> No, I cannot reach my router. As shown in these previous posts.

route prints out the pcs ip routing table. some references in it point to your router. it's output is useful in finding IP configuration bugs, like an unreachable gateway. you do not need to be able to reach your router to run route and it may show errors that would prevent you from reaching the router.

---

### Post by Vaughands on 2008-10-03
Interfaces File:

> auto lo
iface lo inet loopback




auto eth0
iface eth0 inet ipv4ll


Routing Table:

> vaughan@vaughan-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
vaughan@vaughan-desktop:~$ 
vaughan@vaughan-desktop:~$ sudo gkedit /etc/network/interfaces
[sudo] password for vaughan: 
sudo: gkedit: command not found
vaughan@vaughan-desktop:~$ sudo gedit /etc/network/interfaces
vaughan@vaughan-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
vaughan@vaughan-desktop:~$ sudo gedit /etc/network/interfaces


---

### Post by Vaughands on 2008-10-03
Bump.

---

### Post by Iowan on 2008-10-03
If I read **man interfaces** correctly, **ipv4ll** uses avahi to get an address in the 169.254.X.X range.  I haven't had much luck with avahi - if I see an avahi address, it usually means my DHCP didn't work.

---

### Post by Vaughands on 2008-10-03
Well, in English this means...?

---

### Post by doas777 on 2008-10-03
> **Vaughands said:**
> Interfaces File:




Routing Table:


well whatever the problem is, it occures before the routing table is created. the output of your command indicates that you would not be able to access any other addresses (including loopback). did you set the gateway when you configured your IP address?

---

### Post by Vaughands on 2008-10-03
I'm tempted to just buy a Ubuntu Wifi USB that works out of the box or is KNOWN to work with little effort. Can anyone reccomend one? 

 This thread dosen't seem to be going anywhere.

---

### Post by Vaughands on 2008-10-03
Bump.

---

### Post by arunvir on 2008-10-03
ok ....... I saw your router configuration


Your DHCP provides Ip addresses in range from 

192.168.1.100 to 192.168.1.199

I could see that you have been trying to get it working with the following configuration

> 
iface eth0 inet static
[COLOR="Red"]address 192.168.1.25[/COLOR]
netmask 255.255.255.0
gateway 192.168.1.1




If you try to give a different ip not in range,the router wont recognize your system being part of it........

Your very first configuration image
showing 192.168.1.101 as your ip could be the right one.....

ok, i'm not wrong, your network could be something like this

adslmodem->yourwirelessrouter->yoursystem

ok, something about what you do in windows might be needed.
Do you connect automatically or
give an ip address with accompanied DNS server addresses(I use that)

or do you use connect to and give username and password(PPPoE)


If you just have to connect your ethernet cable and you are able to connect to the internet in windows, then in network manager, just enable DHCP(roaming mode) in ubuntu and there you are ready to work.
> 
vaughan@vaughan-desktop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1b:24:43:81:16
inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::21b:24ff:fe43:8116/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:12 errors:0 dropped:0 overruns:0 frame:0
TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3112 (3.0 KB) TX bytes:4734 (4.6 KB)
Interrupt:16 Base address:0xa000 

Ok the above one shows 2 details.

you have been able to send something and recieve back something

3112 bytes and 4734 bytes.

so the problem could be somewhat different.

ok just check this thing.
goto system->administration->network 

click on wired connection and then properties and then enable roaming mode

Check if DHCP is enabled in your router.

try pinging the gateway
192.168.1.1

if network unreachable
then try disconnecting an reconnecting the cable again

All the Best and reply back with any progress

---

### Post by Iowan on 2008-10-03
> **Vaughands said:**
> Well, in English this means...?Means you might have better luck with "dhcp" or "static".

---

### Post by Vaughands on 2008-10-03
No luck with plugging in and out...

> pvaughan@vaughan-desktop:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.3.159 icmp_seq=1 Destination Host Unreachable
From 169.254.3.159 icmp_seq=2 Destination Host Unreachable
From 169.254.3.159 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3
vaughan@vaughan-desktop:~$ 






The million dollar question, why am I transmitting packets from that address...?

---

### Post by jerome1232 on 2008-10-03
I just want to point something out I noiticed on an earlier post
```
Listening on LPF/eth0/00:1b:24:43:81:16
Sending on LPF/eth0/00:1b:24:43:81:16
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[ OK ]
```

When your interface sent out a dhcp request your router never responded. Does it by chance have some sort of mac filtering setup?

btw a 169.x.x.x address = fail, it's a self assigned private address. I would follow arunvir was getting to, and try and assign a valid static ip address for your network like 192.168.1.180 for example.
put this in your /etc/network/interfaces
> 
iface eth0 inet static
address 192.168.1.180
netmask 255.255.255.0
gateway 192.168.1.1 

---

### Post by Vaughands on 2008-10-03
So I'd replace the old Ipv4all line with those ones?

---

### Post by jerome1232 on 2008-10-03
I can't get a sense of what your file looks like right now from reviewing the thread, can you post the contents of /etc/network/interfaces again for me?
```
cat /etc/network/interfaces
```

---

### Post by Vaughands on 2008-10-03
> auto lo
iface lo inet loopback




auto eth0
iface eth0 inet ipv4ll 

It was a few posts back.

---

### Post by jerome1232 on 2008-10-03
Okay yeah we would want it to look like this then
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.180
netmask 255.255.255.0
gateway 192.168.1.1
```

You could try a few ip's just stay between 192.168.1.100 - 192.168.1.199 it's possible you accidentally choose one in use and it causes problems.

edit: make sure you caught my edit I forgot to add auto eth0, when done try and ping your router again.

---

### Post by arunvir on 2008-10-03
I agree that 169.254.*.* when PC fails to get any IP from router using DHCP.

Whats you laptop model???:confused::confused::confused::confused:

That could also help!!!!!

If nothing works, run the live CD and plug the ethernet cable then and goto

System->administration->networks and click on wired connection and set enable  roaming mode.

Then check whether you are able to access internet then and also try pinging the gateway.

Post back with your results............

---

### Post by Vaughands on 2008-10-03
> vaughan@vaughan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:43:81:16  
          inet addr:192.168.1.180  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:362 (362.0 B)  TX bytes:2747 (2.6 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1400 (1.3 KB)  TX bytes:1400 (1.3 KB)

vaughan@vaughan-desktop:~$ 



 Sorry for being so late, I thought I'd post this output. This is with the static enabled, LiveCD boot is no go.

---

### Post by jerome1232 on 2008-10-03
Were you able to ping your router after setting that static ip up? What about the outside world?

```
ping -c 3 192.168.1.1
ping -c 3 google.com
```

---

### Post by Vaughands on 2008-10-03
Firefox wouldn't connect at all, so I would presume no?

---

### Post by Iowan on 2008-10-03
> **jerome1232 said:**
> You could try a few ip's just stay between 192.168.1.100 - 192.168.1.199 Why? This is the DHCP range. Wouldn't there be less chance of address conflict to *avoid* this range?

Sorry... going off-topic.

---

### Post by Vaughands on 2008-10-03
Pinging router was unsuccessful.

---

### Post by jerome1232 on 2008-10-03
> **Iowan said:**
> Why? This is the DHCP range. Wouldn't there be less chance of address conflict to *avoid* this range?

Sorry... going off-topic.

I guess your right, it would've worked with the 192.168.1.25 address, it's all on the same subnet. Just goes to show I need some caffeine.

At any rate I'm not sure what's going on now, nothing is responding to dhcp requests, assigning static ip information isn't getting him online, if it wasn't for the fact that is working when he boots into windows then I'd be wondering if the cable was even plugged in on both ends...

---

### Post by Vaughands on 2008-10-03
This is complete and utter madness...

---

### Post by Vaughands on 2008-10-03
Bump.

---

### Post by arunvir on 2008-10-04
ok, try a ping thru the interface:-

ping -I eth0 192.168.1.1

must work.

keep everything as roaming..........
right click on the gnome-panel and select "Add to panel" and then the "Network monitor" applet.

and then select eth0 in the name of the interface.

If you are able to see some change in the number of packets sent and recieved = you are reaching till your router, but somehow your router ain't responding to you.

Post back with the results!!

Note:-
Check if you have some kind of MAC Filtering or IP filtering enabled on your router.

---

### Post by Vaughands on 2008-10-04
Grah, I reformatted my Ubuntu install, but now it won't boot :(. I installed just like normal and its alright I suppose.. but when I go to boot it goes to load and then the loading bar locks up.

---

### Post by arunvir on 2008-10-04
How Sweet!!!!!!!!!


Congrats on upgrading your problem from a simple networking one to installation one......

Never mind............
Now that you have decided for re-installation , do try another one and reply back.

---

### Post by arunvir on 2008-10-04
ok, after you do manage a successful installation do try my last set of steps.

One thing...... Never ......... absolutely never go about editing interface files manually.

I have had the worst of all experiences.

---

### Post by Vaughands on 2008-10-05
Yeah, I'm getting some packets.. minimial ones though.

---

### Post by arunvir on 2008-10-05
so your ping -I eth0 192.168.1.1

returns some result............

right

can you post the ping result.........

also please try changing the router ip from 192.168.1.1 to something like 10.x.x.x...........

having the same set of router ip's in your adsl modem and your wireless router could affect your network...........

---

### Post by Vaughands on 2008-10-06
No, it returns nothing. My network monitor shows some packets sent and recieved. That's it. Nothing else will go through, no pings or anything.

Mind you these packets are there on startup.

---

### Post by arunvir on 2008-10-07
ok packet transmission means something is working but not everything is ok.

I'll give you a set of commands........... try them and reply back on whether any progress is made....


sudo ifconfig eth0 down
sudo ifconfig eth0 up 
sudo dhclient eth0

then try pinging again(the gateway only). if not successful then post your ifconfig here. Edit your mode from roaming to static ip in network manager.

ip:-192.168.1.110
mask:-255.255.255.0
gateway:-192.168.1.1


then try pinging the gateway........

using the command:- ping -I eth0 192.168.1.1

Finally try finding out whether you need a crossover ethernet cable. Sometimes even that could be the issue.
or
try changing your gateway ip from 192.168.1.1

to 10.x.x.1 (x can be anything in between 20 and 90(a better range actually))

change your ip address range correspondingly in the router and in your system.

try pinging again and post back with the ifconfig..........

---

