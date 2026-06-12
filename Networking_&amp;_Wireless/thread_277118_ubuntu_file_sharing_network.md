---
title: "ubuntu file sharing network"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by rich79 on 2006-10-14
Hello smart people! 

 I have win XP on one p.c and on the other ubuntu. 

I have 2 problems:

1. if I'm trying to contact the ubuntu files from the win XP, it is asking me for pass. I want 2 disable this option. I don't want it 2 ask me at all. 

2. if I'm trying 2 find the XP from the ubuntu p.c. I click on the workgroup and get empty window! How come?? 

thank you in advance,
Ohad

---

### Post by Kateikyoushi on 2006-10-14
Read [this]("https://help.ubuntu.com/community/SettingUpSamba") ubuntu samba guide.

You have to edit your /etc/samba/smb.conf file

Etting editing these two lines in the folder's section what you wish to share, would solve it.

Guest ok = Yes
Browseable = Yes

---

