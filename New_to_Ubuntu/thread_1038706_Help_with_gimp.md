---
title: "Help with gimp"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by da protagonist on 2009-01-13
I hope this is the right place to post this, but my wife is having some trouble with gimp.  The toolbox has vanished and she cannot bring it back.  She has tried the menu command and uninstalled and reinstalled the program, but to no avail.  Any help here with my noobiness would be greatly appreciated.  Thank you

---

### Post by whoop on 2009-01-13
Open the user directory click view-->show hidden files. Then delete the .gimp directory. It could have a version number after it.
This will reset gimp to it's default configuration.

---

### Post by newbee70 on 2009-01-14
> **da protagonist said:**
> I hope this is the right place to post this, but my wife is having some trouble with gimp.  The toolbox has vanished and she cannot bring it back.  She has tried the menu command and uninstalled and reinstalled the program, but to no avail.  Any help here with my noobiness would be greatly appreciated.  Thank you

to completely uninstall gimp you should use.

```
 sudo apt-get purge gimp 
```

then do a normal install

---

