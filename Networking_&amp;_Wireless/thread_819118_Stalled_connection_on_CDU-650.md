---
title: "Stalled connection on CDU-650"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by 2TallSwede on 2008-06-05
I have a Franklin CDU-650 that I have been playing around with. I got it set up and working using info in this link (among others):

[http://ubuntuforums.org/archive/index.php/t-537979.html]("http://ubuntuforums.org/archive/index.php/t-537979.html")

I've set up Gnome-PPP as my connection interface, entered all the usernames and such and everything connects just fine. However, for some reason, most of the time, the connection just stalls. It sits there and transmits/receives a kb here and there but nothing worth a thing when you're trying to surf somewhere or download emails. But, it's still connected.

I've tried to go through wvdial for a change and the results are the same. It connects without problems, I see the IPs, the DNS servers etc. but for both methods, about one out of ten attempts will actually produce a connection that actually works continually for more than just a second or two after connecting.

I do have my computer connected to a router normally (which I disconnect when I try this) so maybe there's something there that I'm missing. I know that the unit itself works fine when I boot into XP so I don't think it's the device itself.

When it is working I get satisfactory speeds (800kbps-1Mbps) but it's irritating to not be able to get a working connection every time.

Any suggestions? I'm running 8.04 by the way.

---

### Post by Jaciss on 2008-06-10
I got this modem (CDU-650) yesterday and was having the same issue, so if you find a solution an update would be much appreciated.  If I do, I'll post it here.

Stalling aside, I found I didn't need to do anything particularly special for the card to work (after reading all about what I'd need to do).  After testing it in Win with the 'official' software I booted Gutsy with the card in.  It showed up under /dev/ttyACM0  which was detected by wvdialconf (and hence gnome-ppp).  Setting the username and password with phone = #777 in /etc/wvdial.conf or via gnome-ppp got it connecting.

A good summary of the logic involved can be found in this post by yellowbread (note that the topic discusses a different model - I doubt the 650 has a 'data mode'):

[http://ubuntuforums.org/showpost.php?p=4313032&postcount=66](http://ubuntuforums.org/showpost.php?p=4313032&postcount=66)

Unplugging the card whilst it's in use causes issues, but otherwise it seems to recognize the card and create /dev/ttyAMC0 whenever I plug it in.  All in all, I think it's a good wireless USB modem for Linux - I don't think the stalling is anything major, it just needs some figuring out.

---

