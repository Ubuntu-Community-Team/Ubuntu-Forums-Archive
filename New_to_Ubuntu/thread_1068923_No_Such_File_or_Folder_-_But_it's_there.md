---
title: "No Such File or Folder - But it's there?"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-13
Why does ubuntu report ....

"NO SUCH FILE OR FOLDER"  when it's clearly right there?



thx

---

### Post by avtolle on 2009-02-13
Taking a wild guess here, the file or folder is showing on the desktop, and you are trying to install something/access it from the terminal. If this is so, do```
cd Desktop
```which changes the directory you are in to your desktop, then```
ls
```and see if the file is reflected there. If it is, then proceed with what you are trying to do.

Linux is case sensitive; desktop is different from Desktop.

---

### Post by mistypotato on 2009-02-13
Hi, thx.

I'm working in Terminal.

I'm in /var/www$

when I do an ls I can see two folders listed

I cannot cd into those folders as it insists they are not found....but I can see them.

---

### Post by williane on 2009-02-13
Remember ubuntu is case sensitive, so if youre trying to navigate to myFolder by typing 'cd myfolder' it wont work. Maybe copy and paste from your terminal so we can see exactly what is going on?

---

### Post by oldos2er on 2009-02-13
> **mistypotato said:**
> I'm in /var/www$

when I do an ls I can see two folders listed

I cannot cd into those folders as it insists they are not found....but I can see them.

 Please post the output of
```
ls /var/www
```

---

