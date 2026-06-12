---
title: "Installing Ubuntu 10.10 inside windows after initial usb installation"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by jorgiov on 2010-12-14
Hello to everyone,

I have a Dell inspiron 600m running windows xp. Four months ago I have successfully used wubi to install ubuntu on an external USB hard drive. I would like to install ubuntu on my laptop's hard drive (c: ) as well. I am wondering if after the installation I will have three choices on the boot menu (WinXP, Ubuntu USB, and the new Ubuntu installation of the hard drive) or the new ubuntu installation will overwrite the old (USB) one. I have this question because I don't want to lose the access to the ubuntu usb installation. And another question, do you think that 8gb will be enough for the new installation inside windows?

Thanks a lot,

Jordan

---

### Post by Frogs Hair on 2010-12-14
I tried something similar on 9.10 except my Wubi installation was not on usb but on the hard drive. I was unable to boot with a live cd while Wubi was installed. I could view the contents of the disc from both Windows and Ubuntu . I encountered an auto run error and changing the boot priority in the bios had no effect. Once Wubi was removed the cd worked fine.

---

### Post by bcbc on 2010-12-14
You can't install wubi twice - regardless of where you install it. The second installation attempt will first prompt you to uninstall the existing install - and will delete everything.

You can get around this... but it involves a bit of tweaking.

Having a wubi install shouldn't interfere with booting from CD... unless somehow the bios is checking the contents of the hard drive for wubi - which seems unlikely ;)

PS... standard wubi warning - do not update packages grub-pc and grub-common while running a wubi Ubuntu install. They are known to break Wubi.

---

