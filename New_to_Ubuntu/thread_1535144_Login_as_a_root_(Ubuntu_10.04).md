---
title: "Login as a root (Ubuntu 10.04)"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by khushalb on 2010-07-20
Well guys I know I can login to the root using Terminal with sudo command. I check on the internet and theres this thing to edit gdm.conf but its not available in new version of Ubuntu.

Some recommended executing 

Sudo bash 

so I excecuted the command and added my password. what does it exactly to and is it recommended? Need help and also do we really need admin rights for the GUI.

---

### Post by da burger on 2010-07-20
I've already said this in the other thread you wrote in but I will answer the extra questions you brought up here.

You should not log in as root through gdm. It is against forum policy to teach people how to do this. It is not necessary, sudo is more than adequate.

For a single command as admin use sudo.
For a graphical command as admin use gksudo.
For a root shell use sudo -i from a normal shell.

---

### Post by Rubi1200 on 2010-07-20
Just to reiterate what da burger has just said:

Not only will sudo/gksudo do everything you need, you will also be better protected.

If you need to do something that requires root privileges, and you are not sure of what you are about to do, ask here first. There are more than enough experienced users who can offer advice that will not destroy your system.

---

### Post by snip3r8 on 2010-07-20
to login as root you have to open a terminal and enter the following:

```
sudo su
passwd
```

then enter your password.after that,when you are at the gdm login screen ,select other and then type "root" as userrame and then enter your password that you set from the "passwd" command.

---

### Post by aysiu on 2010-07-20
So it sounds as if you've been getting a root prompt using ```
sudo -i
``` If you want a graphical root file browser, you can use the command ```
gksudo nautilus
``` If you find yourself using that a lot, you can create a launcher or keyboard shortcut for the command.

---

### Post by mikewhatever on 2010-07-20
If gdm.conf is not available, how exactly would loggin as root help?

---

### Post by lisati on 2010-07-20
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
and here: [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by snip3r8 on 2010-07-20
> **mikewhatever said:**
> If gdm.conf is not available, how exactly would loggin as root help?

the title of the thread was "login as root" ,so thats what i told...i don't read much

---

### Post by Rubi1200 on 2010-07-20
> **snip3r8 said:**
> the title of the thread was "login as root" ,so thats what i told...i don't read much

Well, you should **definitely** read this then:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by Primefalcon on 2010-07-20
This will tell you how to do it...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

it'll also inform you about why you should not do it

---

