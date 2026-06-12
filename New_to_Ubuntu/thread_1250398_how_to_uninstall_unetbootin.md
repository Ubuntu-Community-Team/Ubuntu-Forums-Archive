---
title: "how to uninstall unetbootin"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by jbutzu on 2009-08-26
Hi.  I reecently downloaded unetbootin from sourceforge and now need to uninstall it. (When the computer boots on start up i still see the option to run it along with my dual boot OS's.)  Any idea how to get rid of it?

Thanks.
John

---

### Post by LewRockwell on 2009-08-26
if you're referencing it being listed in the grub bootloader menu

then you'll want to edit the /boot/grub/menu.lst file to remove it

.

---

### Post by colau on 2009-08-31
> **jbutzu said:**
> Hi.  I reecently downloaded unetbootin from sourceforge and now need to uninstall it. (When the computer boots on start up i still see the option to run it along with my dual boot OS's.)  Any idea how to get rid of it?

Thanks.
John
How did you install unetbootin?

---

### Post by jbutzu on 2009-08-31
> **colau said:**
> How did you install unetbootin?

Simply by running the downloaded exe file using windows. :)

---

### Post by colau on 2009-08-31
> **jbutzu said:**
> Simply by running the downloaded exe file using windows. :)
Why do you want to uninstall unetbootin?

---

### Post by jbutzu on 2009-08-31
becuase it shows on computer start up... very annoying.

---

### Post by colau on 2009-08-31
> **jbutzu said:**
> becuase it shows on computer start up... very annoying.
Can you post the lists in details (it shows before booting)?

---

### Post by thiebaude on 2009-08-31
Just, gksudo gedit /boot/grub/lst and then scroll down and find the entry for unetbootin and delete it.

---

### Post by colau on 2009-08-31
```

sudo gedit /boot/grub/menu.lst&

```

---

