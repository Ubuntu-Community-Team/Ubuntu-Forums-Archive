---
title: "Wubi Ubuntu installed well. Internet isn't working."
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by seremina on 2008-07-03
After a few years of frustration in trying to get Ubuntu [or other Linux distros] to work, I have finally had success thanks to Wubi Ubuntu 8.04.1; with one problem...how do I get it to access the internet? Here's a description of my internet:

Cable internet ran through a non-wireless router and into an RCA modem that was provided by the cable company. It works fine in WinXP Home, which my brother set up. I don't know how to set it up otherwise and he doesn't know how to do it on Linux nor Ubuntu. So please use simple English, if possible. Thank you so much.

I was told to post this here instead of in Wubi Ubuntu forum.

---

### Post by him610 on 2008-07-03
I responded to a similar problem a couple of days ago.

[http://ubuntuforums.org/showpost.php?p=5301195&postcount=7]("http://ubuntuforums.org/showpost.php?p=5301195&postcount=7")

Good luck.

---

### Post by seremina on 2008-07-03
Oh! Thank you so much. I hope it works. :)

---

### Post by seremina on 2008-07-04
I followed all the directions, except for getting drivers for my NIC card [which I do not know how to do] and I think the NIC card is Realtek but not sure. I'm guessing it failed because I didn't get the drivers? If so, what should I be doing next?

---

### Post by seremina on 2008-07-08
This is just to let people know it got fixed with help from someone on this forum. He helped me discover that Windows has, by default, 2 switches turned on that seems to do a sneaky...it makes it harder for you to get your NIC working on Linux. It'll only work on Windows because of this.

So I flipped the two switches for the NIC and it works without any messing around. The two switches, for others to read, are...

Wake on Lan after Shutdown. This is Disabled by default. Enable it. Finally, shut off Windows' power management for your NIC. It is enabled by default.

And everyone, thank you.

---

