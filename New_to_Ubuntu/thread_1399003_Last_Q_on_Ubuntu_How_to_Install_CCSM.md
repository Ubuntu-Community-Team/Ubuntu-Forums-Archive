---
title: "Last Q on Ubuntu: How to Install CCSM?"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Akatsuki26 on 2010-02-05
I fixed the whole thing with the flash player! Thanks a lot guys!

Now to my last problem:

I went to Software Centre and looked for Advanced Desktop Effects Settings (ccsm)

I found it, clicked on "Install", but under "Progress" it says "Waiting for other software managers to quit"!
(because of this it doesn't start downloading-and installing)

But I am not running any other software managers, only the software centre...

Can anyone help?

Thanks a lot!

Akatsuki26

---

### Post by abhishekdagr8 on 2010-02-05
Try installing it through the terminal window instead of the software center... maybe that'll help

---

### Post by lidex on 2010-02-05
Run this command in a terminal ("Applications>Accessories>Terminal"):
```
sudo apt-get install compizconfig-settings-manager python-compizconfig compiz-fusion-plugins-extra compiz-fusion-bcop compiz-fusion-plugins-main compizconfig-backend-gconf
```
It's all one line - just copy and paste.
Enter your password when prompted.

---

### Post by Akatsuki26 on 2010-02-06
This is what I get when I enter the code you told me:

"myname"@ubuntu:~$ sudo apt-get install compizconfig-settings-manager python-compizconfig compiz-fusion-plugins-extra compiz-fusion-bcop compiz-fusion-plugins-main compizconfig-backend-gconf

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

Can anyone help?

---

### Post by Flimm on 2010-02-06
> **Akatsuki26 said:**
> This is what I get when I enter the code you told me:

"myname"@ubuntu:~$ sudo apt-get install compizconfig-settings-manager python-compizconfig compiz-fusion-plugins-extra compiz-fusion-bcop compiz-fusion-plugins-main compizconfig-backend-gconf

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

Can anyone help?
Something went wrong the last time you tried to install something. To recover from the crash, type this command in a terminal:
```
sudo dpkg --configure -a
```You can then try the installation command again.

---

### Post by lidex on 2010-02-06
> **Akatsuki26 said:**
> This is what I get when I enter the code you told me:

"myname"@ubuntu:~$ sudo apt-get install compizconfig-settings-manager python-compizconfig compiz-fusion-plugins-extra compiz-fusion-bcop compiz-fusion-plugins-main compizconfig-backend-gconf

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

Can anyone help?

Probably explains your Software-Center problem ;)

---

### Post by airtonix on 2010-02-06
> **lidex said:**
> Run this command in a terminal ("Applications>Accessories>Terminal"):
```
sudo apt-get install compizconfig-settings-manager python-compizconfig compiz-fusion-plugins-extra compiz-fusion-bcop compiz-fusion-plugins-main compizconfig-backend-gconf
```
It's all one line - just copy and paste.
Enter your password when prompted.

Unless you have a good reason for installing the extra packages (other than compizconfig-settings-manager) you should not suggest that people install them...

creates nightmares on support requests when they can't remember what they installed.


start simple and then add extras if you need them.

---

