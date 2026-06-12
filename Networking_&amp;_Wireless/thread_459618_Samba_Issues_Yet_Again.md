---
title: "Samba Issues Yet Again"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by Monsuco on 2007-05-30
Ok, after spending months trying to get samba to stop timing out, asking for passwords, or just being beligerent, I have accomplished nothing. All the graphical tools Ubuntu has don't really set Samba up well at all (why there are no simple setup tools that just ask for the directory and if it should be writable is beyond me).

Does anyone have an smb.conf that allows for anyone to browse my shared folders with NO logging in, NO passwords, NO timeouts, and the program runs just fine. In other words, I want to share files between my Linux and Windows PC the same way I do between two windows PCs, without any server login crap getting in the way. I could really use a good smb.conf

---

### Post by KaroSHiv0n on 2007-05-30
erm..you mean sort of like system>admin>shared folders
untick read only?

works for me.

---

### Post by obrient on 2007-05-30
I don't think you will want the whole config file. Just add the following at the end of the file 
```

[TestServer]
path = /home/username/foldernam
comment = This is my Samba Share on Ubuntu
available = yes
browseable = yes
public = yes
writable = yes

```

I also know that when I had any problems I would do is simply 
   1.  sudo smbpasswd -e username
   2. Type and retype new Samba password 

Then if any problems do a ```
sudo chmod 0777
``` of the folder that you want to share. This isn't secure but it should work.

---

