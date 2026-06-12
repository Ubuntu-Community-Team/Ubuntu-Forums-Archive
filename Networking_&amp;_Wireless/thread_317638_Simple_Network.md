---
title: "Simple Network"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by orbit1979 on 2006-12-12
I am a linux noob and want to set up a simple network. 
I have a desktop with printer running Ubuntu, and a laptop running XP and Ubuntu. They are connected together via ethernet cable and router.

I would like to share the printer and share my home folders between the two.

What is the simplest way to achieve this?

Suggestions would be appreciated.

---

### Post by kevinatkins on 2006-12-12
Hi,

Which version of Ubuntu are you running?

---

### Post by orbit1979 on 2006-12-12
Ubuntu 6.10. using KDE desktop if that matters.

---

### Post by kevinatkins on 2006-12-12
OK .. I'm using Gnome so the setup will be somewhat different.. Printer sharing is fairly straightforward using cups (dead easy using Gnome and Ubuntu 6.10). As for file sharing, you've got two choices - either NFS, or Samba. Samba would probably be better if you've got an XP machine on your network. You'll want to install the samba server on both Ubuntu machines, samba client should be installed by default. Then browse the forums for help on setting the server up.

---

### Post by orbit1979 on 2006-12-12
I try that out. Thanks

---

### Post by Iowan on 2006-12-13
[http://www.ubuntuforums.org/showthread.php?t=202605]("http://www.ubuntuforums.org/showthread.php?t=202605")
This one might be helpful.

---

