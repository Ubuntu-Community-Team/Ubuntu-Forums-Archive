---
title: "Ubuntu installation update and question"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by uv2008 on 2008-12-28
Hello,

A few days ago I asked here a question regarding Ubuntu graphical installation: when choosing the option "use largest continuous free space" (or something like that) then it seems that Ubuntu is going to be installed on 100% of the hard drive, rather than on the specific space that I shrank for that purpose.
After reading a few posts I decided to risk my Vista and try that "continuous free space" option. So for your information: it worked perfectly fine, and indeed installed Ubuntu only on the specific space, while keeping Vista intact (well, saying that, there was a quirk of my Norton antivirus being ruined after the Ubuntu installation, but you guys will probably say that it's for the best :-)).
So it seems to me that there is indeed a graphical bug in this intstallation option.

Now for my question: when I start up my computer, Ubuntu is currently the first (default) option, while Vista is the last one. I think that the program is called Grub 1.5.  was wondering if any of you knows how to make Vista the default one.

Thanks for all your help!

---

### Post by Michael.Godawski on 2008-12-28
hey,

just follow this guide and ask if you hit the wall:

[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

---

### Post by billgoldberg on 2008-12-28
> **uv2008 said:**
> 
So it seems to me that there is indeed a graphical bug in this installation option.


This doesn't make much sense to me.

I guess you mean that you think it's Ubuntu's fault that Norton is acting up. Well it's not, it's Norton's fault.

--

in a terminal copy/paste this:

sudo gedit /boot/grub/menu.lst

Then you'll see something like this:

> 
title  Arch Linux
root   (hd0,0)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/93bd5de8-c684-4c49-bf5e-429a2367f$
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,0)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/93bd5de8-c684-4c49-bf5e-429a2367f$
initrd /boot/kernel26-fallback.img

# (2) Windows
title Windows 7
root (hd0,1)
makeactive
chainloader +1

I'm guessing that moving windows up before Ubuntu (or arch in this case) will do the trick.

So it would be like this:


> # (2) Windows
title Windows 7
root (hd0,1)
makeactive
chainloader +1

title  Arch Linux
root   (hd0,0)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/93bd5de8-c684-4c49-bf5e-429a2367f$
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,0)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/93bd5de8-c684-4c49-bf5e-429a2367f$
initrd /boot/kernel26-fallback.img





---

### Post by Elfy on 2008-12-28
I would actually suggest moving the whole windows stanza above the automagic line - then when there are kernel updates the file won't need editing again.

Slightly more involved - but easily achieved - if you want to do so post your menu list

```
cat /boot/grub/menu.lst
```

---

