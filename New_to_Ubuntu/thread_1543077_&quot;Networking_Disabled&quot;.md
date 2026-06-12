---
title: "&quot;Networking Disabled&quot;"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by TortureQueen on 2010-07-31
Hi, guys.  Yesterday--and part of today--my computer could not connect to the internet via wireless connection *or* wired connection.  The box was checked for "connect to the internet using wireless and ethernet," and my computer's wireless signal was turned on.  Despite all of this, I could not connect to the internet, and every time I clicked on the network connection monitor on my panel (or task bar. .), it would say, "networking disabled."  I tried re-clicking the ethernet and wireless connection box, I tried restarting the computer, and I also tried unplugging my ethernet cable and shutting off the box, then plugging it back in.  This did not work.  I was so distraught--I need to pay bills today, and had no other reliable computer to use--so I just reformatted.  I know it isn't good for my hard disk, but I didn't know what else to do.  When the connection problem began: I connected to my library's public WiFi connection.  I finished what I had to do, and then I selected disconnect from my panel's networking monitor.  Then closed my laptop, and went about my business.  About an hour later, I booted up my computer and attempted to connect to the public WiFi connection.  It would not connect, and I saw the "networking disabled" message.  Today, I tried to connect to the internet via ethernet, and I still could not connect--I still received the "networking disabled" message.  Can someone tell me what caused this, or why my computer is doing this?  I am very worried about this.  I am afraid it will happen again, and I do not know how to fix this problem.  I'm starting to have a love-hate relationship with Ubuntu. . -.-;

---

### Post by Rubi1200 on 2010-07-31
Hi,
could you post the results of 
 
```
ifconfig 
```
and
```
 
/etc/network/interfaces

```please.

---

### Post by TortureQueen on 2010-07-31
Do I type these in the command line, or somewhere else?

---

### Post by jerenept on 2010-07-31
right click on the NetworkManager applet and select "Enable Networking"

---

### Post by Rubi1200 on 2010-07-31
> **TortureQueen said:**
> Do I type these in the command line, or somewhere else?
Sorry, go to Applications > Accessories > Terminal and run the commands from there (separately).

---

### Post by TortureQueen on 2010-08-03
Hi Rubi,  the first command resulted in this:  eth0      Link encap:Ethernet  HWaddr 00:26:22:36:95:77             UP BROADCAST MULTICAST  MTU:1500  Metric:1            RX packets:0 errors:0 dropped:0 overruns:0 frame:0            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0            collisions:0 txqueuelen:1000            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)            Interrupt:29 Base address:0xe000   lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0            inet6 addr: ::1/128 Scope:Host            UP LOOPBACK RUNNING  MTU:16436  Metric:1            RX packets:16 errors:0 dropped:0 overruns:0 frame:0            TX packets:16 errors:0 dropped:0 overruns:0 carrier:0            collisions:0 txqueuelen:0            RX bytes:1096 (1.0 KB)  TX bytes:1096 (1.0 KB)   wlan0     Link encap:Ethernet  HWaddr 00:23:08:be:ca:af             UP BROADCAST MULTICAST  MTU:1500  Metric:1            RX packets:0 errors:0 dropped:0 overruns:0 frame:0            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0            collisions:0 txqueuelen:1000            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)   I couldn't do the second command.

---

