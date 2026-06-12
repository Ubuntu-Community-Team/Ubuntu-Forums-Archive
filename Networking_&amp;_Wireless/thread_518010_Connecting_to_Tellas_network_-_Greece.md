---
title: "Connecting to Tellas network - Greece"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by paulgray on 2007-08-05
Hi!
I'm on my one month long holidays in Greece: there is a Tellas net provider in the flat I live.

So, at first I've installed firmware for a F200 Crypto ADSL USB modem: all works perfectly (I think so: `dmesg` returns no errors, etc. )
I've tried to connect to the network configuring my connection via pppconfig and manually

In first case, when I use the guide found at [http://ubuntuforums.org/archive/index.php/t-128573.html](http://ubuntuforums.org/archive/index.php/t-128573.html) and after typing `pon`, nothing happens: no connection and `tail /var/log/messages` show me:
> 15:40:09 blah-blah pppd 2.4.4 started by root, uid 0
15:40:10 blah-blah Exit.
hmmm

In second case, when I connect as it is described at [http://antonis.wordpress.com/2007/04/29/crypto-f200-adls-usb-modem-%CF%83%CE%B5-ubuntu-feisty/](http://antonis.wordpress.com/2007/04/29/crypto-f200-adls-usb-modem-%CF%83%CE%B5-ubuntu-feisty/) (I don't know Greek, I've only copied the content of /etc/ppp/peers/tellas and change the passwords etc.)
And after typing `pon tellas` I receive a message: 
> plugin pppoarm.so loaded.
tcgetattr: Inappriopriate ioctl for device (line 917)
It is a USB modem, so I replaced the line `8.35` by a `/dev/bus/usb/004/00x` where x is a number of device (I read it from Device Manager)

I will spend here almost a month - please, let somebody guide me, step-by-step, what should I do to make it works :)

thanks in advance

---

