---
title: "Networking....Ubuntu 8.10 and windows XP"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by sajixavier on 2009-01-22
Hi
i have recently installed ubuntu in a system that is a part of network, that contain windows xp machines. Installation went well.Also i am able to access the windows network files that are shared. 
I have shared some folders in windows xp network (also it is a workgroup not domain network) that are hidden from other windows machines (by placing $ at the end of each name).
My problem is that now that ubuntu machine is  part of this workgroup network, it is showing the hidden folders of windows network.
Is it possible to hide those shared folders from ubuntu machine too....

---

### Post by Coreigh on 2009-01-22
After a quick read of a handful of google items [[COLOR="Blue"](here)[/COLOR]]("http://www.google.com/search?source=ig&hl=en&rlz=&=&q=Ubuntu+Windows+hidden+share&btnG=Google+Search&aq=f") it seems that Samba is not designed to comply with the Windows default method of hiding a share. The best advice is to make sure the shares are secured with a password if there are concerns over who should access what.

---

### Post by sajixavier on 2009-01-22
thanks for the reply

---

### Post by sajixavier on 2009-01-23
how can i secure the shared folders using passwords in windows xp. i didn't see any password setting options in it...

---

### Post by cariboo on 2009-01-23
I've never tried it, but hidden files in Linux start with . (period), you could try adding a period to the start of the share name instead of doing it Microsofts non-standards comliant way.

Jim

---

### Post by sajixavier on 2009-01-23
Yes i tried that. it is not working...

But i tried another way...Currently i am using the guest account for customers to access computer (internet Cafe)..So from google searching, i got an idea and give the guest account,  password. In ubuntu i have created an unprevilaged user. so now ubuntu is not displaying any files that are shared by another computers including hidden one too....this is what i was looking for..

---

