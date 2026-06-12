---
title: "Avant Windows Manager in VirtualBox"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by ozbolt on 2009-02-10
When I try to run AWN in Ubuntu, which is running inside VirtualBox (Guest additions installed), I get error:
Run Compiz or another compositing manager. How do I do that?

---

### Post by Peter09 on 2009-02-10
AT present virtualbox does not support 3D acceleration so I think you will not be able to run compiz. You can try, by typing the following command in  a terminal.

```
compiz &
```

---

### Post by binbash on 2009-02-10
New virtualbox has support for 3d acceleration HOWEVER i didn't try with compiz.It may run or not.And you can't use awn without compiz

---

### Post by fraser_m on 2009-02-10
Start the VirtualBox Manager, select the Ubuntu VM, click settings. In the "General" tab, select "Advanced", and switch "Enable 3D Acceleration" on. Then start up the Ubuntu VM, and run "compiz --replace". This *should* work if the 3D does.

---

### Post by howefield on 2009-02-10
May be wrong, but I think the 3D support is only good for windows guests at the moment.

---

### Post by ozbolt on 2009-02-10
[IMG]http://www.shrani.si/f/3O/ez/2y8qkp2X/screenshot.png[/IMG]

Where?

---

### Post by howefield on 2009-02-10
> 
Where?

You will find it in the Basic tab of your settings for Windows guests, but not for Linux guests.

---

### Post by vanadium on 2009-02-10
> And you can't use awn without compiz
Yes, you can if you enable compositing for metacity.

---

