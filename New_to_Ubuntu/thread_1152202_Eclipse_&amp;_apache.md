---
title: "Eclipse &amp; apache"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by UK00 on 2009-05-07
Hi I'm trying to make /var/www/,the apache default web root, my workspace in eclipse 3.4, and I'm getting the message that it cannot be created or is in use.  When i try to open eclipse using sudo in terminal it only will open 3.2 not 3.4.  Any input here would be much appriciated.  Thanks for your time.

---

### Post by tarps87 on 2009-05-08
> **UK00 said:**
> Hi I'm trying to make /var/www/,the apache default web root, my workspace in eclipse 3.4, and I'm getting the message that it cannot be created or is in use.  When i try to open eclipse using sudo in terminal it only will open 3.2 not 3.4.  Any input here would be much appriciated.  Thanks for your time.

It is probably opening eclispe 3.2 because this is the one in the system path. You can try running eclipse using the full path to the launcher, but I strongly recommend that you do not run any program you don't need to with root permissions. A better solution would be to use a folder(which you own) within the www/ folder, change the permissions on the www folder to all everyone write access (this will have security implications) or change the group of the www/ folder to one that allows the system,root and your user to write to it and then allow rw for the group.
Post back if you need help doing one of these.

---

### Post by Paul41 on 2009-05-08
> **tarps87 said:**
> It is probably opening eclispe 3.2 because this is the one in the system path. You can try running eclipse using the full path to the launcher, but I strongly recommend that you do not run any program you don't need to with root permissions. A better solution would be to use a folder(which you own) within the www/ folder, change the permissions on the www folder to all everyone write access (this will have security implications) or change the group of the www/ folder to one that allows the system,root and your user to write to it and then allow rw for the group.
Post back if you need help doing one of these.

+1 for this.  I changed the group to the www folder added myself to the group and that works for me.

---

### Post by tarps87 on 2009-05-08
This should set it up for you.
Note: not all the steps are need but it doesn't hurt to do them.

```

sudo groupadd web
sudo usermod -a -G web root
sudo usermod -a -G web *your_username*
sudo chown root:web /var/www
sudo chmod g+rw /var/www

```

---

### Post by UK00 on 2009-05-08
Thank you! yep it worked when I changed the ownership!

---

