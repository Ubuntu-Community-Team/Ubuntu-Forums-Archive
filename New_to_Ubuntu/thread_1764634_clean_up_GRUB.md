---
title: "clean up GRUB?"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by RememberWhenItRained on 2011-05-22
Is there a way to clean up GRUB so that you don't see the previous versions/kernels?
I'm dual-booting and would only like to see my latest Ubuntu version, mem test, recovery mode, and win 7 loader. Is there a way to clear the two or three older kernels i have off of GRUB?

thanks

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189100&d=1302848327[/IMG] my current screen looks more cluttered than that.

---

### Post by Rubi1200 on 2011-05-22
Hi,
there are a couple of things you can do:

Clean up the menu (but remember to keep at least one older kernel for troubleshooting purposes): [http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

Set defaults, timeout, menu order etc with a GUI app: [http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Be aware, that the GUI app. has some issues with 11.04. but for most versions prior to that it should be okay.

---

### Post by Quackers on 2011-05-22
You can also delete the Memtest entries if you want to, with this command
```
sudo chmod -x /etc/grub.d/20_memtest86+
```

---

### Post by Gone fishing on 2011-05-22
Or you could uninstall the older kernels - personally I think its a good idea to keep the last kernel, but remove the older ones.

---

### Post by Paqman on 2011-05-22
> **Gone fishing said:**
> Or you could uninstall the older kernels - personally I think its a good idea to keep the last kernel, but remove the older ones.

Yep, I tend to just got into Synaptic, search for "linux-image" and filter for installed, and they all pop up.

I used to keep a spare older kernel, but I'm of the opinion these days that it's only necessary on the testing branch. I've never had a kernel update break anything on a stable release, ever, and I don't recall hearing of anyone else who did either.

---

