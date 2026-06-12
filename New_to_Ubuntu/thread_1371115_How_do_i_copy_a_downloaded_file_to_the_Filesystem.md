---
title: "How do i copy a downloaded file to the Filesystem?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by Sandeepkumar on 2010-01-03
I'm using ubuntu 9.10 Jaunty Jackalope with windows xp guest in virtual box 3.0.8_OSE i have downloaded the guest additions for it and to install them the virtual machine wants them to be placed in the virtualbox folder which is in Filesystem/usr/share/virtualbox . Now how do i copy the virtualbox guest additions iso file to this folder.
The iso file is in downloads folder.
Please help and thanks in advance!

---

### Post by hashimoto on 2010-01-03
The guest additions should be installed within the virtual Windows. See here:

[http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/](http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/)

---

### Post by Methuselah on 2010-01-03
Note that usually there is an option to make the virtual CD drive in Virtual Box load the .iso so that it will appear to be in the windows D drive.

In any event, to answer your original problem, my guess is that you are having permission issues since your user is not allowed to write to directories outside of /home/you.

In a terminal (Accessories->Terminal) type 
```

gksu nautilus

```
then hit enter.

This will launch the file browser in adminstrator modde then you can copy anything wherever.
Don't get carried away though. :p

---

### Post by Sandeepkumar on 2010-01-03
that helped! thanks a lot!

---

