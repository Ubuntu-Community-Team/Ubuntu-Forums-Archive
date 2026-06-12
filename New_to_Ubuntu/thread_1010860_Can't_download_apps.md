---
title: "Can't download apps"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by bobelix on 2008-12-14
I tried to download Guitar Tux using add/remove and it hung so I rebooted. Now when I try to download any application, I get a message telling me to manually input 'dpkg --configure -a'. I tried doing this on Terminal but got a message saying I needed to be a superuser.
HELP!!!

---

### Post by ibizatunes on 2008-12-14
hello
this is quite a easy fix
go to application > accessories > terminal

```
sudo dpkg --configure -a
```

that will finish off installing the application you may want to run this command after (up to you)

```
sudo apt-get update && sudo apt-get upgrade
```

To become super user you type sudo
that gives you root permissions

---

### Post by Michael.Godawski on 2008-12-14
Try with sudo as mentioned above.

You can also try this command:
```

sudo apt-get install -f
```

---

### Post by Bölvaður on 2008-12-14
lets first try to see if you can download tuxguitar from the terminal

```
sudo apt-get install tuxguitar
```

**sudo** is put at front for super user rights, unlimited rights to do _anything_
**apt-get** is a program for installing programs and maintaining updates for them.[B]
install[/B] means that you are telling **apt-get** that you are going to install some application
**tuxguitar** is the name of that application

please try that let us know what happence.
copy the error messages to here if you get any

---

