---
title: "Dlink dwl-g650"
date: 2004-11-18
forum: Networking &amp; Wireless
---

### Post by travisat on 2004-11-18
As of right now my wireless connection is no longer working.  I have the dlink listed in the title and it is an atheros chipset so it should work....and did for a while.  The first time I installed ubuntu it worked great.  But I couldn't figure out how to compile a kernel with menuconfig (I didn't install ncurses) so I uninstalled and installed another distro, which much to my chagrin didn't support my card.  So me being lazy and not feeling like fooling around with madwifi on my own I reinstalled ubuntu, but my wireless card wouldn't work anymore.  Being a fresh install I just decided to try it again and lo and behold my wireless worked.  However I started to upgrade it to hoary and about halfway through the wireless quit working.  It turned out that the router had got uplugged.  Anyway after I fixed the router I started bAck up ubuntu and my wireless no longer worked (it works great in my windowsxp dual boot).  Anyway I tried to figure out what was wrong and the bottom of the dmesg says that no ipv6 routers are present or something to that affect.  I have tried reinstalling several times but my wireless still won't work.  What is really strange is that the card looks like it is working.  When it works there are two lights that blink at the same time and they do that.  

Any help would be appreciated.

---

### Post by randy on 2004-11-21
Did you change any settings on the router? If not you may have to reinstall the restricted-modules package.

---

### Post by travisat on 2004-11-22
I got it sorted somewhat.  It wasn't anything wrong with ubuntu, but something is up with the router.  In order to get linux to work I often have to power cycle the router and I had to manually enter the dns servers.  But at least it works.

---

