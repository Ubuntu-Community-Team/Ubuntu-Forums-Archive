---
title: "SMB / Dreamweaver Question"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by ipubtech on 2008-04-03
Hey, I'm sorry if I have posted this in the incorrect area.  I am very new to all of this.  Anyways I am running Ubuntu 7.10 in Gnome, and my machine dual boots with vista (now you know why i switched to ubuntu)  I have dreamweaver installed on Linux through wine, now here's the problem.  I have a networked SMB folder that I can open from my linux desktop.  I can go in there, manage folders, do everything I need to.  However, when I try to add sites in that folder through dreamweaver's "manage a site"; for one i cannot find the networked folder when i hit the little browse button.  Also, when I paste the actual location of the SMB folder into the same area, I get an error that says the following:

"cant create folder: (then it lists the path of the smb folder)"

I have no idea what to do with this, and I appologize if it is cryptic, so if it is...please ask questions I will answer as well as I can.  I am tired of booting into vista JUST to use dreamweaver, so if somebody can figure this out , you will have converted one more user over to your side.  Thanks for your help in advance.

---

### Post by Eiríkr on 2008-04-03
How are you accessing your Samba share?  It would have to be mounted onto the local filesystem for Dreamweaver (or any other Wine app) to properly access it.  An example for how to mount a Samba share would be:
```
sudo mount -t cifs -o rw,username=USERNAME,password=PASSWORD,uid=UID,gid=GID //SERVER/SHARE /MOUNT/PATH
```
Replace the caps as appropriate.  The uid and gid options define who owns the share once it's mounted; replace UID with your username, and GID with your group name.  If you leave these options out, the default owner is root, which makes it hard to do anything with the mounted share.  

Cheers,

Eiríkr

---

### Post by ipubtech on 2008-04-03
Hey, thanks for your help!  Your information was very useful, between me and our admin, we were able to get it to work.  Thanks so much for your help.  I may never boot to vista again.  Thanks!

---

### Post by Eiríkr on 2008-04-03
Glad you got things working.  :D  If that does it for this thread, please mark it as SOLVED in the Thread Tools dropdown towards the top of the page -- makes it easier for folks looking for solutions.  :)

Cheers,

Eiríkr

---

