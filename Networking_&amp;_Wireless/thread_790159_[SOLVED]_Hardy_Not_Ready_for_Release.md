---
title: "[SOLVED] Hardy Not Ready for Release"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by mandrill on 2008-05-11
So, Canonical released Hardy knowing that samba filesharing was broken. Check out launchpad and other bug reports. It doesn't work. If there is a way to make filesharing work someone please let me know. I have 50GB of music I can't access from any other pc in the house. A flagship LTS should not have these problems......   

OFFICIAL END OF RANT. (but read this - [http://www.degen.net/](http://www.degen.net/))

---

### Post by ajmorris on 2008-05-11
hi there,
smbclient works here... (i am using intrepid, but not that many updates have been pushed yet, and i cant see it being fixed in intrepid before hardy....)
syntax for smbclient is:
```
smbclient \\\\<ip-address>\\<share name> -U <username>
``` it will then prompt for the share password, then once in the help command will give you a list of commands, but basically, cd will change the directory in the share, lcd will change the directory on your computer, then you can use put and get to upload/download, other parameters such as tarmode for folders etc may need to be used also.

AJ

---

### Post by stinger30au on 2008-05-11
> **mandrill said:**
> So, Canonical released Hardy knowing that samba filesharing was broken. Check out launchpad and other bug reports. It doesn't work. I


works fine here.

---

### Post by squirrel_chaser on 2008-05-11
I have been mounting Windows shares with the smbclient using cifs since the beta and have not had any difficulty.  Someone here can certainly help you out with any specific problems.

---

