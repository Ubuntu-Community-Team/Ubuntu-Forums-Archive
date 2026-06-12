---
title: "VirtualBox and Samba"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by JustinAlf on 2007-04-24
Whenever I try and acces my Linux computer from the WIndows machine, it tells me MSHome is not accesible.  How do I fix my Samba to allow it to accesable?
I've already edited the samba file to allow for writeing and viewing, although not sure if I did it properly.  I need this to work in order to access music files to throw on a minidisc.  So please someone help.

---

### Post by scxtt on 2007-04-24
make sure you do: **sudo smbpasswd -a <username>** on the ububtu box ...

i.e. **sudo smbpasswd -a JustinAlf** ... then a "map network drive" should work for any smb share you've setup on ubuntu ...

---

### Post by JustinAlf on 2007-04-25
I tried that previous to this post and it didn't work.  I tried it again after you suggested it and now everything works as it should.  I had two restarts in between, so i'm wondering if a reset of the samba server was necessary?  Anyways, thanks for the help!

---

