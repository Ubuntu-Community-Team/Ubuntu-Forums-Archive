---
title: "remastersys"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by dzon65 on 2010-06-29
This guy wants me to install ubuntu on his pc.Since he only has a 10GB hd,I decided to make a copy of my system (minimal,2,6 Gb) with remastersys to save some time.But,which remastersys option should I choose in order to install it without my username and password ?I supose that's the dist option.But,will there be an option to fill in his name and his password during install?

---

### Post by philinux on 2010-06-29
> **dzon65 said:**
> This guy wants me to install ubuntu on his pc.Since he only has a 10GB hd,I decided to make a copy of my system (minimal,2,6 Gb) with remastersys to save some time.But,which remastersys option should I choose in order to install it without my username and password ?I supose that's the dist option.But,will there be an option to fill in his name and his password during install?

The dist option will produce an auto login livecd. Just like the normal ubuntu livecd. 
The only real difference between backup and dist modes is that backup mode copies the /home directory to the CD/DVD.  Dist mode auto-logins to the desktop with the LIVEUSER you create, whereas backup mode stops at GDM, waiting for a specific user on your current machine to login and eventually find their normal desktop on the CD/DVD and the installed system.

During the install I think you are prompted to create a user as normal.

[http://klikit.pbworks.com/Remastersys](http://klikit.pbworks.com/Remastersys)

---

### Post by dzon65 on 2010-06-29
So,if the dist cd will autologin straight to the desktop,how can he set his username and password?
Edit:my bad.So a dist install will prompt with a user and password setting.

---

### Post by philinux on 2010-06-29
> **dzon65 said:**
> So,if the dist cd will autologin straight to the desktop,how can he set his username and password?

Thats for the livecd booting. Once you've booted with the livecd you get straight to the desktop without gdm and there is an install icon as normal.

The backup livecd would stop at gdm and ask for YOUR userid and password.

---

### Post by dzon65 on 2010-06-29
Okidoki.Thanks Phil.

---

