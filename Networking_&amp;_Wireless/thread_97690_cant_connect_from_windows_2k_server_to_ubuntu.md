---
title: "cant connect from windows 2k server to ubuntu"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by tonysathre on 2005-12-01
i have set up a win 2k DC with AD, i have created shares on both boxes to test the connectivity.  the problem is that i can connect from my ubuntu client to my win 2k server and view the shares, but not vice versa, when i browse to the box with \\ubuntu it asks me for a username and password to connect with, i have tried all the username/password combinations on the box and none of them have allowed me in.  in AD after i joined the domain the box showed up under the computers OU so i know its part of the domain, also the have installed the webmin server on the ubuntu and that is the only way i can connect to the ubuntu box from my DC, thanks for any help or advice u can give me

---

### Post by wrtrdood on 2005-12-01
Did you use smbpassword to set up the ubuntu side?  Samba needs it.  Stuff will be visible but you can't access it without the user identification being set up.

---

### Post by tonysathre on 2005-12-01
k thanks, i set up the password and tried to connect again, but it wouldnt go, i browsed out with \\ubuntu got prompted for a username and password, i didnt know what user to use so i just tried them all with the new samba password but it still doesnt work, any ideas....... thanks

---

### Post by tonysathre on 2005-12-01
i figured it out, i had to set up a samba account as well with the smbpasswd -a username command, now it works thanks for the reply

---

### Post by wrtrdood on 2005-12-01
Sorry.  Should have been a bit more clear on that.  Glad you got it working.

---

