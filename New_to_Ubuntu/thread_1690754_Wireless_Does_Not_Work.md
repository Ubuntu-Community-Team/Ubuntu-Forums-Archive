---
title: "Wireless Does Not Work"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by 8sh8 on 2011-02-18
I have a Toshiba Satellite L655 S5115 with a Realtek RTL8188CE Wireless LAN 802.11n PCI-E NIC wireless card. At the moment, I boot Ubuntu off of a USB drive. When I boot Ubuntu there is no wireless what-so-ever. I saw a thread with a suggestion input into terminal, but I was unable to get that to work(possibly because I am doing something wrong).

Also, I am not so tech savvy so please use simple terms. Thanks.

---

### Post by whatthefunk on 2011-02-18
Go to a terminal and type:

```
ifconfig
```

Post the output.

Do the same for 

```
iwconfig
```

---

### Post by Cracklepop on 2011-02-18
Hi 8sh8, 

You'll find lots of people willing to help solve problems, but you need to give a lot more information if you want that to happen.  

Is there a network symbol in the panel?
Has Ubuntu recognized your wireless card (if you right click the icon can you see "Enable Wireless")?
What was the terminal command?
What did you do with it and what happened (what was the output, if any)?

---

### Post by Dutch70 on 2011-02-18
Also, you may want to check [***[COLOR="Blue"]Here[/COLOR]***]("http://ubuntuforums.org/showthread.php?t=1604101") or [***[COLOR="Blue"]Here[/COLOR]***]("http://www1.ubuntuforums.org/showthread.php?p=10271860")

---

### Post by 8sh8 on 2011-02-18
ifconfig output:
 
eth0
Link encap:Ethernet HWaddr 60:eb:69:52:2e:1c
UP BROADCAST MULTICAST MYU:1500 METRIC:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:45
 
lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1776 (1.7 KB) TX bytes:1776 (1.7 KB)
 
 
iwconfig output:
 
lo
no wireless extensions.
 
eth0
no wireless extensions.

---

### Post by rvchari on 2011-02-18
in the panel notifier applet, you must be noticing an icon for network connections. if not then right click on the panel, add to panel notifier applet.
then you select the applet from panel and you should get the connection manager. try to manually configure your settings. perhaps you should get your wireless to work.

---

### Post by whatthefunk on 2011-02-18
Lets make sure your system is picking up the hardware.  Go to a terminal and type 

```
lspci
```

What does it output?  You should see your device listed in there somewhere.

Im guessing its a driver problem.  Try here:

[http://ubuntuforums.org/showthread.php?t=1604101](http://ubuntuforums.org/showthread.php?t=1604101)

There are several suggestions on how to get the correct drivers installed and running.

---

### Post by 8sh8 on 2011-02-18
lspci output:
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)

---

### Post by whatthefunk on 2011-02-18
So its there.  Its a driver then.  Check out the thread I mentioned in post #7...lots of ways to get it working.

---

### Post by 8sh8 on 2011-02-18
Thanks everyone!

---

### Post by whatthefunk on 2011-02-18
Did you get it?

---

