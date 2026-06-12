---
title: "[SOLVED] how to enable share browsing in nautilus"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by julien-1993 on 2008-02-20
I have just complete a minimal ubuntu gutsy graphic installation.

what I have done is 

-install 7.10 server (without gnome)
-install xserver-xorg , gdm , gnome-core

now i would like to browse my windows network share in nautilus like i was able to do when  I was using ubuntu 7.10 Desktop,

if I go in places->network it open a blank nautilus window

in my precedent install (7.10 desktop) i would have seen a icon corresponding to my windows workgroup wich I could have browse.

I guess something is missing to enable this feature, just can't find what.
Thank you.

---

### Post by ruy_lopez on 2008-02-20
Is samba-client installed?

```
sudo apt-get install samba-client
```

I don't know if that'll help. Just a stab in the dark. You'll need it anyway to browse your windows shares.

---

### Post by julien-1993 on 2008-02-20
I have installed smbclient (dont know the difference with samba-client) and it ddnt work,
I will try samba-client and come back.

thanks for the suggestion

---

### Post by julien-1993 on 2008-02-20
julien@ubox:~$ sudo apt-get install samba-client 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba-client is a virtual package provided by:
  smbclient 3.0.26a-1ubuntu2.3
You should explicitly select one to install.
E: Package samba-client has no installation candidate
__________________________________________

so i guess more than smbclient is needed to activate this feature

---

### Post by ruy_lopez on 2008-02-20
This might help:

[http://ubuntuforums.org/showthread.php?t=662496]("http://ubuntuforums.org/showthread.php?t=662496")

---

### Post by julien-1993 on 2008-02-20
OH YEAH

Thank you my friend the solution was:

```
sudo apt-get install libgnomevfs2-extra
```
and reboot

dont even need smbclient

really appreciate your help

---

