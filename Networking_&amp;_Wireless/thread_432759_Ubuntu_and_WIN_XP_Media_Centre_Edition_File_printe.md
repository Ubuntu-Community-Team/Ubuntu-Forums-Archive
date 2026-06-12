---
title: "Ubuntu and WIN XP Media Centre Edition File /printer sharing"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by dambuster on 2007-05-04
Hi,
Very new (and green) to Ubuntu. I loaded v6 on to a compaq desktop and upgraded to the latest release.
I have another PC (Dell with Win XP Media centre edition loaded) 
The Dell PC connects to the internet via ethernet (hard wired) Belkin router with wireless capability.
The Compaq PC (Ubuntu) connects to the internet via a Belkin wireless PCI interface card.
The ubuntu PC connects to the internet and works fin. I would like to share files, folders and printers between the 2 PC's. I understand this is possible could somebody please point me in the right direction and to where I can find some reasonable documentation that isn't too technical.

Thanks
Dambuster

P.S. I'm amazed by Ubuntu it's an incredible OS.

---

### Post by murlosad on 2007-05-04
Well, if you are looking to share files/printer from the XP machine to the Ubuntu machine all you've got to do is enable sharing on XP and Ubuntu should be able to see it.

If you are looking to go the other way you need to setup Samba on the ubuntu box, which can be used for both file and print sharing, along with lots of other stuff.  There are some really good threads on this forum about setting up samba.  [http://us1.samba.org/samba/](http://us1.samba.org/samba/)

You can also share a printer from ubuntu to XP using cups, then search for a network printer in XP and install the proper drivers. Again there are lots of threads on that topic too, it's just a matter of knowing what to search for.

Lots of good stuff here: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

Hope this helps a little, or at least gets you started.

---

### Post by ivanoz on 2007-05-31
hey, i read the thread and i have a problem, first of all:

i have a desktop with win XP my printer is installed in that one
then my laptops has Ubuntu Feisty

now i want to share my printer, ofcourse, in win my printer is set up to share and when i wnat to install the shared printer in my Ubuntu, it asks me for user name and password for my win network workgroup, as i leave it blank. Aparently my printer is installed but when I send a test page, nothing happens.

please, if someone can help me.

Cheers

P.S. I'm feirly new in Ubuntu ;)

---

