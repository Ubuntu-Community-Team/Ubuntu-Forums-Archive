---
title: "trying to edit the grub menu.lst but accsess is denied"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by azz2811 on 2009-01-18
basically what the title says i want to edit the menu.lst and i after i have finished editing it i want to save it but when i click save it say accsess denied.  How do i give my self access?  thanks

---

### Post by mjheagle8 on 2009-01-18
did you use ```
gedit
``` or ```
sudo gedit
```
the second one will give you administrator priveleges and will allow you to access it.

---

### Post by oldos2er on 2009-01-18
"sudo gedit"

 Should be "gksu gedit".

---

### Post by azz2811 on 2009-01-18
ok thanks i just went to file system/boot/grub  so yeah i did it wrong.

thanks



i just tried it now and when i put gksu gedit into the terminal it just came up with an empty text box.  am i ment to copy everything from the menu.lst and then change what i want and then save this new document as menu.lst and then put it in the grub folder?

thanks

---

### Post by 73ckn797 on 2009-01-18
> **azz2811 said:**
> ok thanks i just went to file system/boot/grub  so yeah i did it wrong.

thanks



i just tried it now and when i put gksu gedit into the terminal it just came up with an empty text box.  am i ment to copy everything from the menu.lst and then change what i want and then save this new document as menu.lst and then put it in the grub folder?

thanks


You need to enter, in terminal:
```
gksudo gedit /boot/grub/menu.lst
```

That will allow edit and saving of the changes you make.

---

### Post by azz2811 on 2009-01-18
ok thanks alot

---

### Post by mjheagle8 on 2009-01-18
you're welcome. good luck!

---

### Post by b0b138 on 2009-01-19
You can also install nautilus-gksu  ```
sudo apt-get install nautilus-gksu
``` This will enable you to right click and "open as administrator"

---

### Post by azz2811 on 2009-01-19
> **b0b138 said:**
> You can also install nautilus-gksu  ```
sudo apt-get install nautilus-gksu
``` This will enable you to right click and "open as administrator"

Thanks!  ill do that now that will be a very big help

> **mjheagle8 said:**
> you're welcome. good luck!

worked awesome thanks again :)

---

