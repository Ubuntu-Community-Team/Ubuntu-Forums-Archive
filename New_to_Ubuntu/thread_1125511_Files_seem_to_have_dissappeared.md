---
title: "Files seem to have dissappeared"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by mistypotato on 2009-04-14
Hi,

I'm sure there must be a simple explanation for this.  A few moments ago I created a new Folder under Documents.  I then gave that folder a unique name.  I then copied about 20 VERY important files into that folder.

Now, no matter what I cannot find the folder OR any of the files.

Can someone please help me here?  I've never had this happen and it's confusing.

Thanks

---

### Post by Penguin Guy on 2009-04-14
Please run these commands and post back the output:
```
ls -h ~/Documents
ls -h ~/.local/share/Trash/files
sudo ls -h /lost+found
```
Please also tell us the name of the folder and/or files.

---

### Post by mistypotato on 2009-04-14
Hi,

It's not hidden (unfortunately)

**sudo ls -h /lost+found** does not return anything at all

---

### Post by mistypotato on 2009-04-14
This is the first time this has happened,

---

### Post by Penguin Guy on 2009-04-14
Have you checked your trash?
```
ls -h ~/.local/share/Trash/files
```

---

### Post by mistypotato on 2009-04-14
Thanks Penguin.

As usual Ubuntu +1    Noob user 0


They weren't gone....the folder name I gave the folder didn't take for some reason and the folder renamed itself to "untitled folder".

I was sweating there for a moment though.

Thanks for the assist :KS:KS:KS:KS:KS

---

### Post by Penguin Guy on 2009-04-14
*slaps head* :lolflag:

---

