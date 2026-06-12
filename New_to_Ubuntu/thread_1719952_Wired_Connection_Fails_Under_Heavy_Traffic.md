---
title: "Wired Connection Fails Under Heavy Traffic"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by ChrisThompson on 2011-04-02
Hey all,

My wired ethernet connection will fail periodically, and it appears to  be tied to my traffic volume.  I seldom have this problem when I am  simply browsing, but if I am downloading files from a site or running  Transmission my internet connection will invariably stop working after a period  of time (All websites time out, etc).   Usually I can fix this by rebooting, but sometimes even that  does not correct the issue.  I know this is somehow tied to my machine,  since the other users on my home network do not experience this problem,  and I know this is an Ubuntu problem since I usually end up booting  into XP to sidestep it.

I'm running Ubuntu 10.04 with an ASUS A8V-XE motherboard.  According to  Device Manager, the ethernet controller is a VT6102 [Rhine-II].  I am plugged into a D-Link DIR-615 Wireless N 300 router.  I usually hit the problem while running Transmission 1.93 (10621), but I've also encountered it with Firefox 3.6.16 and Chromium 10.0.648.133 (77742).  Though when one goes down, they all go down.

Thank you to everyone in advance for your insight in solving this issue.

--Chris

---

### Post by yeats on 2011-04-02
You might take a look at /var/log/messages for the times around when the issue occurs.  A good start might be:

> sudo grep eth /var/log/messages

---

### Post by Hedgehog1 on 2011-04-02
Greetings Chris!

I found that transmission was overwhelming my network, too.

The easiest thing to try is to use Deluge bit torrent instead. You will find it in the Ubuntu Software Center. While doing this will not stop all the issues, many folks have found it overwhelms their network connection less.

Your router is one of those whose firmware can be updated to an open source choice that can help. It replaces the little Linux install that runs your router with a different one called DD-WRT:

[http://forums.dlink.com/index.php?topic=13599.0]("http://forums.dlink.com/index.php?topic=13599.0")

I upgraded by own router with 'tomato'.  I am not sure if your router can be upgraded with either or just DD-WRT, the google search gave me conflicting responses.

***The Hedge***

:KS

---

### Post by ChrisThompson on 2011-04-03
Howdy Hedge,

Well sadly, Deluge did not solve the problem.  It crashed all the same.

Also, I was not able to change the firmware on my router.  Whenever I tried to upload it through D-Link's firmware Web interface (option 1 on the "Guide to DD-WRT" page) it told me the connection to the server was reset.  This happened with Firefox, Chromium, and even when I booted into Windows and tried loading from IE as one site suggested.  And I simply could not get my router to load into Emergency Room mode (option 2).  I followed all the steps to the letter, although it took me a while to figure out how to change my network adapter IP, but every time I tried to load [http://192.168.0.1](http://192.168.0.1) according to the last step on that page my browser would say that it cannot connect to that page.  I've searched for other ways to load the Emergency Room screen and some places offered some different combinations of tricks (holding the button down longer, plugging the cable into a different port) but nothing worked.

Unfortunately, I was able to reproduce the issue on my laptop, which runs 10.10, so I think you are right about it being the router.  Unfortunately, since I can't seem to change the firmware, I'm not sure what to about it.

Yeats, when my laptop crashed I did pull of that log you asked for:
```

Apr  3 16:02:08 Laptop kernel: [80730.004177] e100 0000:02:08.0: eth2: NIC Link is Up 100 Mbps Full Duplex
Apr  3 16:32:30 Laptop kernel: [82552.004376] e100 0000:02:08.0: eth2: NIC Link is Down

```

Again, thank you to you all for any assistance you can offer.

--Chris

---

### Post by ChrisThompson on 2011-05-06
...Bump?

The problem seems to be getting worse.  It's kicking me after a day of use, even if I avoid Deluge or Transmission entirely.  We have identified that the problem is my router, but since I can't seem to reset the firmware on it I'm just about to buy a whole new router out of frustration.  Is there anyone in the Ubunt-o-sphere who can spare me this expense?

Thanks,

--Chris

---

