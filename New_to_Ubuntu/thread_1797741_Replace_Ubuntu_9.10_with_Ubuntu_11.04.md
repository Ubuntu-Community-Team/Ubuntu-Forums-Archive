---
title: "Replace Ubuntu 9.10 with Ubuntu 11.04"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by sstextile on 2011-07-05
My ubuntu 9.10 is installed side by side windows 7. I have Ubuntu 11.04 in pen drive. I want to replace Ubuntu 9.10 with Ubuntu 11.04. 
If i open Ubuntu 9.10 and then insert pen drive containing Ubuntu 11.04 and start installing it over Ubuntu 9.10. Will it disturb my windows 7.
Please help.
If any body has experiance doing so please eleborate.

---

### Post by abybaddi on 2011-07-05
> **sstextile said:**
> 
Will it disturb my windows 7?

Of course not.
Let your current home dir be /home/x
Install your 11.04 as usual but use a different login name (let it be y) and home directory (/home/y)
After installation is complete make an administrator by any name. Login to that admin.
Open users and groups.
Edit your "y" account.
In the third tab put the home dir from "/home/y" to "/home/x". Click apply.
Log off.
Login to "y".
Delete the admin. Enjoy!!!

---

