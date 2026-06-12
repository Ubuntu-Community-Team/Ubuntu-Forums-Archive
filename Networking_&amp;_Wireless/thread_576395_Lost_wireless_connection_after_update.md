---
title: "Lost wireless connection after update"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by toni2 on 2007-10-15
I have a notebook with intel wireless.
After last ubuntu 7.04 updates (openoffice, etc...), it is not connecting now to wireless. It try, but don't connect.

It seems a problem like this:
   [http://ubuntuforums.org/showthread.php?t=197744](http://ubuntuforums.org/showthread.php?t=197744)

Has anyone same problem?

---

### Post by toni2 on 2007-10-23
Well, some days ago I restarted it, and without do nothing, wireless was working again?!?!

Then, I make upgrade to ubuntu 7.10. And afterwards, it is not working again.
Now this seems to be really broken. Ubuntu 7.10 doesn't work well with intel 3945 wireless.

I have started with ubuntu 7.04 cd and wireless intel 3945 works.
Starting with ubuntu 7.10 cd and wireless intel 3945 doesn't work.

---

### Post by boozker on 2007-10-23
Same as with my topic:

[http://ubuntuforums.org/showthread.php?t=587800](http://ubuntuforums.org/showthread.php?t=587800)

And i have the same driver and everything. I have been working on this for hours. NOTHING here on the forums works. I'm going to just reinstall previous version of Ubuntu i guess and check back in a couple months. 

I give up. What's the point. I love the built in Beryl stuff, but it's just not worth it. Stupid upgrade for a huge amount of us.

---

### Post by toni2 on 2007-10-24
I have tried to uninstall network-manager-gnome and network-manager and install wicd. Someone points that this is a gnome network manager bug. But this doesn't fix anything, wireless don't work.

I have tried starting from kubuntu 7.10 cd and it also doesn't work.

Then: Ubuntu 7.10 and kubuntu 7.10 doesn't work with intel 3945 wireless. It shows wifi's, but when I try to connect, it doesn't connect (tried with WEP and with no-security).
It is labeled as an "official" Ubuntu 7.10 bug in anyplace??

Ubuntu 7.04 works perfectly, and I think to do a downgrade now (reinstall it).

---

### Post by toni2 on 2007-10-26
It's a ubuntu 7.10 kernel problem (ie 2.6.22-14) and it doesn't work.

With old kernel 2.6.20-16 and with ubuntu 7.10 wireless connection works well.

---

