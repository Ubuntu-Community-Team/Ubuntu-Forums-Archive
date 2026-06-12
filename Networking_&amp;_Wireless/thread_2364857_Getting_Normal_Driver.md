---
title: "Getting Normal Driver"
date: 2017-06-28
forum: Networking &amp; Wireless
---

### Post by Darth4212 on 2017-06-28
Recently I did a fresh install of Ubuntu Studio alongside Windows 10. Now beforehand my network card was working fine. But after the install it went dumb. 
So I decided to run ```
lshw -c network
``` to see if there was any sort of problem.
The output was this: [IMG]https://sqphdg.bn1301.livefilestore.com/y4mn91EyYy08qPo1QzznlKzO1enVskMXRNB-CTwSpopqJ0Oj-0JNBV6ZC7jsCMF2yhwUXA4YDIIvsD7lDWd-GD6Hb4DSxtmBk7xdtg54eqQ4LeiyEJV_ctQ2me7Fc7br0nIw5ALhkVRcVlU5j56E3iGTgoCcOAZEnL-AkKktOn_JVMLbVywiHffQSdbJCxfOb0ERgxjZXV7fSXKc99Kx7jwfQ?width=1022&height=237&cropmode=none[/IMG]
So what I need to know is if the fact that this is the low latency driver may be affecting things. If so where could I get the normal version of the driver at?
Also before installing the logical name of the wireless interface was ```
wlan0
``` and is now ```
wlp8s0b1
``` what would have caused this?
But no matter what I would like to know where I could download the normal driver.
For reference my wireless card is a Broadcom 802.11n Wireless Card
**[SIZE=4]NOTE: [/SIZE]**[SIZE=4][SIZE=2]The internet works on it. It is just that before I connect to my network it shows that I have 3 bars of signal but after connecting it drops to 1 or sometimes if I am lucky 2. Also the issues are under Windows 10 as well.[/SIZE][/SIZE]

---

### Post by Bucky Ball on 2017-06-28
So, internet is working, the problem you're having is found in Windows also, and that problem is that the name of wlan0 has changed, and that is not a problem, but is normal. The new protocol for describing wireless connections, a seemingly random string, is as you've got there. To be expected. Someone else will be able to explain for what reasons/why this has changed in recent releases.

My wireless connection, which is working faultlessly, is logical name: wlp3s0. The driver is part of the kernel, in this case the UStudio lowlatency kernel, and what you have in your output there is also perfectly normal. 

As your issue, which seems to be the bars going down when you connect, is not specific to Ubuntu, not sure what help can be given. Perhaps the issue is generated somewhere outside your computer as what you have installed in Ubuntu, re. drivers etc, have nothing whatsoever to do with Windows. You are running one OS or the other, not both at once. Never the twain shall meet.

---

### Post by QIII on 2017-06-28
*Moved to **Networking & Wireless***

---

### Post by Autodave on 2017-06-29
Since problem is in both operating systems, the problem IS NOT the operating system. Router too far away? Too much local interference? Are you sure that you are connecting to your router and not a neighbor's? Does router have an antenna on it? You may be able to wrap a piece of wire a couple of times around the antenna and then stretch out a foot or so of it to give a better range.

If none of that helps, get another computer (borrow one or ask a friend to come over) and try their's from the same location that you have your's. If signal still weak, get better router. If signal is good on other machine, you might try a plug-in wifi card or a USB wifi stick.

---

### Post by chili555 on 2017-06-29
> But no matter what I would like to know where I could download the normal driver.Please check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

Broadcom devices are quite unique in that there are two and, rarely, three drivers that will claim the hardware and attempt to drive it. Unfortunately, only one driver actually works well and, in most cases, works at all. Therefore, it is not as simple as uninstalling one driver and installing the other. Please follow the steps in the link and check to see what the suggested driver is for your exact device. 

If you get stuck or need more assistance, post back and we'll be happy to help.

---

### Post by Darth4212 on 2017-07-02
Thanks for the help everyone. But oddly for some reason Ubuntu made me use proprietary drivers so all's well that ends well!

---

