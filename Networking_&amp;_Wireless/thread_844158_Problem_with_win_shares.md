---
title: "Problem with win shares"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by zeezam on 2008-06-29
I hope this is right section.

Have allways had some problems with accesing win shares from my Ubuntu htpc.
I have a home network with one XP desktop and one htpc with Ubuntu 8.10.

Mostly I can't see anything if I go threw Places > Network > Windows network.

Sometimes if I reboot I can see the shares again (only sometimes!).

I can't even ping the XP desktop when the problems appears.
If I reboot the problem sometimes disappears.

Tried to modified the fstab with mount -t cifs but that doesn't help me when I can't access the XP computer sometimes.

I'm using manual IP adress on both computers.
Internet works fine allways.


Any ideas? :(

---

### Post by Iowan on 2008-06-29
7.10 (Gutsy)? Try Places>Connect to Server - it works better on my Gutsy machine.

---

### Post by zeezam on 2008-07-06
> **Iowan said:**
> 7.10 (Gutsy)? Try Places>Connect to Server - it works better on my Gutsy machine.

Doesn't work eather. Now when I reboot I found the computer in the network but with no shares.

I don't have 7.10, it's 8.10.

---

### Post by kimbob on 2008-07-08
I too, have the same problem in 8.1. Sometimes all the computers are there, then just seem to go away! Drives me nuts. Still haven't found an answer....

---

### Post by alliance1975 on 2008-07-10
I have been trying to solve this problem for a few days now and discovered something last night. If I enable UFW then I have the same problem of not seeing the windows shares, (i.e. 0 items in places>network>windows network). But when I disable UFW I can see all the shares and shared folders. I have verified this. If anyone has suggestions please furnish. I will continue to experiment.

Further experimentation showed that when sudo ufw default allow was performed the windows shares became visible and accessible. reverting back to sudo ufw default deny made them inaccessible again. Throughout all this, however, my internet access via my router remained intact. Apparently I must learn more about ufw and allow communications to my window share ips.

---

