---
title: "Flaky Wifi Connectiion - Atheros QCA9565 / AR9565 - Ubuntu 17.10"
date: 2017-10-30
forum: Networking &amp; Wireless
---

### Post by paddyt on 2017-10-30
Hi there,
I'm having trouble configuring my Wifi connection after a fresh 17.10 install.
I am able to connect to my desired network, but the connection regularly drops, or else slows to almost zero. 
 
I am dual booting the machine, and the network works just fine when running windows, which suggests the problem is not simply a weak signal.
After reading around, and trying several solutions proposed elsewhere, I've still had no luck. Any help would be greatly appreciated!

I've followed the instructions in the sticky and ensured my system is up to date and run the wireless info script. The results can be found here: [http://paste.ubuntu.com/25850951/](http://paste.ubuntu.com/25850951/)

Many thanks!

---

### Post by ajgreeny on 2017-10-30
See **Wireless-info** in my signature, download it and run the script, then report back the output here or using [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) if the output is too large to add direct.

---

### Post by paddyt on 2017-10-30
I thought I had provided my wireless-info script results in the original post above! Did I get something wrong?

---

### Post by ajgreeny on 2017-10-30
Apologies; I did not notice that you had already done that.

Mea culpa!

---

### Post by paddyt on 2017-10-31
No worries! Notice anything unusual in my **wireless-info** results?

---

### Post by jeremy31 on 2017-10-31
I would see [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
The first command might help and it might help to removes the spaces in the network name on the router

---

### Post by paddyt on 2017-10-31
Thanks Jeremy31, I've removed any spaces from the network's ssid.
I tried the first command suggested (changing the power settings) in the thread, without noticing any change.
I also tried the other suggestions there, changing the country specific device setting, also without any luck...

Here's an updated script result:
http://paste.ubuntu.com/25858397/

Any other suggestions?
Thanks for all your help.

---

### Post by paddyt on 2017-11-01
Bump!

---

### Post by paddyt on 2017-11-01
I also tried the "nohwcrypt=1" fix listed here, without any luck.
[https://kalpeshpadia.wordpress.com/2013/04/23/fixed-atheros-wireless-slowdisconnecting-intermittently/](https://kalpeshpadia.wordpress.com/2013/04/23/fixed-atheros-wireless-slowdisconnecting-intermittently/)

Starting to lose hope :(

---

### Post by paddyt on 2017-11-02
I also tried changing to Google DNS (8.8.8.8, 8.8.4.4) and disabled ipv6 without any effect.

I observe a strange behaviour where I can achieve an initial "spike" of slow access immediately after connecting to the network ( at ~1Mbps...), enough to maybe load a single webpage if I'm quick, after which the connection speed drops to zero ( while remaining connected to the network according to Network Manager)

Does this behaviour suggest what the problem might be?

---

### Post by jeremy31 on 2017-11-02
I would see if there are any updates available for the router and do a restart on it either way.  I have a different Atheros chipset that uses the same drivers and the reception is a bit weak but I haven't seen your problem occur on my laptop

---

### Post by paddyt on 2017-11-03
Thanks Jeremy31,

I've restarted my router as you suggested, without any effect. It seems it already has the latest firmware, comparing my router settings with the manufacturer website. My ISP (Virgin Media, UK) makes the router and pushes these updates automatically!

Maybe I should think about downgrading to 16.04? I can't think what else to try.

---

### Post by paddyt on 2017-11-07
So I reinstalled my Ubuntu 17.10 instance from scratch (wiped the partition, reinstalled from a live CD) and I still have the same problem - I can connect to my network, with limited speed at first, after which the connection drops to zero (while network manager remains connected to the network with reasonable signal strength). Refreshing the connection typically restarts this cycle, giving another brief spurt of access, followed by zero speed connection.
This behavior makes me convinced the issue must be software-based, and on my machine (restarted the router, other devices work fine). It feels like some program or setting is conflicting/interrupting with the connection.
Stranger still, the drop in connection seems to occur more quickly if I attempt larger downloads, suggesting it is dependent on the amount of traffic between my router and machine. 

Here is a recent pastebin: [http://paste.ubuntu.com/25911153/](http://paste.ubuntu.com/25911153/)

---

### Post by jeremy31 on 2017-11-07
Try a live version of the original 16.04

---

