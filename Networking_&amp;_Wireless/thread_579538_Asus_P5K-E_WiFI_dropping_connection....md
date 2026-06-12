---
title: "Asus P5K-E WiFI dropping connection..."
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by RetepNamenots on 2007-10-18
Just having a bit of a problem with wireless in 7.10 (Just finished installing it). Actually, quite a large one and I'm not sure that anyone's going to be able to help... anyway)

I'm using the built-in wireless AP with the Asus P5K-E WiFi motherboard. It works fine in Windows.

Ubuntu appears to pick it up automatically, and informs me that there are a couple of networks available to join. So, I click on the one that I want. It will take about a minute to connect, then runs extremely slowly - I mean about 3kbps. After a couple of minutes, the connection will just be 'dropped'. I then need to restart the whole PC again to get it 'working', when it will drop again after a couple of minutes...

Any ideas? I need the connection to set up restricted drivers and so on.. :(

Cheers1

---

### Post by syxbit on 2007-12-01
just bought the same Mobo, and was thrilled that it just worked out of the box.
however, is flakes out and requires a reboot.
this is unacceptable.
i may end up putting in a PCI linksys card.
let me know if you figure anything out.
i've found ndis wrappers to be terrible, so i'm not going to try that

---

### Post by thevjm on 2008-04-24
Same problem here.

Anybody tried it out in Hardy?

---

### Post by murkin on 2008-05-02
I've been using Hardy with this set up for about a week now. Everything works great except for wifi. I'm not 100% sure about it yet. When downloading a torrent, the network connection drops with regularity. When not, it seems to be ok. Very strange. There's some kind of cron job that runs once an hour. Maybe that is the culprit. Also, something ipv6 related seems to be happening too. 

Anyway, I'm following the bug closely. No answers thus far. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/182473)

Honestly, I've been very busy with finals, but just finished today so, I hope to report back soon.

---

### Post by barakaspeed on 2008-07-07
I just purchased this same mobo and am experiencing the same issues with Hardy.  I also installed Fedora 9 to troubleshoot and experienced the same issue there.  Not sure if that helps any.  Hope to see a resolution soon!

Edit:  I originally thought the only way to get it working again was to reboot the machine as other's have suggested.  I tried reseting my wireless router tonight and that allowed it to reconnect without rebooting ubuntu...

---

