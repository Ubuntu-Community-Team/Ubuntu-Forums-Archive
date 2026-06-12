---
title: "Wget download from ftp?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by djb6 on 2008-12-21
So i have a file I would like to download from an FTP site.  Now I've discovered that using the command WGET in the terminal speeds up my downloads for whatever reason.  The problem is, I need to log into the ftp site using a specific username and password, but when I use wget, it tries to log me in using annoymous, which won't work.  Is there a way to log into the ftp with the proper name, but use the wget command to download?

---

### Post by ercferret18 on 2008-12-21
look at the man page... I think it's like user_name:... and password:... but i'm not sure, it will say in wget's man page

---

### Post by djb6 on 2008-12-21
What do you mean by "main page"?

---

### Post by ercferret18 on 2008-12-21
> **djb6 said:**
> What do you mean by "main page"?
actually that says "man page", and you access it with the command "man wget". but i figured it out, just give wget the options --user=(user) and --password=(password) and that is how you log in.

---

### Post by djb6 on 2008-12-21
sweet!  Thanks

---

### Post by ercferret18 on 2008-12-21
no problem

---

### Post by zazuge on 2009-02-09
or you can do this
[noparse]wget "ftp://user@pass:url:port"[/noparse]

Edit bodhi.zazen: Fixed smiles in code.

---

### Post by zazuge on 2009-02-09
or you can do this
wget "ftp://user@pass:url:port"

---

