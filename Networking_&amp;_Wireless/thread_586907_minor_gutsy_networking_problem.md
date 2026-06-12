---
title: "minor gutsy networking problem"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by bearcat on 2007-10-22
Unlike some people, I'm not finding myself unable to get onto the Internet in Gutsy -- but I have to manually disable and then re-enable networking each and every time I boot. It won't connect at all until after I do that, although after I re-enable networking it connects without a problem. 

Is there a way to fix this?

---

### Post by jamesey on 2007-10-22
I get this too. Every time I boot, I have to go into networking, select my saved setting for my home network, and then I connect to the internet. Not major, but annoying. In Feisty, everything was automatic. In Gutsy, it's not.

---

### Post by jamesey on 2007-10-22
Man this is annoying. Every restart means I have to go here and set my connection settings. How do I make these "stick"

[IMG]http://i63.photobucket.com/albums/h138/jameseyjamesey/Screenshot-NetworkSettings.png[/IMG]

---

### Post by Megatog615 on 2007-10-23
Same issue on two laptops, with Kubuntu and Xubuntu. I didn't have the issue when I first installed Gutsy; rebooted a few times with no issues, until a few days after when I updated to the latest packages.Maybe they broke something in the updates?

Seems to be isolated to wireless cards.

---

### Post by darjeeling on 2007-10-23
Not just wireless cards. I'm having the issue of having two perfectly-supported gig NICs and only one will network at a time. One is DHCP and one is static to my internal network. Worked fine with Feisty with zero changes. Already disabled NetworkManager and have been doing just the /etc/network/interfaces - ifup/ifdown eth1/eth2 route....

Commenting out one card in the interfaces file and bringing up just one will be fine, but as soon as I bring up the second, all traffic outside the network stops. I'm guessing it's a routing issue, but haven't spent a lot of time researching...

---

### Post by jamesey on 2007-10-23
Besides the automatic connection not happening, My connection will drop after 10 minutes, then when I manually reconnect, it will be fine for the rest of the day.

---

### Post by mikecj on 2007-10-23
I have the exact same problem, accept the profile reverts back to its "default" DNS of 10.0.0.1 when the system is idle for 10 minutes - whether the screensaver/power saving features kick in or not.

This is HIGHLY frustrating - especially for someone like me who is curious about computer technology but has absolutely no ability (aka 'noob').

Because of this lack of ability, I am at a loss as to how to rectify this annoying problem. Any user friendly responses would be appreciated.

Thanks!

---

### Post by darjeeling on 2007-10-23
> **darjeeling said:**
> Not just wireless cards. I'm having the issue of having two perfectly-supported gig NICs and only one will network at a time. One is DHCP and one is static to my internal network. Worked fine with Feisty with zero changes. Already disabled NetworkManager and have been doing just the /etc/network/interfaces - ifup/ifdown eth1/eth2 route....

Commenting out one card in the interfaces file and bringing up just one will be fine, but as soon as I bring up the second, all traffic outside the network stops. I'm guessing it's a routing issue, but haven't spent a lot of time researching...

Solved my issue. For some reason, I had an error in my interfaces file of putting a gateway on my internal interface, and it was not needed since they were the same subnet. I took it out, and now both cards route perfectly. Odd that this was the exact same config file from Feisty and it worked.

---

### Post by aaargh486 on 2007-10-25
I confirm this issue. It's annoying, I had this in Windoze and I thought I finally got away from it?

---

### Post by Therion on 2007-10-26
Same/similar problem using my LinkSys WRT54G router.  Every restart of the PC means rebooting the router (unplug it, plug it back in ten-seconds later) to get an internet connection.  Annoying!!

---

