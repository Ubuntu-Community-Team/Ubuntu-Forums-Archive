---
title: "Network access permission in windows"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by servalsoft on 2008-09-15
help pleeeease

I have installed samba on my ubuntu box, and used it to create a share folder (through the wizard). now i can access the XP's share folders from Ubu, and in XP I can only view the computer and the share but when I try to access it I keep on getting access denied and that I dont have the permission to access the file. 

ps: the share folder is an external HDD, and when I turn it on it goes to folder /media/myhdd. 
can any1 please help

---

### Post by Iowan on 2008-09-15
Is your Windows user the same name as your Ubuntu user? More specifically, have you built a Samba user/password for the "Windows" user (via smbpasswd - or whatever it's new equivalent is called)?

---

### Post by servalsoft on 2008-09-16
> **Iowan said:**
> Is your Windows user the same name as your Ubuntu user? More specifically, have you built a Samba user/password for the "Windows" user (via smbpasswd - or whatever it's new equivalent is called)?
Thanks for your reply

On the samba prog, there is and option to add users to use samba share, and I added those (it was just a tick).
Im logged in as "ubuntu". I have added some other users, but since ive installed "super ubuntu" on the machine, when I add new users some menu does not appear i.e: synaptic package mgr, add/remove prog....
so now I just use the default "ubuntu" user. Ive change the password of course. I tried changing the login name to match the one on windows but it wont allow me.

How can I add my window user so that he can view the shares on the linux box???

Thanks again

---

