---
title: "very slow network transfer speeds"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by ZeroHimself on 2008-05-02
Ok, just wondering here, I don't know how to find out what is going on...
I recently upgraded to hardy-amd64.. I was running gutsy x86....

I get horrible network transfer speeds

on gutsy(wireless and wired)
I would get about 300kb/s-700kb/s on ubuntu package downloads(or direct downloads for that matter)
I would get between 170kb/s to 350kb/s on torrents

both of these were for internet downloads

now with hard(wired or wireless)
I get about 500b/s - 60kb/s for updates(or direct downloads)

and about 30kb/s - 150kb/s for torrents

BTW I use an iwl4965 AGN driver for wireless and a realtek RTL8111/8168B PCIe gigabit lan controller.......

I don't have a 32-bit version of anything(or a windows version for that matter) to test and compare with....

any ideas?

---

### Post by Sylchat on 2010-08-15
realtek RTL8111/8168B is giving lots of trouble... it seems Ubuntu loads a bad driver and that the chip may seem 'bricked'. Mine was locked to 10Mb transfers, both on internet and LAN... Problem solved by doing a cold boot (shutdown, unplug the PSU for a while).


See here: [http://ubuntuforums.org/showthread.php?t=1436667](http://ubuntuforums.org/showthread.php?t=1436667)

---

