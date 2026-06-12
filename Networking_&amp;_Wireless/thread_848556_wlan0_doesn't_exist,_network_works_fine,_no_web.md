---
title: "wlan0 doesn't exist, network works fine, no web"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by Atokad on 2008-07-03
Okay, I'm the ultra-noob, but usually pretty good at find my backside with both hands and a flashlight;)

Two days ago, installed Ubuntu 8.04 (Hardy), and LOVED it (even the steepish learning curve) on my laptop (specs below).

Today, I learn there's a specific Ubuntu for media creation, etc, called UbuntuStudio 8.04, so I went ahead and installed it.

The Broadcom Driver worked fine for my system (without NDISWrapper), during the Vanilla Ubuntu work, so I expected things to be fine in UbuntuStudio.

Now, the funny things and questions:
1) Why is it I've been able to set up all my automounts/shares, etc, and can access them perfectly FINE with my wireless card... but CANNOT get to any web page in Firefox?

2)Why does my wlan0 tell me "interface does not exist", when I try to configure it?
I don't think I need to go through the NDISWRAPPER issue, as it was working fine earlier.

Any suggestions, please and thanks?!?

Laptop:
Dell Vostro 1500 Laptop (2GB/160/Broadcom/yadda)
(yes, the Broadcom wireless, but its doing its thing fine?)

Router is a NetGear FM114p, and appears tro be doing everythiung fine.

O/S is Dual-Boot WinXP and UbuntuStudio 8.04

I know its not giving you much to work with, yet, but I assume you'll have me type a few commands and reply with the results. I'm willing to "work the problem"... just a little dazed that I can read anything through the network, except the internet!

Dave

---

### Post by pytheas22 on 2008-07-03
It could be a DNS problem or something weird going on with the network.  Please post the output of these commands:
```

iwconfig
ifconfig
host google.com
wget google.com
wget 64.233.187.99
```

These should help narrow down the problem.

---

### Post by Atokad on 2008-07-03
Thanx for the quick reply pytheas!
Sorry for the wait (had to let the failures timeout).

Here's the results of your code lines:
---------------------------------------------------
me@MyComp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"CapnBlyOne"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:09:5B:2D:1E:F6   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=96/100  Signal level=-37 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-------------------------------------------------------------

me@MyComp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:c2:57:7a  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fec2:577a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2911 (2.8 KB)  TX bytes:1812 (1.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1834 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93634 (91.4 KB)  TX bytes:93634 (91.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:46:68:fa  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe46:68fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1101097 (1.0 MB)  TX bytes:299881 (292.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-4C-46-68-FA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

-----------------------------------------------------

me@MyComp:~$ host google.com
;; connection timed out; no servers could be reached
dave@BlyBook:~$ wget google.com
--16:24:19--  [http://google.com/](http://google.com/)
           => `index.html'
Resolving google.com... failed: Name or service not known.

--------------------------------------------------------

me@MyComp:~$ wget 64.223.187.99
--16:25:33--  [http://64.223.187.99/](http://64.223.187.99/)
           => `index.html'
Connecting to 64.223.187.99:80... failed: Connection timed out.
Retrying.

-----------------------------------------

Any clues in there?

---

### Post by pytheas22 on 2008-07-03
Yes, it does look like a DNS issue.  What does:
```

cat /etc/resolv.conf
```

tell you?

And do you know the IP addresses for your DNS servers?  These should be supplied by your ISP, or if you have Windows computers on your network, use the ipconfig /all command and it should show you the DNS server addresses somewhere in the output.

---

### Post by Atokad on 2008-07-03
Really appreciate your help, here!

The "cat" line results in:
"No such file or Directory"

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\xxxxxxxxx>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : capnbly
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : rochester.rr.com

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : rochester.rr.com
        Description . . . . . . . . . . . : Realtek RTL8168/8111 PCI-E Gigabit E
thernet NIC
        Physical Address. . . . . . . . . : 00-18-F3-63-AC-C5
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.3
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 24.92.226.40
                                            24.92.226.41
                                            24.92.226.9
        Lease Obtained. . . . . . . . . . : Thursday, July 03, 2008 3:06:25 PM
        Lease Expires . . . . . . . . . . : Sunday, July 06, 2008 3:06:25 PM
-------------------------------

I owe you one, one day when I'm gooder at this ;)

---

### Post by Atokad on 2008-07-03
The fresh data is from rebooting the router, earlier.
It's a NetGear FM114P, and I'm using 128-bit WEP on the WLAN 
(rest of machines are LAN)

Dave

---

### Post by Atokad on 2008-07-03
While browsing some Forums I stumbled across a link that shows how to set DNS Servers to something other than the standard ISP ones.

[http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Anyway, I told myself I'd go have a peek at that file (and swore I'd not touch anything until I heard back from you, lol)... 

Here's what I found
(contents of /etc/dhcp3/dhclient.conf)

[COLOR="DarkRed"]request subnet-mask, broadcast-address, time-offset, routers, domain-name,  domain-name-servers, host-name, ntp-servers;[/COLOR]

A little odd to have a config file all blanks, isn't it?

Thought maybe the info would help you helping me.

I'll be nearby ;)

---

### Post by pytheas22 on 2008-07-03
> A little odd to have a config file all blanks, isn't it?

No, actually mine is blank too, so I guess it's supposed to be that way.  But to be honest I'm not sure what that file is for.

What I do know for sure is that there's a problem if /etc/resolv.conf doesn't exist; that's where Ubuntu looks to figure out how it should resolve domain names (i.e., figure out which IP addresses "google.com" represents).  Try creating it and entering the right information:
```

sudo gedit /etc/resolv.conf
```

A blank file will open.  Add in the line:
```

nameserver 24.92.226.40
```

Then save the file and run the command:
```

/etc/init.d/networking restart
```

and see if you can use the Web (you may need to reconnect to your wireless network first).

---

### Post by Atokad on 2008-07-03
pytheas...

as my mom said, "When you're good, it ain't braggin'!"

Well Done, Man! It worked right off, then I've just made it survive a reboot just to double-check... seems fine and dandy.

Is there more left we need to take care of?
If so, I'm here.

If you want to explain any of what you did (I'm already hip to sudo, gedit, and basics), I'd be glad to learn more.  

If not, or you're busy helping somebody else out (or having a life), I'm sure I'll run into you again.

Many Thanks

Dave

---

### Post by chili555 on 2008-07-03
> request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, host-name, ntp-servers;These are not 'empty.' They tell the DHCP process to retrieve all those things from the DHCP server, generally your router or access point. So, when 'sudo dhclient wlan0' runs, dhclient is supposed to grab DNS servers. Did you get > inet addr:192.168.0.5via DHCP or did you set up a static IP address? Static assumes the user will provide the DNS server addresses, not the router.

---

### Post by Atokad on 2008-07-03
Roger on the "emtpy" (thought maybe that was the "request" idea, Chili.

That IP is via DHCP (let the router pick), as my router has static ability on LAN, but not WAN (or I've not found it).

Dave

---

### Post by pytheas22 on 2008-07-03
As for what I did:

I just had you tell the system which server to connect to for resolving domain names.  Usually it figures that out automatically, although I'm not sure how--as per chili555's comments, it sounds like maybe that's where /etc/dhcp3/dhclient.conf comes in.  But in your case it didn't know where the DNS servers were for whatever reason.  So you opened the file that's supposed to tell Ubuntu where to look for DNS servers, /etc/resolv.conf.  And you added the line to tell it that there is a DNS server (aka nameserver) at the IP address 24.92.226.40.  The /etc/init.d/networking restart command just refreshes your networking to that the new settings could take effect--a reboot of the computer would have done the same thing, but this isn't Windows, so we try not to reboot every other time we click the mouse:)

Anyway, I'm glad it's fixed, and have fun with Ubuntu.

---

