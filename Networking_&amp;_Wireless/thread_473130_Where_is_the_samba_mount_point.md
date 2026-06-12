---
title: "Where is the samba mount point?"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by britlion on 2007-06-13
Okay, I'm a week shy of being a linux newb.

But I can't find the answer to this question. I can connect to a windows share by using nautilus, and look at the files. I can't access them via something like VLC however, because it's a samba share. 

I can copy the files over - but it was rather convenient to be able to use remote files like local ones where appropriate.

Does the system make a mount point equivalent I can get a program like vlc or pdf reader to read the file from directly, or will it only work if I copy the file to local store first?

---

### Post by bukwirm on 2007-06-13
Look into [smbfs]("https://help.ubuntu.com/community/SettingUpSamba#head-d0cf07ad854d6a463aa1ba9345600732832d47ef").

---

### Post by dmizer on 2007-06-13
i wrote a howto for cifs.  you can follow the second link in my sig.

you should use cifs instead of smbfs because you will get better speed, and the ability to transfer files larger than 2gig.

---

### Post by britlion on 2007-06-14
Awesome. Cifs worked like a charm. Thankyou!.

It's a very steep learning curve, but with the support of people like you guys, I haven't quite had to go back to windows (Though I'll admit to a virtual machine :)

---

