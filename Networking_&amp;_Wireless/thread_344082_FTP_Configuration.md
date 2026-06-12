---
title: "FTP Configuration"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by Ducimus on 2007-01-22
I have set up my system with an FTP server and admin prog - GPROFTPD 
My box also has an additional  HD mounted and Shared for internal usage.
Now when I log into the drive into the home directory, i can of course see the folders there, but NOT on the second drive. Is there a way to script a link in that directory that i could use to allow linking to the other drive?

---

### Post by LotsOfPhil on 2007-01-22
Make symbolic link

ln -s /path/to/the/second/drive Name-of-link

Like: ln -s /media/hdb1 SecondDrive

---

