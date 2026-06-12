---
title: "lp vs lpadmin?"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by Ansible on 2009-07-09
So I've been having trouble getting printers to work on my friend's computer, where i just installed 9.04.  The system can see the printers and the icons appear in the Printer configuration window, but I can't print to them.  On the HP, the I get a 

Device Communications Error - 5012

error.  Google tells me that this may be associated with wacked out permissions, like not being a member of the lp group.  I go to Users and Groups and 'lp' is not listed.  Looking at the permissions on /dev/usb/lp0, it is in 'lp', the nonexistent group.  I create a group, 'lp', and then lp0 changes to '7'.  I change the lp number to '7'.  I also added my user to the lp group (it was already in lpadmin).  This has not fixed the problem. 

Should I add the lp0 to lpadmin?  lp0 was created automatically for me.  Will whatever creates these printers always create them under the wrong group?  how do I fix that?  Is lpadmin ubuntu's name for lp?  Or is lpadmin nothing to do with printers at all?

---

