---
title: "update manager crashed"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by Zulu Lion on 2010-01-24
Hi...need help.
Update manager froze.  On rebooting required that dpkg --application -a by entered in terminal...but requires super supervisor permissions...what does this mean and how do I correct the error?

Thanks
Zulu Lion

---

### Post by bapoumba on 2010-01-24
Moved to ABT.
You need to prefix the command with sudo. That will grant you admin privileges in that terminal. You will not see the password you enter (use your user password if this is the one created when installing ubuntu) for security reasons. Please paste here any error you get.

---

### Post by Joeb454 on 2010-01-24
I imagine it's asking you to run ```
sudo dpkg --configure -a
``` Try that, and as bapoumba said - post back any error you get :)

---

### Post by Zulu Lion on 2010-01-25
thanks that worked...

I have problems with VLC and totem being unable to play VOB files....any ideas?

Regards,
ZL

---

### Post by Zulu Lion on 2010-01-25
installed libdvdcss thats seems to have worked!

Thanks a lot....

Zulu Lion, South Africa

---

