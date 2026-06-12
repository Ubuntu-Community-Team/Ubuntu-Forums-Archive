---
title: "How to copy files over network quickly!"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by Blutack on 2007-11-18
I have a server and laptop, both using DHCP and 54mbps wireless cards.  File copying over the network is stupid slow.
I tried samba which reckoned over an hour to copy a 650mb iso.
I am now using scp, but even with the -c blowfish option I'm getting ~160kbps speeds.  Both computers are reasonably quick (C2 Duo and a Sempron 3600+) and are not under much load.  The network is not doing anything else.  It wouldn't annoy me so much except when I downloaded the file from 'tinternet I got ~1100kb/s.  Surely I should be able to copy faster across the network!
Anyone any ideas?  What is NFS like?

---

### Post by Blutack on 2007-11-18
[Update - curioser and curioser!]
I started transferring a second file also by scp, and the speeds are exactly the same!  As in, ~160kbps for both transfers!  So it definately isn't a bandwidth thing.

---

### Post by njparton on 2007-11-18
I can't offer a solution to your specific problem, but I started out with a wired 10/100 network and I found even that painfully slow, topping out at 4 MB/s if I was lucky.

I've since invested in a gigabit switch and enabled jumbo frames all around. I now get up to 50MB/s write and up to 20MB/s read to my linux box from my Vista x64 machine.

Just some food for thought for you. If you're thinking about transfering a lot of large files around, gigabit is definitely the way to go! I can't even imagine attempting this with wireless, let alone 54 Mbps wireless.

---

### Post by Blutack on 2007-11-18
Eeek.  It's now down to ~30 kbp/s
This is stupid...where is my lighttpd...
OH FOR THE LOVE OF GOD - even with the file shared on lighttpd, ssh'ing into the remote box and using wget I'm getting a whole 66kb/s.
Thanks anyway njparton, not a lot of use in my situation I'm afraid as the server isn't anywhere that can be wired.
And it just got stupider - I just hooked the laptop into a wired port.  It is now ~80kbp/s.  This is 10 times slower than my internet over wireless.  Thanks anyway njparton, I'm off to find my external HD...

---

