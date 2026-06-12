---
title: "&quot;No Network Connection&quot;, but router is assigning IP and ifconfig shows no problems"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by thing-fish on 2008-05-17
Wow, I'm stumped and hope someone can provide assistance.  I applied updates to Xubuntu 8.04 Hardy a couple of days ago and it indicated that I may need to restart.  I restarted, and now ifconfig looks OK, but I the box can't see the LAN or WLAN and the WLAN and LAN can't see the box.  The router has assigned the correct IP via DHCP and ifconfig output looks correct.

Any ideas?  Do I need to post more information?  Thanks for any assistance, this is killing me!

---

### Post by chili555 on 2008-05-17
How about letting us see *ifconfig*? Thanks.

---

### Post by thing-fish on 2008-05-17
> **chili555 said:**
> How about letting us see *ifconfig*? Thanks.

Sure!  Thanks for the assist!  Here goes (typing it out)

eth0 Link encap:Ethernet HWaddr 00:e0:7d:92:81:a3
inet addr:192.168.1.3 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::230:7dff:fe92:81a3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets: 30015 errors:0 dropped:0 overruns:0 frame:0
TX packates:10485 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2048980 (1.9 MB) TX bytes:1305164 (1.2 MB)
Interrupt:10 Base address:0xe000

lo Link encap:Local loopback
inet addr:127.0.0.1 Mast 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:180 (180.0 B) TX bytes:180 (180.0 B)

---

### Post by chili555 on 2008-05-17
Your *ifconfig* looks fine. Is this:> the box can't see the LAN or WLAN and the WLAN and LAN can't see the box.really a samba problem? Was your */etc/samba/smb.conf* rewritten by the updates?

All my machines are some flavor of Linux, so I have run out of ideas at the door to samba.

---

### Post by thing-fish on 2008-05-17
> **chili555 said:**
> Your *ifconfig* looks fine. Is this:really a samba problem? Was your */etc/samba/smb.conf* rewritten by the updates?

All my machines are some flavor of Linux, so I have run out of ideas at the door to samba.

It's not just Samba.  Xubuntu actually has a little icon at the top with an X and when I mouseover it I see "No Network Connection."  When I open Firefox or try to use other internet things, no-go.  Pinging it from inside the network works OK.  I have two apps running with http interfaces, and I can get to one but not the other.  

It's so weird again, literally everything was fine, then I rebooted after updates, and now I have this weirdness.  I just don't even know where to look to solve this and am pulling my hair out!

---

### Post by chili555 on 2008-05-17
Weird, indeed! Please let us see:```
ping -c3 192.168.1.1
ping -c3 74.125.47.104
cat /etc/resolv.conf
```Thanks.

---

### Post by thing-fish on 2008-05-17
> **chili555 said:**
> Weird, indeed! Please let us see:```
ping -c3 192.168.1.1
ping -c3 74.125.47.104
cat /etc/resolv.conf
```Thanks.

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.656 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.594 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.596 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.594/0.615/0.656/0.035 ms


PING 74.125.47.104 (74.125.47.104) 56(84) bytes of data.
64 bytes from 74.125.47.104: icmp_seq=1 ttl=242 time=39.1 ms
64 bytes from 74.125.47.104: icmp_seq=2 ttl=242 time=37.8 ms
64 bytes from 74.125.47.104: icmp_seq=3 ttl=242 time=35.8 ms

--- 74.125.47.104 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 35.884/37.619/39.163/1.364 ms


search nycap.rr.com
nameserver 208.67.222.222
nameserver 208.67.220.220


On that last one, note that I'm wasn't familiar with resolv,conf, but I recognize those as my opendns dns settings.

And an update: at some point during this trouble Firefox had somehow gotten into offline mode, and that setting persisted.  I just now put it in online mode and am in fact posting this message from my Xubuntu box.  However, the icon in the top right corner of the screen *still* has the red X in it and *still* says No Network Connection when I mouseover.

Cripes, is it possible that in the last update this thing is showing me that it can't find the wireless network? (I don't have a wireless card in this computer).  When I left-click, "no network devices have been found" is greyed out, and "manual configuration" is there to click on.  When I right click, "Enable Networking" is checked, "Connection Information" is greyed out and "Edit Wireless Networks" (and About) is there to click on.  Note that clicking Edit Wireless Networks does indeed bring up a Wireless Networking dialog that does not list any wireless networks.

---

### Post by chili555 on 2008-05-18
Well, your ping results show you are connected to the router, and you are able to get to the internet. The IP address 74.125.47.104 is Google. Let's try tweaking *resolv.* Please *sudo gedit /etc/resolv.conf* to make it look like:```
#search nycap.rr.com
nameserver 208.67.222.222
nameserver 208.67.220.220
```Then see if you can:```
ping -c3 www.google.com
```Can you now surf the web?

---

