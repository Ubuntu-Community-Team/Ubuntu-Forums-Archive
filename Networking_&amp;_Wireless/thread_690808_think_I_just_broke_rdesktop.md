---
title: "think I just broke rdesktop"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by akahige on 2008-02-07
Been working out the kinks on a dual monitor upgrade. Everything was working a-okay until I tried to build an icon to replace having to dump this into a xterm: "rdesktop -g 1680x1050 -D -P -x l 192.168.2.14:3389". In trying to test the thing, the icon got hit twice and things started breaking.

Now, the -P option -- which allows bitmap caching -- breaks the entire rdesktop display. Instead of the remote screen coming up, a black square of the specified size appears. Carrying this slightly further, I don't think that rdesktop is actually running without video display, because I can't cancel out of the remote login by hitting ESC, which I should be able to do.

There seem to be some other cascading issues of apps not remembering which monitor they opened on, or not expanding full screen. I assume that these issues are related because none of them were previously present, but I can't say for certain.

I looked at my Nvidia setup, and it doesn't look like anything changed. And I assume that if my X config got whacked, then X wouldn't work. Thinking that the -P thing might be related to a cache that needed clearing (but not knowing where to look for such a creature), I rebooted, but that didn't actually help things.

Anybody got any ideas?

---

### Post by mexpolk on 2008-02-08
First try reinstalling rdesktop, removing it first with purge option:

```


$ sudo apt-get --purge remove rdesktop


```

Then install it again:

```


$ sudo apt-get install rdesktop


```

If your X-Server is not working, try to find a backup from /etc/X11/xorg.conf, they're named like xorg.conf.1, xorg.conf.2, xorg.conf.etc... 

```


$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp
$ sudo cp /etc/X11/xorg.conf.1 /etc/X11/xorg.conf


```

I recomend to use the first backup: xorg.conf.1


grets

---

### Post by akahige on 2008-02-08
Thanks grets...

I actually just found an .rdesktop directory in my home directory. (Don't remember seeing it there before.) There was a cache directory in it and once I deleted the cache contents, things were back to the way they'd been.

So far as the X config, I think the thing that happened was that something in the Nvidia settings interface monkeyed with the way the screens were being positioned. After a lot of fiddling and rebooting, things got sorted. That kind of worries me, but since it's working again, I'm not going to complain too much.

---

