---
title: "dual boot mode help"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Weapondrift on 2009-11-09
I was trying to setup my dual boot today but I keep getting errors. I open the terminal and type the following 

```
sudo gedit/boot/grub/menu.lst
```  when this happens I am prompted in my terminal for my password I type the password that I use for login and I get an error saying ```
command not recognized
```. What am I doing wrong?

---

### Post by dragonboss on 2009-11-09
Youre not leaving a space between the gedit command and the path

---

### Post by egalvan on 2009-11-09
> **Weapondrift said:**
> 
I keep getting errors. I open the terminal and type the following 

```
sudo gedit/boot/grub/menu.lst
``` 

 What am I doing wrong?

 A space is needed between **gedit** and the file name **/boot/grub/menu.lst**


thus
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Weapondrift on 2009-11-09
> **dragonboss said:**
> Youre not leaving a space between the gedit command and the path

so it should look like this? 
```
sudo gedit /boot/grub/menu.lst
``` correct?

---

### Post by sandyd on 2009-11-09
> **Weapondrift said:**
> so it should look like this? 
```
sudo gedit /boot/grub/menu.lst
``` correct?
yes.

p.s. are you using ubuntu 9.10 or 9.04? (i assume you did a fresh install, but if this was an upgrade, ignore me.)
9.10 has a new boot system called grub2 and the dual boot settings are NOT configured there.
see here for more info [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

p.s. wonder why their putting a beta version of grub into karmic.....

---

### Post by Weapondrift on 2009-11-09
> **carlee said:**
> yes.

p.s. are you using ubuntu 9.10 or 9.04? (i assume you did a fresh install, but if this was an upgrade, ignore me.)
9.10 has a new boot system called grub2 and the dual boot settings are NOT configured there.
see here for more info [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

p.s. wonder why their putting a beta version of grub into karmic.....

Im using the newest version of Ubuntu...I think its 9.10/

---

### Post by kansasnoob on 2009-11-09
Post the output of the following commands (copy-n-paste please):

```
grub-install -v
```

That will display the version of grub.

```
sudo fdisk -l
``` (That's a lower case L.)

Will show us the basic drive and partition structure.

---

### Post by LewRockwell on 2009-11-09
please use **gksudo** for GUI and **sudo** for command line

.

---

### Post by egalvan on 2009-11-09
> **LewRockwell said:**
> please use **gksudo** for GUI and **sudo** for command line

.

Oops, I totally missed this...

Yes, use 
**gksudo gedt**

---

### Post by winotree on 2009-11-09
> p.s. wonder why their putting a beta version of grub into karmic..... I was reading on the forum last night [don't remember where] and someone asked the same question -- seems that GRUB Legacy is a beta too, even after all these years [version 0.97].

---

### Post by kansasnoob on 2009-11-09
> **carlee said:**
> yes.

p.s. are you using ubuntu 9.10 or 9.04? (i assume you did a fresh install, but if this was an upgrade, ignore me.)
9.10 has a new boot system called grub2 and the dual boot settings are NOT configured there.
see here for more info [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

**p.s. wonder why their putting a beta version of grub into karmic**.....

I recently gave Sidux a spin and I believe it uses the same version, so I think that's the newest available.

---

