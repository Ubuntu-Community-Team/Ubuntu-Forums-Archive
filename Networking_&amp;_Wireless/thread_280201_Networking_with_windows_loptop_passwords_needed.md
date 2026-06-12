---
title: "Networking with windows loptop passwords needed"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by My Name on 2006-10-19
Hi guys,

I have installed edgy and the network has been connected automatically. Fantastic! now, I can transfer files from ubuntu to the windows laptop, but i can't connect to the ubuntu machine fom the leptop as it is asking for a login name and password.  I like that it needs a password, so i don't want that disabled, but when i use my ubuntu login name and password it will not let me in.

Any ideas about this?

I also have my printer on the ubuntu machine which i would like to share with the laptop, which i may need help with as i have yet to get this printer working on the network.

Thanks for the help...

---

### Post by Crooksey on 2006-10-19
[http://ubuntuforums.org/search.php?searchid=8958765](http://ubuntuforums.org/search.php?searchid=8958765)

Look into setting up an SMB folder on Ubuntu, then share that.

---

### Post by Jussi Kukkonen on 2006-10-19
> now, I can transfer files from ubuntu to the windows laptop, but i can't connect to the ubuntu machine fom the leptop as it is asking for a login name and password. I like that it needs a password, so i don't want that disabled, but when i use my ubuntu login name and password it will not let me in.
How are you trying to connect? SMB (Windows filesharing), ssh, ftp...
 If it's SMB, have your taken a look at *System-Adminstration-Shared Folders*? Samba (the SMB implementation on linux) takes care of sharing the printer too, although I'm not sure if that works from the GUI I mentioned...

---

### Post by My Name on 2006-10-19
Well the folder has the smb symbol on it...

---

