---
title: "Samba: a Xubuntu's shared folder"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by ccafiero on 2007-07-24
Hello!

I'm using Xubuntu 7.04 to make new life to my Acer Travelmate 521T (Pentium III).

All works fine but now i'd like to share a Xubuntu folder to Xp home.

This folder will be writeable, browseable etc... (in few words open to all the network users).

I tryed to configure samba (using the guides around the net) and this is my smb.conf

*****
[global]
workgroup = MSHOME
security = SHARE

[public]
comment = Pubblicamente Accessibile
path = /home/public
public = yes
read only = no
writeable = yes
guest ok = yes
browseable = yes
*****

My Xp Home (with COMODO Firewall set as "permit to all" to access to your pc) see the Xubuntu pc on the net but i'm not able to open the folder "You don't have the permissions" says XP.

How can i do?

Some one could help me please?
Many thanks indeed.

---

### Post by dmizer on 2007-07-24
on your xubuntu computer, do the following:
```
sudo smbpasswd -L -a [COLOR="Red"]your_xubuntu_username[/COLOR]
sudo smbpasswd -L -e [COLOR="Red"]your_xubuntu_username[/COLOR]
```
but replace "your_xubuntu_username" with your actual xubuntu user name.

restart samba ... or reboot your xubuntu machine, and retry your share from windows.

---

### Post by ccafiero on 2007-07-24
Hi dmizer!

Thank you for your help.

I try your suggest but nothing changes! :(

sudo smbpasswd -L -a andrea (is my xubuntu useranme)
sudo smbpasswd -L -e andrea (is my xubuntu useranme)

Win Xp reply always the same message: "You may not have the permissions".

I've tryed even with firewall on or off.

I don't know how i can try more!

Bye!

---

### Post by ccafiero on 2007-07-24
Ok, 
renaming host name in network setting with a shorter name (12 letters) all works (before the name was longer).

Bye!

---

