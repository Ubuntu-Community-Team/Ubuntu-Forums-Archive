---
title: "cant install or remove programs"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by Malik on 2009-07-11
> malik@malik-desktop:~$ sudo apt-get remove  moblock-nfq
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

I got that after I thought moblock was the problem but I got this from trying to install ktorrent

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by DirtDawg on 2009-07-11
So, did you try the 'sudo dpkg --configure -a' command?

---

### Post by lisati on 2009-07-11
Do what it says: open up a terminal (on the Applications->Accesories menu) and type in ```
sudo dpkg --configure -a
```
When asked, type in your password (which won't show)

---

### Post by Malik on 2009-07-11
I see I get the blockcontrol configuration screen thing is I cant freaking press ok So the screen stays in that place.

---

### Post by QIII on 2009-07-11
Can you run anything at all in the terminal when you open it fresh?

If you can, try

sudo blockcontrol stop

---

### Post by Malik on 2009-07-11
horrible thread. It was so simple. Im so sorry for wasting y'alls time. UGH.

---

### Post by QIII on 2009-07-11
How was it horrible?

Did you get it to work?  Did it help?  This is exactly what the forum is for.

Before you shut down, while you have blockcontrol turned off, remove it.

---

### Post by Malik on 2009-07-11
> **QIII said:**
> How was it horrible?

Did you get it to work?  Did it help?  This is exactly what the forum is for.

Before you shut down, while you have blockcontrol turned off, remove it.
yea pidgin doesnt work now when moblock is on. I actually need to uninstal it. Do you know how I go about that? Thanks,

---

### Post by QIII on 2009-07-11
Try Synaptic.

I'm not entirely sure, but the terminal should go something like this:

```
sudo apt-get remove moblock blockcontrol
```

---

### Post by Malik on 2009-07-11
> **QIII said:**
> Try Synaptic.

I'm not entirely sure, but the terminal should go something like this:

```
sudo apt-get remove moblock blockcontrol
```
Totally worked. Thanks for all the help dude.

---

### Post by jre on 2009-07-13
This might help you: [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

Especially for the install problem:
[https://help.ubuntu.com/community/MoBlock#I tried to install MoBlock but I'm stuck on a screen with a Moblock warning](https://help.ubuntu.com/community/MoBlock#I tried to install MoBlock but I'm stuck on a screen with a Moblock warning)

And for pidgin:
[https://help.ubuntu.com/community/MoBlock#Some%20applications%20cannot%20connect%20to%20the%20internet%20any%20more!](https://help.ubuntu.com/community/MoBlock#Some%20applications%20cannot%20connect%20to%20the%20internet%20any%20more!)!

---

