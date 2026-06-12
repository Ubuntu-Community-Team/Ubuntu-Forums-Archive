---
title: "Can't Get DNS Working"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by Bezmotivnik on 2007-01-14
After innumerable tries, I've discovered how to trick my notebook's RT2500's mini-PCI card into working, at least in unencrypted "stupid" mode (it has to do with the up/down bug in Linux with this device, but that's another thread) in 6.06 Live.

Everything works perfectly like this -- except I can't get DNS to work.  I've entered several DNS addresses in the "DNS" section of the networking GUI, but no dice.

If I know the IP of the site, I can enter it in the browser and go right there, but URLs won't work.

Any thoughts here?

As always, thanks for any help!

---

### Post by robertpolson on 2007-01-14
I am not network expert, but aren't DNS something that is provided by your ISP provider, so they have to be exact?

Or just use this:

[http://www.opendns.com/](http://www.opendns.com/)

    *  208.67.222.222
    * 208.67.220.220

---

### Post by Bezmotivnik on 2007-01-14
> **robertpolson said:**
> I am not network expert, but aren't DNS something that is provided by your ISP provider, so they have to be exact?
Yes, but it wouldn't work.

I tried some public servers and they wouldn't work either.

I just can't get URL lookup function to work for some reason.  Weird, huh? :confused:

---

### Post by Bezmotivnik on 2007-01-14
I eventually got it working.  I am not sure how.

Or how well.

But it IS working and I am entering this online in Ubuntu 6.06 Live w/my notebook in wireless mode.  :-k

---

