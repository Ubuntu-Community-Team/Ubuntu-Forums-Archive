---
title: "any idea how to know if cdrom tray is open or close ?"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by honeybear on 2010-11-22
eject -T can toggle but to know its status after done ?

---

### Post by HermanAB on 2010-11-22
Just run 'eject' without the -T, then you know it is open.  After that, you can use -T to close it again.

---

### Post by karthick87 on 2010-11-22
You can disable cdrom tray from opening using the following command,

```
eject -i on
```Now you cant open the cdrom tray to open it you should it enable it again,

```
eject -i off
```But i dont think there is a way to check the status for open/close cdrom tray.

---

### Post by fatality_uk on 2010-11-22
Bit more background on the eject command.

[http://manpages.ubuntu.com/manpages/maverick/en/man1/eject.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/eject.1.html)

---

