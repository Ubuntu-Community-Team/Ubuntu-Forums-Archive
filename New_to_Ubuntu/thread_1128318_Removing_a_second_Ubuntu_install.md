---
title: "Removing a second Ubuntu install"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Oded on 2009-04-17
Hello all
My original setup is dual-boot Ubuntu 8.10 and WinXP.
Lately I've installed another instance of Jaunty and would now like to remove it and restore my system to the original setup above.
I've browsed the forums to search for a method, I concluded I'd have to delete the partition and resize the original partition etc...
I've also seen talks about restoring the default windows mbr...I'm guessing that's not what I need to do.
Will grub automatically recognize I only have Ubuntu 8.10 and WinXP? if not, what would I have to do to make it so?
Thanks in advance

---

### Post by cariboo on 2009-04-17
You will probably have to restore grub, as it usually runs from the last Ubuntu version installed. to repair grub, have a look at this [thread=224351]howto[/thread].

Jim

---

### Post by Oded on 2009-04-17
> **cariboo907 said:**
> You will probably have to restore grub, as it usually runs from the last Ubuntu version installed. to repair grub, have a look at this [thread=224351]howto[/thread].

Jim

Worked a treat. thanks

---

