---
title: "Wireless again (sorry!)"
date: 2005-05-03
forum: Networking &amp; Wireless
---

### Post by nacnud on 2005-05-03
Hi folks,

I'm new to Ubuntu with and with a new laptop (Dell 600m), so I apologize for asking a very common question.  I can't seem to get my wireless to work, either through gui or the few iwconfig commands I tried.  I'm using an intel pro/wireless 2915abg with a netgear router.  What are the basic steps to active wireless?  I couldn't find a wicki on this and what I have found so far in the forums hasn't worked.....

Thanks very much.

---

### Post by krazeivan on 2005-05-03
[QUOTE=nacnud]Hi folks,

I'm new to Ubuntu with and with a new laptop (Dell 600m), so I apologize for asking a very common question.  I can't seem to get my wireless to work, either through gui or the few iwconfig commands I tried.  I'm using an intel pro/wireless 2915abg with a netgear router.  What are the basic steps to active wireless?  I couldn't find a wicki on this and what I have found so far in the forums hasn't worked.....

Thanks very much.[/QUOTE]
 if it's an 802.11g card you'll need someting like ndiswrapper you can follow the howto here: [http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

---

### Post by luca_linux on 2005-05-04
You should use the ipw2200 driver. You can follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)
In fact ipw2200 is not only for the 2200 b/g card but also for the 2915 a/b/g one.

---

### Post by nacnud on 2005-05-04
[QUOTE=luca_linux]You should use the ipw2200 driver. You can follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)
In fact ipw2200 is not only for the 2200 b/g card but also for the 2915 a/b/g one.[/QUOTE]

Thanks for the link.  So I need to install updated firmware and driver to get the card to work even if I'm not using wpa?

---

### Post by luca_linux on 2005-05-04
Yes, you have to install the latest firmware and driver, even if you don't want to use wpa (so just follow the first part of the howto).

---

### Post by nacnud on 2005-05-04
[QUOTE=luca_linux]Yes, you have to install the latest firmware and driver, even if you don't want to use wpa (so just follow the first part of the howto).[/QUOTE]


Thank you--this worked.  Wireless is up and running!

---

