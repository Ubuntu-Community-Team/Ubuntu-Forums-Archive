---
title: "Keyring Manager does not recreate default keyring"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by pvravi on 2007-06-25
Hi, 

I deleted the default keyring since I had (unwittingly) set the password to my WPA pass phrase. Now, Keyring manager never asks me for a default password anymore. Not when I run the keyring manager, or when I configure a wireless network. It does not save my wireless network info, either. How do I keyring manager to ask me for a password and save my wireless connection info?

I upgraded to NetworkManager 0.65 (I wanted LEAP). Is that the cause? I dont think so, since at first NetworkManager 0.65 stored its leap password in Keyring Mgr!

Help, please! I posted in one of the other related threads, but no response. Hence the double post.

---

### Post by pvravi on 2007-06-25
Deleted the default keyring, created a new keyring with the name default, and a new password. It finally asked if I wanted to allow NetworkMgr to access the Keyring. Appears to work OK for now.

---

### Post by alexv305 on 2007-07-01
Pardon my curiosity, but what exactly does the keyring manager do?

---

### Post by komputes on 2008-02-21
Keeps the passwords for your wireless network (and has the possibility to do more if other apps use it), but by default on Ubuntu, I think it just covers the Wireless passwords. 

@pvravi I'm not sure creating a keyring and naming it default is the same as the default keyring. I think that gnome-keyring-manager may see the "login" key as the default keyring, which it is in my case.

There are many problems I see with gnome keyring manager.

Resetting the default password: 

Let's say you forget the keyring password there should be a way to reset it. Up to now the best way I have to do so is:

**NOTE THIS WILL DELETE YOUR KEYRING AND ALL PASSWORDS WITHIN IT**

```
rm ~/.gnome2/keyrings/default.keyring
```

If you do have the password and would like to change it to something new, there is no way to do so within gnome keyring manager. You have to download seahorse to do that.

Otherwise if you want to remove the keyring manager causing you to type the password in every single time you want to connect to something, you will need to take out a huge chunk of your operating system. I have tried removing they keyring manager and was told that the following packages would have to be removed as well:

```
gnome-keyring-manager ubuntu-desktop
```

If I want to remove gnome keyring, the list of packages grows, as you can see it includes a big chunk of the OS:

```
 xchat-gnome-common libmono-security1.0-cil libpth20 python-pexpect
  libmono-sharpzip0.84-cil cdrecord libmono-system-web1.0-cil bittornado
  python-chm libmono-cairo2.0-cil tango-icon-theme-common tango-icon-theme
  kdebase-kio-plugins python-qt3 dar boo libdar64-4 libkonq4
  tango-icon-theme-extras python-sip4 libtaglib2.0-cil icedax libmono1.0-cil
  libmono-data-tds1.0-cil libmono-system-data1.0-cil kdesktop libxine1-gnome
  rdiff-backup python-wxversion libavahi1.0-cil libgpgme11 pmount
  python-wxgtk2.6 python-xlib miro-data librsync1 libboost-python1.34.1
```

---

