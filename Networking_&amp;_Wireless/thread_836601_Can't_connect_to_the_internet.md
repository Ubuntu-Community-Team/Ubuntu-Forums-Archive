---
title: "Can't connect to the internet"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by waggers on 2008-06-21
I've been trying for over a week to configure Ubuntu to work with my BT Voyager 105 USB modem and finally gave up and purchased an ethernet modem in the belief that I'd just be able to plug it in and it would, to use Ubuntu's tagline, "just work".  It doesn't.

The ethernet modem in question is a Siemens Speedstream 4100.  Unfortunately my old (Windows) computer doesn't have an ethernet card/port so I can't try the new modem on the old computer.

I feel like I've tried just about everything and am seriously on the verge of giving up on Linux if I can't get this working soon.  Being new to all this, I've no idea where to start trying to diagnose the problem - having read responses to similar forum posts, I'm more confused than ever!

I've entered all the relevant information in the Network Settings dialogue box but can't connect. When I run sudo pppoeconf I get this message:

"Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond.  Please check your network and modem cables.  Another reason for the scan failure may also be another running pppoe process which controls the modem."

When I run /sbin/ifconfig I get:

eth0      Link encap:Ethernet  HWaddr 00:0b:db:b1:9f:bd  
          inet addr:192.168.254.1  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:feb1:9fbd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73256 (71.5 KB)  TX bytes:33598 (32.8 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84300 (82.3 KB)  TX bytes:84300 (82.3 KB)

I'm running Ubuntu 8.04.  Please help!

---

### Post by Wobblybob on 2008-06-21
Have you seen these instructions for your old modem?
[http://ubuntuforums.org/showthread.php?t=140010&highlight=BT+Voyager+105+USB]("http://ubuntuforums.org/showthread.php?t=140010&highlight=BT+Voyager+105+USB")

---

### Post by waggers on 2008-06-22
> **Wobblybob said:**
> Have you seen these instructions for your old modem?
[http://ubuntuforums.org/showthread.php?t=140010&highlight=BT+Voyager+105+USB]("http://ubuntuforums.org/showthread.php?t=140010&highlight=BT+Voyager+105+USB")

Yep.  Using version 11 of eciadsl I couldn't get the configuration tool to work (either in the "ugly" eciadsl-config-tk stand alone window or the terminal-based version, eciadsl-config-text).  So I installed version 12 and got a bit further, managing to enter my details using eciadsl-config-text.  However, when I ran eciadsl-start, it failed at the synchronization stage.  I've since uninstalled eciadsl (on the assumption that I don't need it any more since I've purchased an ethernet modem) so I'm afraid I can't replicate the exact error message right now.

Having said that, I'm more than happy to try again if you think I'm more likely to be successful with the USB modem than the ethernet one...

---

### Post by CEB2nd on 2008-06-22
This is just a WAG, but did you run the setup for the
Speedstream when you first connected it?  Open your
web browser and enter the address [http://speedstream](http://speedstream)

If I remember correctly, the default password is admin
and you just leave user-name blank...should be in your
instruction manual. Is the modem running in bridge or
router mode?

---

### Post by waggers on 2008-06-22
Thanks CEB2nd, but when I open Firefox and type [http://speedstream](http://speedstream) into the address bar, it doesn't find anything.  It eventually changes the address to [http://www.speedstream.com](http://www.speedstream.com) and displays the standard "address not found" error.

I've just tried pinging "speedstream" from Network Tools and receive the same message: the address "speedstream" cannot be found.

---

### Post by CEB2nd on 2008-06-22
I just wanted to make sure that you know [http://speedstream](http://speedstream) allows
you to access the settings inside the 4100 using your web browser, it
isn't an actual web site.  If the above address doesn't work try
one of these:

[http://192.168.1.1](http://192.168.1.1)
[http://192.168.0.1](http://192.168.0.1)
[http://192.168.2.1](http://192.168.2.1)
[http://192.168.254.254](http://192.168.254.254)

Did you buy this modem new retail or was it originally supplied
by an ISP?  If all else fails, try holding the reset button in
for about five seconds and release.  The power light should turn red. Give
the modem a couple of minutes to reboot then try accessing it
again.  Good luck.

On edit:  You can download a PDF of the 4100 user manual here:
[Speedstream 4100 PDF]("http://www.finestplanet.com/downloads/SS4100manual.pdf")

---

### Post by waggers on 2008-06-23
FANTASTIC!  Thank you so much - I'm writing this from Ubuntu!  Yep, I knew [http://speedstream](http://speedstream) wasn't a real website but an admin console for the modem.  Having gone through the addresses you suggested, finally the last one worked and it was plain sailing from there,  Thanks also for the user manual link, I was looking for that!

Incidentally, to answer your other question, I got the modem off of ebay (which I know could be slightly risky.

Thanks again for bearing with me and sorry for any impatience that's come across, I was reaching the end of my tether but am full of enthusiasm again now!

(Until, that is, I try to connect our printer, scanner and CD/DVD writer, all of which connect via USB - but that's another story)

---

### Post by CEB2nd on 2008-06-23
Glad I could help! :D

---

