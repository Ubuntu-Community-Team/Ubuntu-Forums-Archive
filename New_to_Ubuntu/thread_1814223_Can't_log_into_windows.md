---
title: "Can't log into windows"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by husky12 on 2011-07-29
I installed Linux Ubuntu 11.04 a few weeks back, and now upon logging in, the purple screen that I'm supposed to log into either ubuntu or windows has only the ubuntu options.

---

### Post by pierreyy on 2011-07-29
i checked out the problem myself... what happens is that the computer boots up( bios there and everything, the system is a dual boot), when the purple screen comes up, it only shows ubuntu selections and the memory test thing... when booted in ubuntu we can access the windows files and all, even the partition is visible. the laptop is a dell vostro. any suggestions?

---

### Post by ajgreeny on 2011-07-29
If this is a proper dual boot with separate partitions for windows and ubuntu, from ubuntu run sudo update-grub in terminal and see if windows comes back into your grub menu.  If that does not help, click on the Boot-info-script in my signature and follow the instructions to copy back the RESULTS.txt file back here in code tags (the # in toolbar at top of reply entry box)

If you used wubi to install I'm afraid I have no idea what you need to do, however, have a look at the wubi megathread link in my signature.

---

### Post by pierreyy on 2011-07-29
> **ajgreeny said:**
> If this is a proper dual boot with separate partitions for windows and ubuntu, from ubuntu run sudo update-grub in terminal and see if windows comes back into your grub menu.  If that does not help, click on the Boot-info-script in my signature and follow the instructions to copy back the RESULTS.txt file back here in code tags (the # in toolbar at top of reply entry box)

If you used wubi to install I'm afraid I have no idea what you need to do, however, have a look at the wubi megathread link in my signature.


ubuntu was installed with a separate partition from a live cd not through wubi...thanks alot... hope it works.

---

### Post by pierreyy on 2011-08-13
( hey, sorry for being this late to reply)sudo update-grub did not work... ill check the link in your signature... thanks

---

### Post by amjjawad on 2011-08-13
> **pierreyy said:**
> ( hey, sorry for being this late to reply)sudo update-grub did not work... ill check the link in your signature... thanks

How many Hard Drives do you have?

As already suggested, please:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


When posting the result here, PLEASE wrap up the text with "CODE" tags or highlight the text and click on "#".

---

