---
title: "Server Problem"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by Peter_APIIT on 2007-05-25
Hello all Ubuntu expert, i have a Ubuntu 7.04 server edition installed in my computer. 

How to get in to GUI interface ? I have issues startx but the terminal return packages not return. 

How to admin the apache and mysql ?

Thanks for your help. 

Your help is greatly appreciated by me and others.

---

### Post by swamytk on 2007-05-25
> $ sudo apt-get install ubuntu-desktop
The above will install GUI interface

---

### Post by reckless2k2 on 2007-05-25
Yeah there is no GUI under the server edition. You have to add it yourself. BUT, if you are looking ONLY to admin apache and mysql while keeping your resources down on your machine, install webmin instead. Don't rush to install the full desktop because you may have not wanted the desktop specifically because of the bloat. Install webmin and SSH packages so you can remote into the machine from another machine and admin your box.

---

### Post by ruy_lopez on 2007-05-25
For managing mysql take a look at phpmysqladmin.

---

