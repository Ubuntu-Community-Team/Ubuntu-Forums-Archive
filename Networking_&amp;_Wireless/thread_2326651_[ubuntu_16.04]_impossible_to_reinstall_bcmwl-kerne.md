---
title: "[ubuntu 16.04] impossible to reinstall bcmwl-kernel-source on Dell XPS 15 9550"
date: 2016-06-03
forum: Networking &amp; Wireless
---

### Post by david524 on 2016-06-03
Hi,

I dual-booted Windows 10 with Ubuntu last week, and it worked like a charm for 5 days.
However, my WiFi connection turned slow at a point, so slow that it was taking me 2 minutes to load even a google search page.
I decided to search for similar problem, and I ended up using the command:
```
[COLOR=#111111][FONT=Consolas]sudo apt-get remove --purge bcmwl-kernel-source[/FONT][/COLOR]
```

However, as I am a smart guy, I did not notice that my new Dell XPS 15 9550 did not have any rj45 connector...

I tried to fresh install the bcmwl-kernel-source.deb package, but either it freezes
or a fatal error shows up with the following message:
```
modprobe module wl not found
```

And I do not know how it could be related, but since I purged the bcmwl-kernel-source, my Ubuntu freezes when shuting down,
playing me the Ubuntu animation infinitely. It looks like it can come from broken packages, or something like that.

Thank you for reading!

---

### Post by david524 on 2016-06-04
Ok, after trying a lot of things, I do not why, I did :
```
sudo apt-get bcmwl-kernel-source
```

Apparently, the apt-get found the file to build as I did not have any internet connection and it worked.
However, at the end of the build, I saw this message in the terminal:
```
[COLOR=#000000][FONT=Verdana]DKMS: install completed.[/FONT][/COLOR]
**Segmentation fault**
```

I rebooted and... the WiFi was there!

However, even if the drivers are now working well, I am still thinking they are broken, because when I am shuting down the computer, it hangs
on the Ubuntu animation screen, over and over. I may have something broken but I don't know how to fix it.
On the forum, a lot of people had the same issue, and they modify the /etc/default/grub file but I am pretty sure this fix is not good for

If someone can share any idea to fix it, it would be nice.
I hope the above "fix" could also help anyone that did the same mistake as I did.

Thank you.

---

