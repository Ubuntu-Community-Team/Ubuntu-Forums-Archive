---
title: "trouble with login window"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by clapton on 2009-02-05
Hello people!
I install a gdm theme, but when its supposed to appear window, nothing appears.
I've got to stop gdm and do startx.
I try to change theme with login window (gdmsetup) I can't because gdm is not working.
HOw can I change gdm theme without gdmsetup?

THx!

---

### Post by khelben1979 on 2009-02-05
I don't know, but.. in order to get a working X enviroment where you don't need to quit the x server each time you boot up the machine, you can always install KDM instead. And in this case I think it might be suitable to uninstall GDM in favour of KDM.

sudo apt-get remove gdm

sudo apt-get install kdm

(I'm sure someone will give you a better answer here, but you might consider KDM if GDM is messed up so bad that even an reinstall of GDM won't give you a working login manager)

---

### Post by clapton on 2009-02-05
Thanks.
It's working solution, but I think that can be way to setup gdm without gdm setup :D

---

### Post by khelben1979 on 2009-02-05
> **clapton said:**
> Thanks.
It's working solution, but I think that can be way to setup gdm without gdm setup :D

Okay. :D

---

### Post by clapton on 2009-02-05
I install KDM(to get soundmixer and some applets that didn't start with "startx" command), but I can't setup gdm!
With startx ou KDM the error is the same when I press Adminstration>Login Windows
Appears

---

### Post by meinvateristnein on 2009-02-07
such a simple fix...... just download  a theme and goto system>>>aministration>>>>login window>>>>>> install or add new theme

my perosnal favourite is "nice looking 8.10 login" this can be found on gnome-look.com

---

