---
title: "what this command does?"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by iam_newhere on 2009-05-08
what does sudo dpkg-reconfigure-xserver-xorg do to your system??

i'm running ubuntu 8.04.2.

---

### Post by taurus on 2009-05-08
It would give you an error message since there is no such a command.  I believe you meant

```
sudo dpkg-reconfigure xserver-xorg
```
That would let you reconfigure your X server.

---

### Post by ibuclaw on 2009-05-08
dpkg-reconfigure allows you to reconfigure installed packages.

In the context of which you are using it, it will restore the xorg.conf file back to it's failsafe default in the event that the login screen/GUI fails to start and you are forced into a command prompt or "low resolution" mode.

This file is located here:
```
/etc/X11/xorg.conf
```

The command you are asking about is:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Alternately, you can boot into 'Recovery Mode' and select the "Fix X" option.

Regards
Iain

---

### Post by iam_newhere on 2009-05-08
> **taurus said:**
> It would give you an error message since there is no such a command.  I believe you meant

```
sudo dpkg-reconfigure xserver-xorg
```
That would let you reconfigure your X server.

yes, i wanted that. a little typo there.

i did that command to fix something. the resolution was off and stuff when i changed something in screens and graphics under other in the applications menu.

it asked me questions. i didnt really read them, except for the first one. 
i just went in and pressed OK.

do u think something might happen wrong after that?

---

### Post by Kareeser on 2009-05-08
No. The command itself tries to autodetect your hardware and rolls back xorg.conf to a generic version, which works with as many types of graphics card combos as possible.

---

### Post by iam_newhere on 2009-05-08
> **Kareeser said:**
> No. The command itself tries to autodetect your hardware and rolls back xorg.conf to a generic version, which works with as many types of graphics card combos as possible.

thank you! i think i wont have to worry about it anymore.

cuz ive reinstalled ubuntu and xubuntu so many times after tweaking and stuff.

this forums is a life savior :popcorn:

---

