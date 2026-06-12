---
title: "Is it possible to keep home partition from 32 bit version and install a 64 bit one?"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by legolas_w on 2010-04-11
hi,

I have ubuntu 9.10 32 bit edition installed and i want to install ubuntu 10.04 64 bit edition.

I have a separate home partition, and I want to know whether it is possible to keep the home partition from my previous version (9.10 32 bit version) and install the 10.4 64 bit version?

Are they compatible with each other?

thanks.

---

### Post by eriktheblu on 2010-04-11
For the most part I think you should be ok.

It should just be the applications that differ between 32 and 64 bit, and those aren't typically stored in /home. Your pictures, documents, and files ought to be compatible.

---

### Post by cascade9 on 2010-04-11
Going from 32bit to 64bit and keeping home is no problems. 

Its possible that some of the config files in /home might cause problems when you move over, but if there are any issues (I've never had any) then just delete the config files, or go to synpatic, find the program, 'completely remove' then reinstall it ('completely remove' also removes any config files you have).

---

### Post by srs5694 on 2010-04-11
One other caveat: Be sure that the user IDs (UIDs) of user(s) on the two systems match each other. If you're the only user, chances are this will happen automatically. If not, you'll have to either create users in the same order on the new installation or adjust the UIDs in /etc/passwd by hand. (UIDs are in the third colon-delimited field on each line in this file.)

---

### Post by legolas_w on 2010-04-12
Thank you everyone.

---

