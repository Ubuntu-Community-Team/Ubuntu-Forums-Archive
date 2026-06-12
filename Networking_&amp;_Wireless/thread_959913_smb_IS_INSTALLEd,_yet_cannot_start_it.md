---
title: "smb IS INSTALLEd, yet cannot start it"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by taseedorf on 2008-10-26
I cannot view my samba shares on my Linux box, from another Linux box I have

I tried sudo /ect/init.d/samba start
and I get
/etc/init.d/samba: command not found

What gives? If I boot into windows, I can see my shares...so I KNOW that it is my Linux here giving me problems.

I have samba installed and everything required... it just doesn't make sense to me. HELP!  It is annoying having to boot into windows just to check out some videos or music.

Okay, I made the file 'samba' exectuable....and the service will start, but I'm not seeing any folders in network? what gives

---

### Post by Yashiro on 2008-10-26
try smb://ip-of-sharedpc/sharedfolder

as for samba not running on your client pc, remove the packages ad re-install it maybe.

---

