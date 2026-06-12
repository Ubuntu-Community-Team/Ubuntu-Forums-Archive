---
title: "samba server w/ xp clients verrrrry slow"
date: 2005-05-12
forum: Networking &amp; Wireless
---

### Post by jce on 2005-05-12
first off, I'm (fairly) n00b w/ *nix's and this is my first day running ubuntu.

Love it so far.

however, I've recently installed samba on my machine and notice that when I connect to the share from a XP Pro client, the file transfers are PAINFULLY slow.  I've connected from OSX clients and see a huge difference in the transfer speeds.

Is there any settings in samba that I can tweak w/ to improve the performance when a windows XP client connects?

thanks.

---

### Post by GrumpySmurf on 2005-05-12
Well, if you listen to Microsoft, Samba is much slower than Windows at filesharing.  I think they're biased, though.

My Samba server is actually on SuSE Professional.  I haven't experienced any performance issues with the default configuration.  I would have to check into the differences between Ubuntu and SuSE to be of real use, but you may wish to look into the Samba performance tuning guide here:

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html)

Also google for "samba performance tuning" for a number of good resources.

---

