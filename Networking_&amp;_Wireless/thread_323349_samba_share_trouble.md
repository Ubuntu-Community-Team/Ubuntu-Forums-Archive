---
title: "samba share trouble"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by TekJunkie2k3 on 2006-12-21
Hi guys. I've just setup my first samba server. Everything works until i try to add new shares. I'd like to set it up so that each member of my family would have their own directory as a share that only they could access to help protect each others data. I assumed i just needed to copy the original share parameters and then just alter them to fit each user. The problem I'm having is that I am now unable to connect to them. When the extra shares are removed and i restore the original share setting everything works fine. Am I doing this right or is there another way to add shares to a samba server. thanks.

---

### Post by Rippey on 2006-12-22
have you tried webmin?

---

### Post by Iowan on 2006-12-22
The original smb.conf defines a default [homes] share with a line (may need to be un-commented)```
valid users = %S
```  That *should* create (well, maybe create is the wrong word) a share accessible only by the the user.

---

### Post by TekJunkie2k3 on 2006-12-22
I tried webmin and it really helped me setup the extra shares.  My only issue now is setting the permission for each user and the directories so that they can be read only or written to. I think i may have forgotten something when setting up the shares because i can only read directories unless i manually go in an change permissions to allow all groups and users to read/write.

---

