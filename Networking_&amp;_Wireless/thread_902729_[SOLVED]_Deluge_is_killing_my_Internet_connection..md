---
title: "[SOLVED] Deluge is killing my Internet connection..."
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by mb_webguy on 2008-08-27
I'm using Deluge 0.9.07 (1.0.0_RC7), and a wireless card using ndiswrapper.  At home, Deluge works just fine, but I'm currently on vacation and behind a router I don't control, so I don't have port forwarding set up.  This usually just means that downloads are slower than usual, but instead it will connect for a short time (with the expected slower than usual but acceptable speeds) but within 5 minutes kills my connection.  

And by "kills my connection", I mean I can't connect to anything (though I still seem to be connected to the WLAN), and can't re-establish my connection without a reboot.  The network manager applet shows good signal strength, but I can't connect to any peers in Deluge, can't load web pages in my browser, etc.  Reconnecting to the WLAN doesn't help (though the network manager applet seems to be indicating that I can), and neither does restarting networking, either using the network manager applet or with "sudo /etc/init.d/networking restart".

I've tried lowering the max upload and download speeds in Deluge, but that doesn't seem to help.

Here's the output of iwconfig after the connection is fubared:```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"SEACOVE1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:F0:EB:36:FD   
          Bit Rate=78 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And here's the output of ifconfig after the connection is fubared:```
matt@the-tardis:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:99:32:6b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60381 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12363166 (11.7 MB)  TX bytes:12363166 (11.7 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:ac:e8:9a  
          inet addr:192.168.0.155  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:feac:e89a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63432784 (60.4 MB)  TX bytes:17252733 (16.4 MB)
          Interrupt:17 Memory:f9ffc000-fa000000 

```
If I reconnect to the WLAN after Deluge nukes the connection, smbtree will show other computers on the network, but I still can't connect to the Internet, and get no response when pinging the router.

I was originally thinking that the router might have some sort of bandwidth limiting policy in effect, and is blocking my computer from connecting if I download more than a certain amount within a given period of time, but that doesn't explain why I have to reboot before I can reconnect to the Internet...  I've also tried connecting to a couple of other available wireless networks, and while I seem to be able to connect (although the signal strength is extremely weak), I still can't connect to the Internet (though I have no idea whether these other networks have an Internet connection in the first place).

I'd really like to get Deluge working here, but I'm out of ideas...

---

### Post by arch0njw on 2008-08-27
Are you getting a different IP each time you reboot?  It could be that you are getting blocked if they don't want people taking up a lot of bandwidth.

Have you also tried ifdown/ifup on wlan0?

---

### Post by prshah on 2008-08-27
> **mb_webguy said:**
> I was originally thinking that the router might have some sort of bandwidth limiting policy in effect, 

I think so too; from the name of the wireless router, looks like you're having a nice, sunny holiday!

You are possibly getting a different IP every time you reboot; and this is probably why the wireless network works after you reboot. Try this: (for confirmation) the next time the connection goes dead, open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo dhclient wlan0
``` This should release the old IP address and request a new one; does the Internet work after this command? (You may have to wait a couple of minutes for the new settings to take effect; no reboot!)

---

### Post by mb_webguy on 2008-08-27
Ok, here is the result of ifdown/ifup.  I *think* I used the command correctly...```
matt@the-tardis:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
matt@the-tardis:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
```
Needless to say from the output, it didn't help any.

And here is the result of dhclient, after rebooting and allowing Deluge to nuke the connection again.```
matt@the-tardis:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 8293
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1c:26:ac:e8:9a
Sending on   LPF/wlan0/00:1c:26:ac:e8:9a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
I waited 5 minutes, but still no connection.  So I restarted networking, reconnected to the WLAN, and tried dhclient again, but with the same results...

:confused:

---

### Post by mb_webguy on 2008-08-27
> I think so too; from the name of the wireless router, looks like you're having a nice, sunny holiday!

Yep, I'm in Florida!  We got here Sunday night just after Fay passed through, so the first day or two were a bit stormy.  But the last two days have been beautiful, and we practically have the beaches to ourselves, since most people don't think to go on vacation when people are talking about hurricanes...

---

### Post by mb_webguy on 2008-08-27
Ok... I solved the problem.  I still don't know why it was so difficult to fix the connection after Deluge killed it, but after lowering the max connections, max half-open connections, and max connection attempts per second in Deluge to (very) low settings, Deluge is no longer causing my connection to die.

Thanks for the replies!

---

### Post by TylerMD on 2008-12-18
Can you post your new settings please?

---

### Post by mb_webguy on 2008-12-21
I'm using version 1.0.7 of Deluge.  Versions prior to 1.0 will have different settings than those listed below.

Max connections: 200
Max upload slots: 4
Max download speed: 350 KiB/s
Max upload speed: 30 KiB/s
Max half-open connections: 50
Mac connection attempts per second: 10

Per torrent settings all at -1 (unlimited)

This is for a low-end cable broadband connection, so your upload and download speeds may differ depending on your connection speed.  This is also for a Belkin F5D7231-4 wireless router.  Yours may be able to handle more or fewer connections.  

Also, while these settings don't kill my connection outright (as was happening previously), they are apparently close to my router's limits and running Deluge will still cause all other network traffic (like web browsing) to slow to a crawl if I'm getting a lot of bittorrent connections.  I've thought about lowering these settings a bit more, but I'm getting *really* good download speeds with Deluge now.  Since I usually leave Deluge running at night and shut it down during the day, it's not really a problem for me that Deluge is using all of the available bandwidth.

Also, my related networking problems (i.e. the difficulty re-establishing a connection after my router crapped out) haven't recurred since upgrading to Intrepid...

---

### Post by krychek on 2008-12-22
I'm having the same issue. Deluge kills both my ADSL and my wifi connections. I only use a router for the wifi connection. However I only suspect Deluge is causing all this. The connect automatically option is ticked in network manager. So why doesn't it connect back automatically? Do I have to tick "system setting" as well? I don't know what that is.

Is this issue reported on Launchpad?

---

### Post by krychek on 2008-12-23
Lowering the number of connections doesn't help me. This issue also happens with Transmission. I've filed a new bug report on Launchpad:
[https://bugs.launchpad.net/bugs/310035](https://bugs.launchpad.net/bugs/310035)

---

### Post by mrsudo on 2009-01-12
I'm having the same problem, with a d-link DIR 615.

I've just changed my connection limits as i've seen that is helping for most.  I am 100% sure deluge is the problem because for the last month, every time i have opened deluge, roughly 5 minutes late (or even less) i cannot access the web whatsoever.  No ping, no local contact ...

I would switch bt clients, but i <3 deluge :)

---

### Post by krychek on 2009-01-12
mrsudo: I started to create a bug report, but it's not complete yet, so I set it to incomplete. You could write your experiences there: 

[https://bugs.launchpad.net/bugs/310035](https://bugs.launchpad.net/bugs/310035)

---

