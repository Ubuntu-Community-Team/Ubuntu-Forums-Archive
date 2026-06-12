---
title: "File sharing via wireless network."
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by fullmetalgerbil on 2008-05-31
Currently I'm running Windows xp on a desktop and Ubuntu 8.04 on a laptop. I've got them sharing an internet connection through a Linksys WRT54G wireless router and I'm wondering how to set up file sharing between the computers.
Any help would be much appreciated.

---

### Post by superprash2003 on 2008-06-01
to share files on ubuntu to a windows pc you have to install samba [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html) and to share files on xp to ubuntu you need to enable file sharing [http://www.practicallynetworked.com/sharing/xp_filesharing/](http://www.practicallynetworked.com/sharing/xp_filesharing/)

---

### Post by SWT_nux on 2008-06-01
I was surprised this wasn't a common feature. I think having a wireless router with the main computer wired and wireless devices like PS3, laptop and others is pretty common. Any advice you can give to us newbies would be greatly appreciated.

---

### Post by dps77 on 2008-06-03
> **SWT_nux said:**
> I was surprised this wasn't a common feature. I think having a wireless router with the main computer wired and wireless devices like PS3, laptop and others is pretty common. Any advice you can give to us newbies would be greatly appreciated.


*******************

Hi SWT_nux,

Did you try to posted advice/instructions re: SAMBA etc.?  If so, did it work?  It sounds like I have an almost identical setup as yours, and I also am trying to enable filesharing (XP desktop <-> Ubuntu laptop via Lynksys router).  Right now I'm just e-mailing files back and forth which is not optimal...
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

---

### Post by dps77 on 2008-06-04
I read the links from superprash2003's post (thanks superprash2003!), and I roughly followed those instructions.  I just added Samba as an application from the Applications menu, then added a "Share" folder using Samba (System > Administration > Samba), set the access for that share to a particular user, then added that user under Samba > preferences > Samba users, and added the Windows username (I got this from XP: [pc name]\Guest) and a new password, then went to Network places in XP, added a network place, chose another network location ("\\[Ubuntu laptop IP]\[Ubuntu "share" name, set in Samba]", drop the brackets).  XP asked for my password and successfully opened the share folder on my Ubuntu laptop.  I shot off my firewalls during all of this, but turning them back on had no effect (I still had access).

---

### Post by dps77 on 2008-06-04
> **dps77 said:**
> I read the links from superprash2003's post (thanks superprash2003!), and I roughly followed those instructions.  I just added Samba as an application from the Applications menu, then added a "Share" folder using Samba (System > Administration > Samba), set the access for that share to a particular user, then added that user under Samba > preferences > Samba users, and added the Windows username (I got this from XP: [pc name]\Guest) and a new password, then went to Network places in XP, added a network place, chose another network location ("\\[Ubuntu laptop IP]\[Ubuntu "share" name, set in Samba]", drop the brackets).  XP asked for my password and successfully opened the share folder on my Ubuntu laptop.  I shot off my firewalls during all of this, but turning them back on had no effect (I still had access).

**************

Ok, I misspoke-- I subsequently had to add the respective IP's for each other's firewalls.  Once I did that, everything worked fine.

---

