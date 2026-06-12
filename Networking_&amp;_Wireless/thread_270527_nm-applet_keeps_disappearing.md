---
title: "nm-applet keeps disappearing"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by colonelk on 2006-10-03
Can anyone help please?

nm-applet seemed to be working fine now all of a sudden it no longer shows up in the notification area unless I go to the terminal and type in "sudo nm-applet".  If i keep the terminal window alive it stays there.  If I shut it it goes.

How do I keep it there all the time please?

I've checked the /etc/network/interfaces file and made sure that auto was commented out except for the lo interface.  I've also checked the "sessions" tool and checked that "nm-applet --sm-disable" is listed.

Any other ideas from the Linx gurus out there?

Any help appreciated.

TIA

CK

---

### Post by ciscosurfer on 2006-10-04
Try this out in a terminal:```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor
```and make sure you have nm-applet --sm-disable set in your sessions tab as well like you mentioned.  Logout then log back in.[SIZE=-1][/SIZE]

---

### Post by colonelk on 2006-10-05
Thanks, but it didn't work :(

---

### Post by benhall on 2006-10-17
Just had the same problem. I found that adding a "notification area" applet to the tool bar sorted my problem. I had removed it by accident trying to deselect a printer.

HTH

---

