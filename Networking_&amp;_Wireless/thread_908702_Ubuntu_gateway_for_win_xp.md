---
title: "Ubuntu gateway for win xp"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by cpricejones on 2008-09-02
Hello to any who's interested,

I'm a linux newb looking forward to getting my ubuntu box up and going again after a 6-month hiatus. I'm planning on setting up my ubuntu computer to act as a gateway/firewall/router for my win XP computer. I have been reading some threads about Samba, such as:

1. (**[COLOR="Red"][http://ubuntuforums.org/showthread.php?t=202605&highlight=use+samba+to+protect+winxp&page=61](http://ubuntuforums.org/showthread.php?t=202605&highlight=use+samba+to+protect+winxp&page=61)[/COLOR]**)
2. (**[COLOR="Red"][https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)[/COLOR]**)
3. (**[COLOR="Red"][https://help.ubuntu.com/ubuntu/serverguide/C/windows-networking.html](https://help.ubuntu.com/ubuntu/serverguide/C/windows-networking.html)[/COLOR]**)
4. others ...

I understand that Samba might be a good choice for doing this. The goal is to use the ubuntu box to protect the xp box among other things related to my research involving linux-only software.

However, I am wondering more about the hardware that I should use--the networking devices, cards, etc, (I don't know what's best). I've read elsewhere about problems with some network cards/components, and the chip on my motherboard had some issues in the past. I will not be doing wireless right now, but I might in the future if a girlfriend's laptop is involved (probably running XP or, dare I say, Vista) or if an iPhone is involved. If it is not that much more expensive to tack on wireless, or it's not too much a pain in the *** with configurations, then I'm probably game for trying wireless.

So here's the setup that seemed to make sense for me:

Cable modem --> Ubuntu 8.04 box via motherboard LAN
Ubuntu 8.04 box network card --> Win XP box network card

Here would be the hypothetical setup with Wifi (?):

Cable modem --> Ubuntu 8.04 box via motherboard LAN
Ubuntu 8.04 box network card --> Wifi casting device and/or Winxp box

So if you have any suggestions about hardware, then I'd really appreciate it. I've been looking around at my options, but I'm not sure how feasible they are. Any personal experience would be great. And if the Wifi casting would not cost more, then perhaps I should consider it.

Cheers,
CPrice :)

---

### Post by cpricejones on 2008-09-02
I've been reading more posts, and I still don't see any help. I'll let you know if I come up with a post that solves it. :)

---

### Post by cpricejones on 2008-09-03
Bump!

---

### Post by jimv on 2008-09-03
I think you're seeing this as being more complex than it is.

All you need to do is have two network adapters.  One for the internet connection, and one for your LAN.  For the NIC connected to the LAN, you need to run a DHCP server to provide IP addresses/internet gateway information to the other machines.

The second post in this thread give you the quick run down of how to set this up.

---

### Post by cpricejones on 2008-09-03
Ok, thanks. Maybe it is really simple, but I'm too new to this sort of thing to really know ... :)

---

### Post by jimv on 2008-09-04
Hey, it probably helps if I post the thread I was referring to...oops.

[http://ubuntuforums.org/showthread.php?t=418446](http://ubuntuforums.org/showthread.php?t=418446)

---

### Post by cpricejones on 2008-09-04
Ahh, thanks for reposting ... I found some links based on what you said (using "DHCP server" etc), but those were much more helpful. I had never heard of ICS before.

---

