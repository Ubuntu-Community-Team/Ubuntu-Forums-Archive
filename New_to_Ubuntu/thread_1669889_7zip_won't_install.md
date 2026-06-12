---
title: "7zip won't install"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by adver on 2011-01-18
I can't install 7zip from the Ubuntu Software Center.  It says "Requires installation of untrusted packages" when I hit install, and then does nothing.  I tried sudo apt-get install 7zip also.  Am I missing the authentication key in my software sources?  If so what is it?

---

### Post by Kirboosy on 2011-01-18
Why exactly are you install 7zip? Ubuntu out of the box can extract most file types. 
 
Just trying to save you some hassle.
 
Right click on the compressed file and hit "extract here"
 
Try this
 
In a terminal type the following
```
sudo apt-get install p7zip-full
```

---

### Post by Rytron on 2011-01-18
sudo apt-get install p7zip-full

---

### Post by Rytron on 2011-01-18
```
sudo apt-get install p7zip p7zip-full p7zip-rar
```

---

### Post by Kirboosy on 2011-01-18
Double post....

---

### Post by adver on 2011-01-18
I can't install 7zip from the Ubuntu Software Center.  It says "Requires installation of untrusted packages" when I hit install, and then does nothing.  I tried sudo apt-get install 7zip also.  Am I missing the authentication key in my software sources?  If so what is it?

---

### Post by Frogs Hair on 2011-01-18
Try ```
sudo apt-get update
``` and try installing again

---

### Post by adeee on 2011-01-18
sudo apt-get install p7zip-full

---

