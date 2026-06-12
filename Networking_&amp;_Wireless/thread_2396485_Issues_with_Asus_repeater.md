---
title: "Issues with Asus repeater"
date: 2018-07-16
forum: Networking &amp; Wireless
---

### Post by mistermagio on 2018-07-16
Hi,

So I've recently acquired a wireless repeater (Asus RP-AC55) because my router didn't reach everywhere I needed it to, but so far it has introduced a bigger issue than the one it was supposed to fix.

The main part issue is that it simply won't allow any Ubuntu device to connect to it. I've tried with 2 different laptops (two Zenbooks) + 1 old desktop on two different versions of Ubuntu (16.04 and 18.04), and it absolutely won't work with any of them. One of the Zenbooks has a Windows partition installed and the connection to the router works seamlessly when using Windows. I've also tried a few Android phones and all of them are able to connect to the repeater (and to the internet through it) without any issue.

The second part is that, when attempting to connect to the repeater from one of the Ubuntu-based devices, the repeater will simply crash, shutdown and reboot. For a few seconds there will be a question mark in the wireless indicator (running GNOME Shell by the way) and no access to the internet, and then the connection drops and the repeater reboots.

I'm willing to provide any logs you might need as long as I manage to get them (the near immediate reboot might make some logs rather hard to obtain), but as I don't know which ones might be useful I haven't included any in this post.

Hope someone will be able to help me fix my problem, and thanks in advance to those who will try.

---

### Post by mistermagio on 2018-07-17
After a bit more experimentation, I'm pretty sure it's a DNS issue: If I set an IP address manually, my laptop connects to the router and it doesn't crash , and ping 8.8.8.8 in the terminal gives positive results, but nslookup and normal internet browsing fails.

If I leave the IP address setting to "Automatic (DHCP)", it still crashes but on top of that trying to ping anything (before the crash) fails. I tried to set the DNS manually to Google's DNS (8.8.8.8, 8.8.4.4) (on top of setting a manual IP) for the connection to the repeater, but if I do that it crashes like it would if I didn't set the IP manually and nothing pings. 

I've also tried to set the repeater itself to Google's DNS, but that didn't bring any positive result either.

So I guess the issue is both with DNS and obtaining an IP, the first one of which I have no clue how I can "fix".

---

