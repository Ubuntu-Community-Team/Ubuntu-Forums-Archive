---
title: "Activating Wireless Network Connection - sits at 28%"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by straightv6 on 2007-05-21
I'm trying to get my WUSB54GC wireless stick to connect to my router.
The network manager shows a signal but I don't receive an IP address and the popup says Activation stage: configuring device.

 I'm not running any security except for a MAC address filter which I have tried turning off already.

---

### Post by BenWhitey on 2007-05-24
I'm having a very similar problem.

---

### Post by thunderkyss on 2007-05-24
My problem was similar, it was the MAC Filter. 

What are your rules, and how are you turning it off??

And what kind of messages are you getting in your Router's logs?? Anything concerning the MAC address of the computer you're trying to connect??

---

### Post by BenWhitey on 2007-05-24
First I received this problem: [http://ubuntuforums.org/showthread.php?t=450987](http://ubuntuforums.org/showthread.php?t=450987)

Then I decided to reinstall kubuntu in case I messed something up trying to get my wifi working.  Then while using the livecd I tried to connect to my wireless and it sopped at 28%.

My router's MAC address filter is off.

---

### Post by thunderkyss on 2007-05-24
> **BenWhitey said:**
> First I received this problem: [http://ubuntuforums.org/showthread.php?t=450987](http://ubuntuforums.org/showthread.php?t=450987)

Then I decided to reinstall kubuntu in case I messed something up trying to get my wifi working.  Then while using the livecd I tried to connect to my wireless and it sopped at 28%.

My router's MAC address filter is off.

I'm guessing I don't fully understand what you mean by "it stopped at 28%"

If you are showing 28% signal strenght, then that sounds good enough to connect. 

If you are saying the progress bar stopped at 28%, then most likely, that means it is waiting for your router to give it an IP address.... or allow it on your network. which means your problem is in your router.

---

### Post by BenWhitey on 2007-05-24
The latter (at least for me).  I go to connect to the network and then the connection stops when it is 28% of the way though the process of connecting.  It never connects.  It is not my router's problem.  In windows I can connect fine to it.

---

### Post by BenWhitey on 2007-05-26
Ok.  Its a bug with the madwifi driver.  [http://madwifi.org/ticket/1343](http://madwifi.org/ticket/1343)

Lets hope it gets fixed soon.  Try bringing your computer closer to the your router.

---

