---
title: "Multimedia files"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by MihailKukutanov on 2008-12-30
All of the music photos and videos that I have copied from my CD's is shown with a padlock and I can't copy delete nor move the files i have tryed to fix it prough the properties but no results. Some tips please. 
P.S. all of the files are in the standard Music Pictures and Videos folders that exist with the instalation.

---

### Post by taurus on 2008-12-30
When you copied them over from the CD, the ownership stays so root probably owns them all.  You just need to change the ownership of those files from root to your username.  

Assuming your username is mihail, you would do something like

Applications -> Accessories -> Terminal
```
sudo chown -R mihail:mihail Music
sudo chown -R mihail:mihail Videos 
sudo chown -R mihail:mihail Pictures
```

---

### Post by MihailKukutanov on 2008-12-30
I tryed the code it didn't worked, I have checked the in properties about the ownership its set to my acount.

---

### Post by taurus on 2008-12-30
Check the permissions too.

```
ls -la ~/Music
```

---

### Post by MihailKukutanov on 2008-12-30
This is what it says after  ls -la ~/Music
drwxr-xr-x  9 milo milo    4096 2008-12-28 18:26 .
drwxr-xr-x 35 milo milo    4096 2008-12-31 03:41 ..
-rwx------  1 milo milo 5186648 2008-12-24 17:47 05 Track 5.wma
dr-xr-xr-x 33 milo milo    4096 2008-12-08 18:08 Al Di Meola
 
and the padlock still stands
and sorry for buging you I'm realy new

---

### Post by taurus on 2008-12-30
```
chmod -R 755 ~/Music
ls -la ~/Music
```

---

### Post by MihailKukutanov on 2008-12-30
Finaly. Thanks for the hellp

---

