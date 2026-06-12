---
title: "Restricted drivers management"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by jratliff on 2008-12-15
Request:

How do I open the restricted drivers management. It is not under System->Administration as some sites suggest.

Any help on accessing the restricted drivers management would be greatly appreciated.

Background:
I am trying to get my Linksys WPC54G wireless card working. I've gotten pretty far and found out that it doesn't work "out of the box" but needs a driver enabled. I found [this]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCMCIA"):

"Get recognized in the setup process, but unable to use it. After setup completes, the card is shown in the network interfaces (as eth0, all hardware details are shown too), but the system is unable to activate it. Updating the firmwares (link broken) fixes the problem. To do this when Ubuntu starts, open the restricted drivers management and enable bcm43xx."

---

### Post by gettinoriginal on 2008-12-15
Right click your panel on System, edit menus, go to admin and make sure that Hardware Drivers is ticked.  Check while you are there for any other items you may want are ticked.  :p

---

### Post by oldos2er on 2008-12-15
Hit Alt-F2, and type in "jockey-gtk"

---

### Post by Aearenda on 2008-12-15
It's just called 'Hardware Drivers' in 8.10. But I think the page you referred to is out of date. Are you sure yours has the Broadcom chipset? Running the terminal command 'lspci' should tell us.

Have you seen [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) ?

---

### Post by jratliff on 2008-12-15
Thanks to all. Aearenda, you were correct on all counts.
1. It's now just Hardware Drivers (as gettinoriginal said)
2. The page was out of date.
3. I definitely have the Broadcom chipset (old laptop, old wireless card).

I followed the link, downloaded the package, installed it, and now I'm using my wireless card. Thanks so much...

SOLVED

---

