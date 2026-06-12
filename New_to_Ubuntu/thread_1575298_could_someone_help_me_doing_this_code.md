---
title: "could someone help me doing this code?"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-09-15
im doing a tutorial to get my wireless internet working on my ASUS Eee Pc 1005p. I can not for the love of me get this to work. here is the bit that's stumped me.

Extract your Download file and cd into the resulting directory.
tar -xjvf name-download-filedestination-directory
cd destination-directory+name-download-file 

i have extracted the tar.bz2 file in my downloads section and ive tried this, tar -xjvf compat-wireless-2.6.tar.bz2-downloads-rachel  and that hasn't worked, could someone fix this for me?

---

### Post by TeoBigusGeekus on 2010-09-15
```
tar -xjvf compat-wireless-2.6.tar.bz2 ~/Downloads/rachel
```

---

### Post by Rave Gloves on 2010-09-15
> **TeoBigusGeekus said:**
> ```
tar -xjvf compat-wireless-2.6.tar.bz2 ~/Downloads/rachel
```

i moved the file to the desktop so i got 

```
rachel@rachel-laptop:~$ tar -xjvf compat-wireless-2.6.tar.bz2 ~/Desktop/rachel
tar: compat-wireless-2.6.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /home/rachel/Desktop/rachel: Not found in archive
tar: Exiting with failure status due to previous errors
```

---

### Post by nothingspecial on 2010-09-15
Hi Rachel
```

tar -xjvf ~/Desktop/compat-wireless-2.6.tar.bz2
cd ~/Desktop/compat-wireless-2.6
```That should do the trick :D

Edit: You say you have extracted the file already and moved it to your desktop

If the file on your desktop ends with .tar.bz2 then you need both those commands, if it`s just called compat-wireless-2.6 then just the second one will do

---

