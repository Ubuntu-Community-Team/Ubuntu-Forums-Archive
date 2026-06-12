---
title: "Sharing a folder on the network"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by johnny9794 on 2006-11-23
--------------------------------------------------------------------------------

Ok I have just now started to use sharing a folder on my network "SMB Network" for my linux box. "I use shared files and folders off my XP boxs all the time and have no problem"

This is my first time using sharing a folder off my Ubuntu, Edgy box so i may access my Ubuntu, Edgy box shared folders and files from my other Windows, XP box.

When I try to access the shared folder that is on my Edgy box from my XP box I get prompt with a username and password login screen, I have tried my Edgy box login name and password, tried my network username and password, none of it works .

Is there a usernamer and password i must set for file sharing on Ubuntu? 

If my typing is bad, I am sorry i have been up for 20 hours or so.

Could someone help me out :)?
Here is a screenshot of the login prompt

---

### Post by Biker on 2006-11-23
Do you have added a samba user? Add the same Ubuntu user/password to the Samba environment (is network sharing)

sudo smbpasswd username (press enter and type the password)

---

### Post by Terpsicore on 2006-11-23
> **Biker said:**
> Do you have added a samba user? Add the same Ubuntu user/password to the Samba environment (is network sharing)

sudo smbpasswd username (press enter and type the password)

Thanx a lot for this help.

I had exactly the same problem and following your indication everything is fine now... :)

---

