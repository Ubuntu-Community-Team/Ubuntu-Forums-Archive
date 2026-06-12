---
title: "Cant save changes to smb.conf"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by brianmulc on 2007-12-22
I am setting up my first Linux machine and wish to share with windows network.  I've made cahnges to smb.conf but am told that I do not have rights to save file.
When I look at properties for file, it shows owner as root and read/write options are grayed out.  I am logged in with admin priveledges.  I'm obviously missing something here.:confused:

---

### Post by NeoLithium on 2007-12-22
smb.conf requires superuser privilages.  If you're using gedit, just open up a terminal window and type ```
gksu gedit /etc/smb.conf
```  It'll ask you for your password, enter that. Edit away and save :)

---

### Post by brianmulc on 2007-12-22
Thanks Neo.   That worked for me.

What is the difference between sudo and gksu that made the difference?

---

### Post by movrshakr on 2007-12-22
> **brianmulc said:**
> Thanks Neo.   That worked for me.

What is the difference between sudo and gksu that made the difference?

I've wondered the same thing.  Hope there is an answer.

---

