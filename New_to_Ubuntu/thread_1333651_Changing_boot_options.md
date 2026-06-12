---
title: "Changing boot options"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Amory_Blaine on 2009-11-21
New to ubuntu.  Just got it up and running last night...

When I boot up it shows 5 options.

Ubuntu
Ubuntu Safe mode
memory test
another memory test
windows 7

I would like to change the first option to Windows 7 and only have one option for ubuntu.  

I don't need to be told exactly how to do it, but at least if someone has link to information that would be awesome.

Thanks in advance!  I am such a newb!

---

### Post by cjv8888 on 2009-11-21
> **Amory_Blaine said:**
> New to ubuntu.  Just got it up and running last night...

When I boot up it shows 5 options.

Ubuntu
Ubuntu Safe mode
memory test
another memory test
windows 7

I would like to change the first option to Windows 7 and only have one option for ubuntu.  

I don't need to be told exactly how to do it, but at least if someone has link to information that would be awesome.

Thanks in advance!  I am such a newb!

To do what you want, you can edit the booting menu.
Change the default number from 0 to boot first to Windows 7
then comment out the other options so you will not see them with a # in front.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Amory_Blaine on 2009-11-21
:D  thanks so much for the information.

At work right now, but I am going to try it when I get home!  

Much appreciated.

---

