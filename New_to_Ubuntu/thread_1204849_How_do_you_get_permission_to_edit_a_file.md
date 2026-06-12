---
title: "How do you get permission to edit a file"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by richie1913 on 2009-07-05
Hi,I am trying to edit the file usb_modeswitch.conf but everytime I try to save the modified file I get permission denied,how do you get the permission needed to do this.Thanks

---

### Post by Paqman on 2009-07-05
There's a few ways.

You can launch your text editor as root. Hit Alt-F2 and type:
```

gksu gedit /name/of/file

```

Or you can install the nautilus-gksu package and from then on you can just right click and "open as administrator".

Or you can open it in a terminal with:
```

sudo nano /name/of/file

```

---

### Post by drs305 on 2009-07-05
Since that is a system file, only someone with administrative privileges is allowed to alter the file. That is why you, as a normal user, cannot save any changes.

To edit the file, open it with *root* privileges. You will be asked to provide a your password before the app opens:
```

gksudo gedit /path.to.file/usb_modeswitch.conf 

```

---

### Post by richie1913 on 2009-07-05
Thanks guys now I can try the rest of the Instructions to get my usb dongle working

---

