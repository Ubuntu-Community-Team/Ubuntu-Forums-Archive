---
title: "Torrent Downloading"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by badgerbailey on 2007-07-14
Hello,

I'm new to Ubuntu and new to Linux but very impressed with it so far. Just a small problem i'm having, I downloaded Azureus and installed it, I set it up and forwarded the correct ports through my router, downloaded a torrent file and all seemed well at first, the torrent tracker status was green, my NAT status is green and I was downloading at a reasonable speed, this lasted for about ten minutes, then nothing, the tracker light remains green, the NAT light remains green and I am connected to plenty of peers and seeds but nothing will download, I thought maybe Ubuntu comes with a pre installed software firewall that may need configuring but i've since found out that there isn't one, i have a windows machine on the same network and azureus works fine on that, i'm stuck as to what the problem could be as it says it is operating ok, just downloading nothing, any help would be much appreciated.

Thanks in advance


Badgerbailey

---

### Post by pinnball_wizard on 2007-07-14
Hi,
I have the same problem. Worked ok until two month ago for me. Havent been used azureus since then but used it last week and got strange probs. Same as you, work for 10-20 minutes then hanging. Ive seen that the memory usage rizes extremely just before azureus hangs. From 120 Mb to 600-700 Mb just with 4 torrents running.  I can also see that there are floods of feed connections to me happening on the port opened for Azureus. They are just in for a few seconds. Its a new fenomena that Ive never seen before. Im using Ubuntu 7.04 and roaming on Wlan. Ive also seen that I sometimes loose my dhcp address when running azureus. This is also a new issue, dont happen if not azureus is running. Reboot is only solution.

My tip is that some new patch to ubuntu dont goes ok with azureus, maybe roaming with both Wlan card and dhcp and traditonal eth.card (not used but still eth-0). Another tip is that there are new features in azureus 3.0 that makes it more stable if there are floods of connections, just guessing that this make the memory usage rize. (Im running Azureus 3.0 on XP without probs).
My next step is to disable roaming and use a hardcoded IP to see if it works.

Ive seen same the problem in other posts without other solutions than changing to another torrent client. I like Azureus since its almost the same on all platforms and hope that someone can help us with this issue.

Regards

---

