---
title: "Tried to share internet connection, Now broken..."
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by drunkmatador on 2008-05-10
After a lot of hard work, I was finally able to get the wifi working on my laptop. It had a Broadcom BCM94311 card and it took awhile but I got it working through ndiswrapper.

Everything was fine until I followed this tutorial, [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
and now the internet does not work. When I try to visit a site, it automatcally goes to the "address not found" page. Just realized that I probably typed sudo before some of those commands, and it says not to.. maybe that is part of the problem?

Anyways how can I get it working again? This sucks. Thanks!

---

### Post by superprash2003 on 2008-05-10
you are usually required to type sudo -i in the beginning and then type those commands..

---

### Post by drunkmatador on 2008-05-10
Oh. Well I really don't remember which I did.. any ideas how to get it working again though?

---

### Post by drunkmatador on 2008-05-10
Nevermind I figured it out. Somebody in the irc suggested I uninstall netmasq and ipmasq, that did the trick. :)

---

