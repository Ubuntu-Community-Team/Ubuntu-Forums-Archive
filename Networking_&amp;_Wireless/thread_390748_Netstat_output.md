---
title: "Netstat output"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by juyanith on 2007-03-22
Okay, I'm confused by this one. I have my computer set up to allow SSH access through my router which works fine. However, I was trying to figure out which IP address was passed to my home computer when I connect from work (I'm not sure if it goes through a proxy or not). Anyway, I did the usual netstat check while logged in and got the following:

[FONT="Fixedsys"]tcp6       0      0 ::ffff:192.168.0.12:ssh ::ffff:nnn.nnn.nnn.:3585 ESTABLISHED[/FONT]

Note the last address (::ffff:nnn.nnn.nnn.:3585). I have removed the first three octets and replaced them with "nnn" since I don't want to broadcast it, but the last octet is missing entirely. Can someone explain to me how this is possible? Perhaps I'm a bit confused about the whole ipv6 format, but I would have expected at least a "0".

As to why this is important, I'm planning on restricting access based on IP, but I don't know which ip to allow. I realize I could allow the entire range based on the first three octets, but I'm confused as to what happened to the last one.

:confused:

---

### Post by kidders on 2007-03-23
Hi there,

I clicked on this thread just after you posted it, hoping someone would provide a clever solution. No such luck. :-(

Unfortunately, the only suggestion _I_ have is not to use netstat. I played with it for a while, and went through its man page with a fine tooth comb, but there doesn't seem to be a way to stop it truncating long addresses. :mad:

Another application that can show you the addresses of the remote ends of current connections is **iftop** which, if I remember correctly, doesn't suffer from the same weird design flaw. Perhaps you could use that.

---

### Post by juyanith on 2007-03-23
Thank you! That answers the question. Apparently netstat has a limit of 19 characters for the ip address and it was simply being truncated. Now I need to see if I can figure out where to submit this "bug", but my initial problem has been solved.

=D>

---

