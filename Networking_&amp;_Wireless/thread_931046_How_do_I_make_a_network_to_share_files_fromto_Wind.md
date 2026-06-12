---
title: "How do I make a network to share files from/to Windows Vista to Ubuntu?"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by riahc3 on 2008-09-26
How do I make a network to share files from/to Windows Vista to Ubuntu? Doesnt Ubunutu support UPNP which would automatically configure everything (almost)?

---

### Post by gregphil on 2008-09-27
Dream on......

You need to install and setup Samba on the linux machines.  (go to package manager etc).  Then you will need to edit /etc/samba/smb.conf **as root** and finally restart samba to see the results.  Don't forget to wait a few minutes for smb shares discovery to take place on the network (up to 12 minutes).  The linux command line tools "smbtree" and "smbclient -L COMPUTER" are useful for debugging the configuration.

This can be complex (it shouldn't be) and there are outstanding bugs in ubuntu 8.04..1
(the bugs listed below actually apply to browsing all authenticated Windows shares, not just on ADS networks).  However unauthenticated winodws shares (which are a huge security leak) can be browsed by ubuntu.  Browsing under kubuntu does not have this browsing bug because the bug is part of the gnome gvfs library (so only gnome GUI apps like Nautilus are effected)

[Bug #207072 in gvfs (Ubuntu Hardy): “nautilus does not display samba shares for machines inside an ADS network.”]("https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072") 

[Bug 524485 - nautilus does not display samba shares for machines inside an ADS network. (gvfs)]("http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26") 

Good luck. (you have lots of manual reading in your future (try man smb.conf))

---

