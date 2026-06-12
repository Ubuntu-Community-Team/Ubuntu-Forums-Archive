---
title: "Update ubuntu"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by d2core on 2009-12-21
Hi
i had already installed ubuntu 9.0 in my system. now i have ubuntu 9.1 .ISO file 

can i upgrade my exiting ubuntu version using this .iso file.

how can i plz help me



Thanks

---

### Post by Cheezespread on 2009-12-21
1.Depends on the ISO you have downloaded. You can find the instructions [here ]("http://www.ubuntu.com/getubuntu/upgrading") to do it with an alternate CD .

2. Upgrade from Update Manager in your machine if you don't mind downloading the updates again .

---

### Post by Temposs on 2009-12-21
If you just want to upgrade, you can do that without an iso file. Go to System->Administration->Update Manager. At the top of that window, you should see something about upgrading Ubuntu to 9.10. Just click on that, and it will start the upgrade process. You can even keep working while it does the upgrade :-)

---

### Post by d2core on 2009-12-21
its okay [Temposs]("http://ubuntuforums.org/member.php?u=169222")

but i don't have very good internet connection. so its not possible for me to upgrade online that's why i download .iso file first 

so i want to upgrade using this file only 


thanks for all replies.


Thanks

---

### Post by d2core on 2009-12-21
thanks [Cheezespread]("http://ubuntuforums.org/member.php?u=680436")

i think its help me

i 'll try it

thanks a ton

---

### Post by holastickboy on 2009-12-21
If you are still having problems: 

sudo apt-get dist-upgrade

---

### Post by 3rdalbum on 2009-12-21
> **holastickboy said:**
> If you are still having problems: 

sudo apt-get dist-upgrade

That command does not upgrade you to a new version of Ubuntu.

If you want to upgrade using an ISO file download, then you need the Alternate CD, and run the "cdromupgrade" script on the CD.

---

