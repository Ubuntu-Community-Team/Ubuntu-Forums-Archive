---
title: "Unable to safely remove external h.d."
date: 2009-11-08
forum: New to Ubuntu
---

### Post by ortaa23 on 2009-11-08
Greetings,

I am getting this message when I tryto safely remove my Maxtor h.d.

"Unable to stop drive

Error detaching: helper exited with exit code 1: sense buffer empty.
Error STOP UNIT for /dev/sdb: Success"

This is with Ubuntu 9.10. Is there anything I can do to fix this?

Adam

---

### Post by Zoot7 on 2009-11-08
You should be able to force it to umount by running
```

sudo umount -l /dev/sdb1
```

---

### Post by ortaa23 on 2009-11-08
Hello there

Thanks for your reply. 

Unless I am typing it wrong, the command you suggest was not found.

sudo, <space>, unmount, <space>, -,1, <space>, /, dev, /, sdb1

PS Very ignorant about this sort of thing

---

### Post by Miljet on 2009-11-08
The command is umount, not uNmount. Don't ask me why. You certainly are not the first to be tripped up by this command.

---

### Post by Zoot7 on 2009-11-08
> **ortaa23 said:**
> Hello there

Thanks for your reply. 

Unless I am typing it wrong, the command you suggest was not found.

sudo, <space>, unmount, <space>, -,1, <space>, /, dev, /, sdb1

PS Very ignorant about this sort of thing

Yeah it's "umount" as opposed to "Unmount", and also that's also a "-l" as in lower case "L", not 1.

Also don't worry about being inexperienced, that's what we're here for. ;)

---

### Post by ortaa23 on 2009-11-08
OK, thanks for that. I now have a new message when I select Safely remove drive:


Unable to stop drive

This file cannot be stopped

Any ideas?

---

### Post by Bunnybugs on 2009-11-08
Well, I guess that you have some kind of programs/files in use from your harddisk, shut down all the applications that have use of your E-HDD

(Had the same trouble with an USB-Flash Drive)

---

### Post by ortaa23 on 2009-11-08
Hello

Unless there are things hiding away somewhere, then all apps are closed when I try to remove the drive.

---

### Post by Zoot7 on 2009-11-08
> **ortaa23 said:**
> OK, thanks for that. I now have a new message when I select Safely remove drive:


Unable to stop drive

This file cannot be stopped

Any ideas?
Does forcing it to unmount with umount -l work?

---

### Post by ortaa23 on 2009-11-10
Hi

The umount -l command has no effect.

---

### Post by bovender on 2009-11-15
Hi all,

I have the same problem here, it occurs quite frequently. I attach a screenshot of the error message. As far as I can tell, the drive does get unmounted even when this message is display. Just not sure if it was "safely" unmounted.

lazy

---

### Post by Zoot7 on 2009-11-15
Try right clicking it and selecting "Unmount", then do the safe removal.

It it won't let you umount you can force it to do so by running
```
sudo umount -l <hard drive>
```
and then do the safe remove.

---

