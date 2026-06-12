---
title: "Ubuntu and the AT&amp;T USBconnect 881"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by gmanigault on 2008-08-21
I figure that this is the place to post this.  I have seen limited articles on the web referencing this issue with no ultimate solution. 


I have the following problem.  I have and AT&T aircard usb 881.  It is manufactured by Sierra Wireless.  THe OS is Ubuntu 8.04 Desktop.  Version 2.6.24.19. This version already has the drivers for AT&T installed.  I called AT&T for a simple thing which was the first mistake and all I wanted was the ip addresses of their nameservers for their nameserver.   They didn't help.  

Well after all that and some script mods etc, I am probably about and inch away from getting it to work.  Here is the problem,  I get a remote ip address of 10.64.64.64 which is incorrect.  I tried this with Windows and did and ipconfig /all to get a list of the ip info. 

Windows Info:
==============
IP - 32.176.61.13
Default GW - 32.176.61.13
DHCP Server - 32.176.61.253
DNS Server - 209.183.50.151
             209.183.54.151

Linux Info:
==============

Route:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0

tracepath -n 1.1.1.1

1:  32.176.47.244     0.270ms pmtu 1500
 1:  no reply
 2:  172.26.248.2    233.232ms 
 3:  172.16.1.210    168.936ms 
 4:  12.87.42.165    189.930ms !H
     Resume: pmtu 1500 

GSM connect results:

Starting Sierra Wireless GSM connect script...



Setting the abort string



Initializing modem



Setting APN



Dialing...

Serial connection established.
using channel 5
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xaf889baf> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x10 <asyncmap 0x0> <auth chap MD5> <magic 0x6312c602> <pcomp> <accomp>]
sent [LCP ConfNak id=0x10 <auth pap>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xaf889baf> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x11 <asyncmap 0x0> <auth pap> <magic 0x6312c602> <pcomp> <accomp>]
sent [LCP ConfAck id=0x11 <asyncmap 0x0> <auth pap> <magic 0x6312c602> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xaf889baf]
sent [PAP AuthReq id=0x1 user="gmanigault-D1520laptop" password=<hidden>]
rcvd [LCP DiscReq id=0x12 magic=0x6312c602]
rcvd [LCP EchoRep id=0x0 magic=0x6312c602 af 88 9b af]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [LCP ProtRej id=0x13 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfReq id=0x8]
sent [IPCP ConfNak id=0x8 <addr 0.0.0.0>]
rcvd [IPCP ConfRej id=0x3 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x4 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfReq id=0x9]
sent [IPCP ConfAck id=0x9]
rcvd [IPCP ConfNak id=0x4 <addr 166.128.200.180> <ms-dns1 209.183.50.151> <ms-dns3 209.183.54.151>]
sent [IPCP ConfReq id=0x5 <addr 166.128.200.180> <ms-dns1 209.183.50.151> <ms-dns3 209.183.54.151>]
rcvd [IPCP ConfAck id=0x5 <addr 166.128.200.180> <ms-dns1 209.183.50.151> <ms-dns3 209.183.54.151>]
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 166.128.200.180
remote IP address 10.64.64.64
primary   DNS address 209.183.50.151
secondary DNS address 209.183.54.151
Script /etc/ppp/ip-up started (pid 16125)
Script /etc/ppp/ip-up finished (pid 16125), status = 0x0
Terminating on signal 2
Connect time 15.4 minutes.
Sent 11522 bytes, received 672 bytes.
Script /etc/ppp/ip-down started (pid 17069)
sent [LCP TermReq id=0x2 "User request"]
rcvd [LCP TermAck id=0x2]
Connection terminated.
Script /etc/ppp/ip-down finished (pid 17069), status = 0x0

Serveral thinkgs that I have noticed are as follows.

1.  The ip address given is much different than that windows environment.

     Windows IP = 32.176.61.13
     Linux IP = 166.128.200.180

2.  Linux will not allow you to ping anything such as [www.google.com](www.google.com).  No URLs are accessible.  

3.   Does anyone know how to make the script receive or ignore the remote IP address?


Gary Manigault
[email]gwsharkcom@gmail.com[/email]

Any help would be appreciated.  Once resolved I will publish all the info on how to do it.

Thanks.

---

### Post by nixscripter on 2008-08-22
My obivous question is: where did the 10.64.64.74 entry in the routing table come from?

Try these:

1. Check **/etc/network/interfaces** to make sure you're not setting an IP automatically. This is unlikely.

2. What does **ifconfig ppp0** show when disconnected? Does it have an **inet** address (not ipv6, that doesn't really matter).

3. Is that IP in the /etc/ppp/ip-up script it is executing?

In any case, I would also suggest next time try a simple fix: change your gateway to the windows Default GW before you connect, like this:

```

sudo del default
sudo route add default gw **win.gateway.ip.here **

```

I also wonder about that 10.64.64.64, but I haven't used PPP, so I don't want to recommend editing that.

---

### Post by gmanigault on 2008-08-22
1.  No, I am not setting up a ip automatically.  

=====[snippet]
interfaces

auto lo
iface lo inet loopback

=====[snippet]


2.  No there is not ppp0 interface when the aircard is not present. 

3.  Here is the ifconfig ppp0.

=====[snippet]

 ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:166.128.237.192  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:1 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:90 (90.0 B)  TX bytes:123 (123.0 B)
=====[snippet]

Any ideas on where to go from here.  This shouldn't be necessary but it is.  They make everything for a windows environment not for a real OS user. 

Gary

Thanks.  

> **nixscripter said:**
> My obivous question is: where did the 10.64.64.74 entry in the routing table come from?

Try these:

1. Check **/etc/network/interfaces** to make sure you're not setting an IP automatically. This is unlikely.

2. What does **ifconfig ppp0** show when disconnected? Does it have an **inet** address (not ipv6, that doesn't really matter).

3. Is that IP in the /etc/ppp/ip-up script it is executing?

In any case, I would also suggest next time try a simple fix: change your gateway to the windows Default GW before you connect, like this:

```

sudo del default
sudo route add default gw **win.gateway.ip.here **

```

I also wonder about that 10.64.64.64, but I haven't used PPP, so I don't want to recommend editing that.

---

### Post by gmanigault on 2008-08-23
**[SIZE="4"]Well I got it to work.  Will publish all here once I write it it.   To make it short use kppp not the pppd that you may have.  I think there might be a version issue with pppd.  If you need more let me know.  There is more to come. [/SIZE]**

---

### Post by gmanigault on 2008-08-23
Well I was having problems with the AT&T 881 Usbconnect using Linux Ubuntu 8.04.   I was not able to get it to work using the pppd call gsm statement. AT&T as usual was no help.  Asked them a simple questions like [ie. what is the ip addresses of your nameservers?].  They call that support and never gave me the addresses. 

Well enough about that.  Lets get to how to make the AT&T Sierra Wireless USBconnect 881 work.   It is made to work for windows, load itself and software in the windows environment.   I thought doing that first and doing and ipconfig / all and gathering all the necessary info would help but that didn't work.  


Steps:

1.  Do a [uname -a].  This will give your the version on Linux you are using.  Mine was:

	  2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

2.  Do a [modinfo sierra].  This will tell you the version of the USB driver if it is installed. 

3.  Either use under applications add/remove and install kppp or do and apt-get install kppp. Once these are insalled you will be able to start configuring it. 

4.  Use the following for UID and password.

	UID - [email]ISPDA@CINGULARGPRS.COM[/email]
	PW  - CINGULAR1
5.  Configuration


	Account - Phone number  - *99#
		Authentication -  PAP/CHAP
		IP - Dynamic IP
		Gateway - Default Gateway
		DNS - Automatic
		
	Modems - Device - Set Name
		Modem device  -  Mine is  /dev/ttyUSB0		Note:  Yours may differ
		Flow Control  - Hardware [CRTSCTS]
		Line Termination - CR
		Connection Speed - I set it to the highest.  It should default to its highest. 

That should do it.  You should then be able to get online.  Good luck. I am going to play with the connect speed to see how I might be able to tweak it.  More to come.  

If you have question email me but be patient. 

[email]gwsharkcom@gmail.com[/email]


Gary M.
gwshark

---

### Post by nixscripter on 2008-08-23
Sounds great. You might also want to mark this thread as solved, and perhaps write a separete HOWTO once you've got it all figured out.

---

### Post by gmanigault on 2008-08-23
How do I mark the thread as resolved?


> **nixscripter said:**
> Sounds great. You might also want to mark this thread as solved, and perhaps write a separete HOWTO once you've got it all figured out.

---

### Post by gmanigault on 2008-08-23
When I write the HOWTO is there a place to post it or just post it here?

> **nixscripter said:**
> Sounds great. You might also want to mark this thread as solved, and perhaps write a separete HOWTO once you've got it all figured out.

---

### Post by nixscripter on 2008-08-23
I would suggest posting a separate HOWTO thread and linking to it from this one.

---

### Post by nick cellular on 2008-08-23
I am seeing the same problem and unfortunately the kppp setup does not work. The only differences is my config is using "wap.cingular" as my APN and my UID is "wap@cingulargprs.com"

Any ideas?

from /var/log/messages
```

Aug 23 19:15:50 laptop pppd[32438]: pppd 2.4.4 started by user, uid 1000
Aug 23 19:15:50 laptop pppd[32438]: Using interface ppp0
Aug 23 19:15:50 laptop pppd[32438]: Connect: ppp0 <--> /dev/ttyUSB0
Aug 23 19:15:50 laptop pppd[32438]: CHAP authentication succeeded
Aug 23 19:15:50 laptop pppd[32438]: CHAP authentication succeeded
Aug 23 19:15:57 laptop pppd[32438]: Could not determine remote IP address: defaulting to 10.64.64.64
Aug 23 19:15:57 laptop pppd[32438]: local  IP address 10.126.51.48
Aug 23 19:15:57 laptop pppd[32438]: remote IP address 10.64.64.64
Aug 23 19:15:57 laptop pppd[32438]: primary   DNS address 10.11.12.13
Aug 23 19:15:57 laptop pppd[32438]: secondary DNS address 10.11.12.14

```

Noticed after I setup GnomePPP to do the connection I get actual DNS but still incorrect IP for ppp0.


```

# tail /var/log/messages
Aug 23 19:23:36 laptop pppd[3547]: pppd 2.4.4 started by user, uid 1000
Aug 23 19:23:36 laptop pppd[3547]: Using interface ppp0
Aug 23 19:23:36 laptop pppd[3547]: Connect: ppp0 <--> /dev/ttyUSB0
Aug 23 19:23:36 laptop pppd[3547]: CHAP authentication succeeded
Aug 23 19:23:36 laptop pppd[3547]: CHAP authentication succeeded
Aug 23 19:23:40 laptop pppd[3547]: Could not determine remote IP address: defaulting to 10.64.64.64
Aug 23 19:23:40 laptop pppd[3547]: local  IP address 10.126.17.34
Aug 23 19:23:40 laptop pppd[3547]: remote IP address 10.64.64.64
Aug 23 19:23:40 laptop pppd[3547]: primary   DNS address 172.18.145.103
Aug 23 19:23:40 laptop pppd[3547]: secondary DNS address 172.18.145.103

```

```

# ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.126.17.34  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:110 (110.0 B)  TX bytes:185 (185.0 B)

```

---

### Post by gmanigault on 2008-08-25
They using this uid and password. 

UID - [email]ISPDA@CINGULARGPRS.COM[/email]
PW - CINGULAR1

THat is what I found to work.  This is not a personal uid and pw that was assigned to me.  

Let me know if that works.


> **nick cellular said:**
> I am seeing the same problem and unfortunately the kppp setup does not work. The only differences is my config is using "wap.cingular" as my APN and my UID is "wap@cingulargprs.com"

Any ideas?

from /var/log/messages
```

Aug 23 19:15:50 laptop pppd[32438]: pppd 2.4.4 started by user, uid 1000
Aug 23 19:15:50 laptop pppd[32438]: Using interface ppp0
Aug 23 19:15:50 laptop pppd[32438]: Connect: ppp0 <--> /dev/ttyUSB0
Aug 23 19:15:50 laptop pppd[32438]: CHAP authentication succeeded
Aug 23 19:15:50 laptop pppd[32438]: CHAP authentication succeeded
Aug 23 19:15:57 laptop pppd[32438]: Could not determine remote IP address: defaulting to 10.64.64.64
Aug 23 19:15:57 laptop pppd[32438]: local  IP address 10.126.51.48
Aug 23 19:15:57 laptop pppd[32438]: remote IP address 10.64.64.64
Aug 23 19:15:57 laptop pppd[32438]: primary   DNS address 10.11.12.13
Aug 23 19:15:57 laptop pppd[32438]: secondary DNS address 10.11.12.14

```

Noticed after I setup GnomePPP to do the connection I get actual DNS but still incorrect IP for ppp0.


```

# tail /var/log/messages
Aug 23 19:23:36 laptop pppd[3547]: pppd 2.4.4 started by user, uid 1000
Aug 23 19:23:36 laptop pppd[3547]: Using interface ppp0
Aug 23 19:23:36 laptop pppd[3547]: Connect: ppp0 <--> /dev/ttyUSB0
Aug 23 19:23:36 laptop pppd[3547]: CHAP authentication succeeded
Aug 23 19:23:36 laptop pppd[3547]: CHAP authentication succeeded
Aug 23 19:23:40 laptop pppd[3547]: Could not determine remote IP address: defaulting to 10.64.64.64
Aug 23 19:23:40 laptop pppd[3547]: local  IP address 10.126.17.34
Aug 23 19:23:40 laptop pppd[3547]: remote IP address 10.64.64.64
Aug 23 19:23:40 laptop pppd[3547]: primary   DNS address 172.18.145.103
Aug 23 19:23:40 laptop pppd[3547]: secondary DNS address 172.18.145.103

```

```

# ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.126.17.34  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:110 (110.0 B)  TX bytes:185 (185.0 B)

```

---

### Post by scrubsJA on 2008-08-26
My installation was working perfectly until a used a crossover cable to try to share internet connection with another machine running xubuntu.

I could not get the computers to share connection. 

Now my ubuntu machine cannot connect to the internet. I also have tried setting up the xubuntu machine and it cannot connect either. I even tried kppp and it does not work.

Both LEDs on the modem come on, and stay lit.

I normally use ppp0 under network connection to connect to the internet.

What can I do to get my internet going again? Can I totally wipe out the network settings remove the modem driver, chat files etc. and start over again? 

I am a novice any help would be appreciated, thanks.

---

### Post by nixscripter on 2008-08-26
I suspect that the network manager messed you up when it detected the ethernet cable. It said, "oh, the internet is over that cable," and messed up all the routing tables.

Try turning off the ethernet interface, and see if that helps: ```
sudo ifconfig eth0 down
``` or whatever interface the card is.

---

### Post by scrubsJA on 2008-08-27
nixscripter

sudo ifconfig eth0 down does not work. Can you instruct me how to uninstall the sierra driver, ppp scripts and restore the network configuration to default?

---

### Post by nick cellular on 2008-08-27
gmanigault

Can you please post your ifconfig on ppp0 and your routes?

So the output from 
```

ifconfig ppp0

```
and
```

sudo route -n

```

Well I think I figured out the problem. I booted with the Hardy CD and it works fine there so it must be my custom kernel OR it is the fact I used WICD instead of networkmanager-applet

---

### Post by nixscripter on 2008-08-28
I would think if you just rebooted, it would forget about the routing tables. If that didn't work, I suppose I was wrong. :neutral:

---

### Post by scrubsJA on 2008-08-28
After rebooting my settings are still messed up. 

lsusb shows the sierra modem as installed and attached to ttyUSB2. 

I have been trying to use network manager to use the modem to connect.

I believe my IP tables got messed up. NB: both lights on the modem are constantly on once I boot up even after doing

Code:

sudo ifconfig eth0 down

HELP!!!

---

### Post by nick cellular on 2008-08-28
Its amazing that everything looks like it works but it doesn't :(

---

### Post by scrubsJA on 2008-08-29
My ifconfig:

ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:db:e9:39:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111512 (108.8 KB)  TX bytes:111512 (108.8 KB)


ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          POINTOPOINT NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:2 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:16 (16.0 B)  TX bytes:143 (143.0 B)

---

### Post by nixscripter on 2008-08-29
In that case, try: ```
sudo ifconfig eth1 down
```

And as for your iptables, I don't think they would have anything in them. If the interface ppp0 isn't up, they won't show anything.

---

### Post by cigtoxdoc on 2008-09-16
I thought I had posted a similar question a few hours ago, but it seems to have been wiped out.  Perhaps I missed the "howto" mentioned above, but where do I find step-by-step to make my AT&T USBconnect 881 device work with a standard desktop PC running Ubuntu?  In particular, what progrrams do I need to have on Ubuntu?  Ubuntu PC at location that does not have DSL, cable, etc.

John

---

### Post by sr20ve on 2008-09-19
> **cigtoxdoc said:**
> I thought I had posted a similar question a few hours ago, but it seems to have been wiped out.  Perhaps I missed the "howto" mentioned above, but where do I find step-by-step to make my AT&T USBconnect 881 device work with a standard desktop PC running Ubuntu?  In particular, what progrrams do I need to have on Ubuntu?  Ubuntu PC at location that does not have DSL, cable, etc.

John


Yes, I am still having the same problem with my remote ip defaulting to 10.64.64.64 and I get no connectivity. I've tried pppd, pon cingular and kppp. I get the same output in /var/log/messages each time...

> Sep 19 20:06:02 johnny-laptop pppd[7775]: pppd 2.4.4 started by root, uid 0
Sep 19 20:06:02 johnny-laptop pppd[7775]: Using interface ppp0
Sep 19 20:06:02 johnny-laptop pppd[7775]: Connect: ppp0 <--> /dev/ttyUSB2
Sep 19 20:06:02 johnny-laptop pppd[7775]: CHAP authentication succeeded
Sep 19 20:06:02 johnny-laptop pppd[7775]: CHAP authentication succeeded
Sep 19 20:06:05 johnny-laptop pppd[7775]: Could not determine remote IP address: defaulting to 10.64.64.64
Sep 19 20:06:05 johnny-laptop pppd[7775]: local  IP address 166.128.165.99
Sep 19 20:06:05 johnny-laptop pppd[7775]: remote IP address 10.64.64.64
Sep 19 20:06:05 johnny-laptop pppd[7775]: primary   DNS address 209.183.50.151
Sep 19 20:06:05 johnny-laptop pppd[7775]: secondary DNS address 209.183.54.151


That output shows /dev/ttyUSB2, but I get the same results with /dev/ttyUSB0.

johnny@johnny-laptop:~$ uname -a
Linux johnny-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

---

### Post by cigtoxdoc on 2008-09-19
I know what happens if I plug the USBconnect 881 into a USB port of a PC running XP Pro SP3.  It just about installs itelf.

What should I expect, if anything, to happen when I plug the 881 into the USB port of a PC running Ubuntu.  I have installed kppp and pppd.

John

---

### Post by GWBouge on 2008-10-01
I'm not sure if y'all have gotten it working yet, but I had similar problems, so I'm going to go ahead and go through the steps it took.  I'm running Ubuntu 8.04 (2.6.24-19) with the Sierra 881u.  I'm still a linux newbie myself (about one month in?), but I hope this helps.

===============================

1) Installed the Sierra drivers with the downloads and instructions from [here]("http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1076").  Note:  I HAD to install kppp to get it working correctly ... using pppd and the gnome ppp tool did not work.

2) I used [this]("http://ubuntuforums.org/showthread.php?t=91370") tutorial to share the internet connection between this (Ubuntu) computer and a Vista desktop through a hub.  It worked great, however I found that I had to re-do steps 1, 2, and 5 after each boot, else I could not connect to the internet.  kppp would still connect, but I guess the iptables kept messing up on boot, so it wouldn't let me through.  which leads me to ...

3) I set the network manually using the GUI Network Settings app (left-click on the network icon in tray -> Manual Configuration).  Unlock, click on wired connection, click on properties.  My settings are as follows:

Disable roaming mode
Configuration -> Static IP
IP address -> 192.168.0.1
Subnet -> 255.255.255.0
Gateway -> [empty]

4) I installed [Firestarter]("http://www.howtogeek.com/howto/ubuntu/install-the-firestarter-firewall-on-ubuntu-linux/").  Here's my initial configuration settings:

Detected device -> Dialup device (ppp0)
Start on dial-out -> check
DHCP -> no check

Enable ICS -> check
LAN device -> eth0

===============================

I tried having Firestarter run at startup, but I get a ppp0 not ready warning, so now I just have to run kppp, connect, then start Firestarter, and everything works like a charm.  when I run 'ifconfig ppp0', it still says my P-t-P is 10.64.64.64, which I don't quite understand, but it works.

Anyways, hope that helped.  Good luck!

---

### Post by crispie on 2008-10-08
> **gmanigault said:**
> I figure that this is the place to post this.  I have seen limited articles on the web referencing this issue with no ultimate solution. 


I have the following problem.  I have and AT&T aircard usb 881.  It is manufactured by Sierra Wireless.  THe OS is Ubuntu 8.04 Desktop.  Version 2.6.24.19. This version already has the drivers for AT&T installed.  I called AT&T for a simple thing which was the first mistake and all I wanted was the ip addresses of their nameservers for their nameserver.   They didn't help.  

Well after all that and some script mods etc, I am probably about and inch away from getting it to work.  Here is the problem,  I get a remote ip address of 10.64.64.64 which is incorrect.  I tried this with Windows and did and ipconfig /all to get a list of the ip info. 

Windows Info:
==============
IP - 32.176.61.13
Default GW - 32.176.61.13
DHCP Server - 32.176.61.253
DNS Server - 209.183.50.151
             209.183.54.151

Linux Info:
==============

Route:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0

tracepath -n 1.1.1.1

1:  32.176.47.244     0.270ms pmtu 1500
 1:  no reply
 2:  172.26.248.2    233.232ms 
 3:  172.16.1.210    168.936ms 
 4:  12.87.42.165    189.930ms !H
     Resume: pmtu 1500 

GSM connect results:

Starting Sierra Wireless GSM connect script...



Setting the abort string



Initializing modem



Setting APN



Dialing...

Serial connection established.
using channel 5
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xaf889baf> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x10 <asyncmap 0x0> <auth chap MD5> <magic 0x6312c602> <pcomp> <accomp>]
sent [LCP ConfNak id=0x10 <auth pap>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xaf889baf> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x11 <asyncmap 0x0> <auth pap> <magic 0x6312c602> <pcomp> <accomp>]
sent [LCP ConfAck id=0x11 <asyncmap 0x0> <auth pap> <magic 0x6312c602> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xaf889baf]
sent [PAP AuthReq id=0x1 user="gmanigault-D1520laptop" password=<hidden>]
rcvd [LCP DiscReq id=0x12 magic=0x6312c602]
rcvd [LCP EchoRep id=0x0 magic=0x6312c602 af 88 9b af]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [LCP ProtRej id=0x13 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfReq id=0x8]
sent [IPCP ConfNak id=0x8 <addr 0.0.0.0>]
rcvd [IPCP ConfRej id=0x3 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x4 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfReq id=0x9]
sent [IPCP ConfAck id=0x9]
rcvd [IPCP ConfNak id=0x4 <addr 166.128.200.180> <ms-dns1 209.183.50.151> <ms-dns3 209.183.54.151>]
sent [IPCP ConfReq id=0x5 <addr 166.128.200.180> <ms-dns1 209.183.50.151> <ms-dns3 209.183.54.151>]
rcvd [IPCP ConfAck id=0x5 <addr 166.128.200.180> <ms-dns1 209.183.50.151> <ms-dns3 209.183.54.151>]
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 166.128.200.180
remote IP address 10.64.64.64
primary   DNS address 209.183.50.151
secondary DNS address 209.183.54.151
Script /etc/ppp/ip-up started (pid 16125)
Script /etc/ppp/ip-up finished (pid 16125), status = 0x0
Terminating on signal 2
Connect time 15.4 minutes.
Sent 11522 bytes, received 672 bytes.
Script /etc/ppp/ip-down started (pid 17069)
sent [LCP TermReq id=0x2 "User request"]
rcvd [LCP TermAck id=0x2]
Connection terminated.
Script /etc/ppp/ip-down finished (pid 17069), status = 0x0

Serveral thinkgs that I have noticed are as follows.

1.  The ip address given is much different than that windows environment.

     Windows IP = 32.176.61.13
     Linux IP = 166.128.200.180

2.  Linux will not allow you to ping anything such as [www.google.com](www.google.com).  No URLs are accessible.  

3.   Does anyone know how to make the script receive or ignore the remote IP address?


Gary Manigault
[email]gwsharkcom@gmail.com[/email]

Any help would be appreciated.  Once resolved I will publish all the info on how to do it.

Thanks.

Hi Gary, I had the same problem as you, 10.64.64.64 and no way out of it, also close to giving up. However, your Windows IP setup helped a great deal. Look at your windows settings, it seems Windows uses the client IP as the gateway. If you manually set your default gw to your client IP address, everything suddenly works. I can't explain this weird behavior, however, at least it works.

Hope that helps.
Cheers!

---

### Post by yuki_chan on 2008-11-08
Today i installed my Sierra 881U into my intrepid,
I'm using pppd. here are the output :

--
root@ubuntu:/etc/ppp/peers# pppd call gsm
Starting Sierra Wireless GSM connect script...

Setting the abort string

Initializing modem

Setting APN

Dialing...
Serial connection established.
using channel 5
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xd9107ac> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x10 <asyncmap 0x0> <auth chap MD5> <magic 0xfc1527e3> <pcomp> <accomp>]
sent [LCP ConfAck id=0x10 <asyncmap 0x0> <auth chap MD5> <magic 0xfc1527e3> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xd9107ac> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xd9107ac]
rcvd [LCP DiscReq id=0x11 magic=0xfc1527e3]
rcvd [CHAP Challenge id=0x1 <b2c86ccefe87ec479459d4f9ae8345e4>, name = "UMTS_CHAP_SRVR"]
sent [CHAP Response id=0x1 <a89160671e433015c13c90aeafabd983>, name = "blahblah"]
rcvd [LCP EchoRep id=0x0 magic=0xfc1527e3 0d 91 07 ac]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [LCP ProtRej id=0x12 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfNak id=0x1 <ms-dns1 xx.11.12.13> <ms-dns3 xx.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 xx.11.12.13> <ms-dns3 xx.11.12.14>]
rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns3 xx.11.12.14>]
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 xx.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfReq id=0x4]
sent [IPCP ConfNak id=0x4 <addr 0.0.0.0>]
rcvd [IPCP ConfRej id=0x3 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x4 <addr 0.0.0.0> <ms-dns1 xx.11.12.13> <ms-dns3 xx.11.12.14>]
rcvd [IPCP ConfReq id=0x5]
sent [IPCP ConfAck id=0x5]
rcvd [IPCP ConfNak id=0x4 <addr xx.58.95.211> <ms-dns1 xx.155.0.10> <ms-dns3 xx.155.0.15>]
sent [IPCP ConfReq id=0x5 <addr xx.58.95.211> <ms-dns1 xx.155.0.10> <ms-dns3 xx.155.0.15>]
rcvd [IPCP ConfAck id=0x5 <addr xx.58.95.211> <ms-dns1 xx.155.0.10> <ms-dns3 xx.155.0.15>]
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address xx.58.95.211
remote IP address **10.64.64.64**
primary   DNS address xx.155.0.10
secondary DNS address xx.155.0.15
Script /etc/ppp/ip-up started (pid 6575)
Script /etc/ppp/ip-up finished (pid 6575), status = 0x0
--
after its connect. i can't use it to ping google. it always not responding. 

what i forget is copying resolv.conf as instructed here : [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1076]("http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1076") 

it's weird. i still got 10.64.64.64 . but it's working!! (and i'm using it right now)

i'm totally newbie. i don't know what else to help you guys out. so if you want me to run some command in terminal. ask me. :D:D

---

### Post by gmanigault on 2008-11-10
I would assume knowing AT&T and their laziness that somehow they are masking and pings out to other systems.  Probably doing a drop of packets when this occurs.  If would to try setting up DNS on your machine as a slave or primary and see what happens.  As long as it works that is all I wanted.  How is your speed though?  It seems slow but I have no ruler to measure it against. 

Gary

---

### Post by hwzdavu on 2008-11-12
You are a frickin genious. This worked without a problem and thank you very much for taking the time to create the instructions. My RHCE Boss was amazed with me for this, so thanks.


> **gmanigault said:**
> Well I was having problems with the AT&T 881 Usbconnect using Linux Ubuntu 8.04.   I was not able to get it to work using the pppd call gsm statement. AT&T as usual was no help.  Asked them a simple questions like [ie. what is the ip addresses of your nameservers?].  They call that support and never gave me the addresses. 

Well enough about that.  Lets get to how to make the AT&T Sierra Wireless USBconnect 881 work.   It is made to work for windows, load itself and software in the windows environment.   I thought doing that first and doing and ipconfig / all and gathering all the necessary info would help but that didn't work.  


Steps:

1.  Do a [uname -a].  This will give your the version on Linux you are using.  Mine was:

	  2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

2.  Do a [modinfo sierra].  This will tell you the version of the USB driver if it is installed. 

3.  Either use under applications add/remove and install kppp or do and apt-get install kppp. Once these are insalled you will be able to start configuring it. 

4.  Use the following for UID and password.

	UID - [email]ISPDA@CINGULARGPRS.COM[/email]
	PW  - CINGULAR1
5.  Configuration


	Account - Phone number  - *99#
		Authentication -  PAP/CHAP
		IP - Dynamic IP
		Gateway - Default Gateway
		DNS - Automatic
		
	Modems - Device - Set Name
		Modem device  -  Mine is  /dev/ttyUSB0		Note:  Yours may differ
		Flow Control  - Hardware [CRTSCTS]
		Line Termination - CR
		Connection Speed - I set it to the highest.  It should default to its highest. 

That should do it.  You should then be able to get online.  Good luck. I am going to play with the connect speed to see how I might be able to tweak it.  More to come.  

If you have question email me but be patient. 

[email]gwsharkcom@gmail.com[/email]


Gary M.
gwshark

---

### Post by gmanigault on 2008-11-13
**This issue has been resolved.   The only gotcha is if, not if, when AT&T changes the userid and password.  Keep your eyes open. **

I will be posting a HOWTO soon. 

Gary M.
GWShark

---

### Post by walano on 2008-11-19
I have the ATT USBconnect mercury. Can I get some help on this too, thanks. (also a bigtime newbie):lolflag:

---

### Post by gmanigault on 2008-11-22
What do you want to know?  Who is your provider?  Need a lot more information from you. 


Gary 
GWShark

---

### Post by walano on 2008-11-26
thanks for your reply, i'm just wondering if you can help configure my USB wireless. My laptop is the new Dell mini 9 and runs under Ubuntu 8.04. My provider is also AT&T and I believe the AT&T USBConnect Mercury is the newer model next to the 881 usb interface. I ask dell support and att support but they don't have the resources to help me. I'm also a newbie with Ubuntu OS so I'm learning slowly. I'd really appreciate it if you have a resolution for me. Thank you.

---

### Post by Bad Penguin on 2009-03-11
> **nixscripter said:**
> My obivous question is: where did the 10.64.64.74 entry in the routing table come from?

Try these:

Just a FYI for anyone experiencing this problem...  I am using a sierra aircard 875 with AT&T.  Using kppp as outlined on the sierra site worked great on gutsy for over a year.  After recently upgrading to hardy, it stopped working.  Like others posting here I was getting the 10.64.64.64 as the remote gateway and thought that might have something to do with it.

Before you start messing with default routes, disabling interfaces, messing around with ppp options, etc...  try something real simple.

Use kppp to connect, then from a shell prompt with <your favorite terminal emulator> try the following:

```

telnet www.yahoo.com 80

```

If you are able to connect you will see something along these lines:
```

Connected to xxxx.xxx.whatever.yahoo.com.
Escape character is '^]'.

```

Press control-] and type exit.

The problem, at least for me, turned out to not be the connection, it was NetworkManager.  Somehow NetworkManager sets a flag that tells firefox the box is offline, even if it isn't.  If you are using firefox go to File -> and make sure there is not an X by "Work Offline", then try browsing.  To turn it off permanently enter about:config in the location bar, enter "networkmanager" in the filter, change toolkit.networkmanager.disable to true.  I ended up disabling network manager and have had no problems since...

---

### Post by jrolland on 2010-08-10
You may want to check this link out: <[http://forums.linuxmint.com/viewtopic.php?f=90&t=52149&p=301926]("http://forums.linuxmint.com/viewtopic.php?f=90&t=52149&p=301926")>.

The key is that, in your modem dialer's config file, you set the option "CID = 1" (without the quotes). This will (I believe) use your Caller ID information to login to AT&T. The rest is in the post.

Hope this helps.

---

