---
title: "Can't access password protected  shares with Nautilus."
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by ubumubumu on 2008-07-08
When trying to browse the shared resources of a computer with Windows XP Home edition, which is protected by ```
net user guest <password>
``` (described [here]("http://netsecurity.about.com/cs/windowsxp/a/aa042204.htm")) Nautilus does not ask for a password and after that does not show the shared folders.
When using Gnome-Commander it asks for the password and shows the folder list, etc and everything is just fine.
The main problem is that because I can't logon from Nautilus I can't used the shared printer of the XP machine.
Can I force Nautilus to logon with a supplied password?

Ubuntu 8.04

---

### Post by bigken on 2008-07-08
try installing samba 

open a terminal 

sudo apt-get install samba 

sudo smbpasswd -a yourname
sudo smbpasswd -e yourname 

you may need to reboot

---

### Post by ubumubumu on 2008-07-08
Samba is installed and working.
The question is that I want login on a particular PC ith a password and Nautilus doe not seem to understand that a password is requred.
I do not understand how 
```
sudo smbpasswd -a yourname
sudo smbpasswd -e yourname
```
will help me in this case?
Besides it sais [I]Failed to modify password entry for user guest
[/I].

---

### Post by ubumubumu on 2008-07-11
up

---

### Post by bigken on 2008-07-11
why dont you share the printer from your account on the windows pc

---

### Post by ubumubumu on 2008-07-14
The printer is shared on the Windows PC, but I cannot access it through Nautilus from the Ubuntu PC. The other Windows PC's in the network have no problem accessing the printer.
I guess it's some kind of bug in Nautilus, I shall probably inform its developers :(

---

