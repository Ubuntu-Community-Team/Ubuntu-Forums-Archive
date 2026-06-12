---
title: "USB WiFi Finally Working. But the solution makes no sense."
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by ubuRudy on 2007-07-29
Hi. I'm posting this hoping that someone can help explain why the following worked...

I installed U7.04 on a Dell CPxH500GT laptop. My wifi adapter is a Linksys WUSB54Gv4 (the little box with USB interface and external antenna). Well, I spent a couple of weeks trying to get online. I prowled through this entire forum and tried and tried every conceivable solution I came across. Absolutely nothing worked. The closest I got was through ubuntu's Network Manager (out of the box install). It would roam great and show several access points but could never connect.

Last weekend, I was in Office Max and came across a PCMCIA wifi adapter. Being older technology, I figured I'd give it a shot. Maybe it would play nice with ubuntu. (it's a D-Link WNA-1330 - aetheros chipset). Sure enough. I brought it home, pushed it into its awaiting slot, and BAM! I'm suddenly (and FINALLY) online. I could finally give my Mac a rest.

So now that I had internet access on the laptop, I again went about trying to get the Linksys to work but haven't had any success. The D-Link and the Linksys both showed available access points but only the D-Link was able to connect to them (albeit with very poor reception).

Today, reception was extremely poor and so I took the D-Link out of roaming mode and configured it to talk directly to the access point. Not really sure if this matters but I just did it on a hunch. Well, when I did this, the network manager (in the menu bar) now only showed the access points as seen by the Linksys (makes sense as it was still roaming-enabled). But here's the crazy part. I am now able to access my access point (and others) with the Linksys. And because it has an external antenna, I'm getting 10x better signal. Just to make sure, I did an iwconfig and sure enough, it's the Linksys talking to the access point.

Now, can somebody please explain why this is working the way it is?

Oh, and to test, I shut down, removed the pcmcia D-Link, restarted, and the Linksys didn't work at all (though it saw all of the surrounding access points). I shut down, reinserted the pcmcia D-Link, rebooted, checked the network settings to make sure that D-Link had an SSID associated with it and that the Linksys was roaming enabled, and got back online using the Linksys. Does this make sense?

Thanks.
Rudy

BTW, great forums!

---

### Post by MillDoGG on 2007-07-29
perhaps your linksys is acting as a repeater.

---

### Post by 1feistymedic on 2007-07-29
[http://ubuntuforums.org/showthread.php?t=512647](http://ubuntuforums.org/showthread.php?t=512647)


Good Job Rudy.....

I don't know how to assist you..I am being assisted in the above post....If you can help me out along with the other nice person, I would really appreciate it!

Thanks

---

### Post by ubuRudy on 2007-07-31
Sorry. I wish I could. Good luck to you. I know how frustrating this must be for you. I lost my hair trying to find the solution.

---

### Post by kevdog on 2007-07-31
Why dont you compare the modules loaded and see if there are any difference in the two scenarios.

Scenario #1
lsmod > one

Scenario #2
lsmod > two

diff -y one two

---

### Post by ubuRudy on 2007-08-09
no difference.

---

