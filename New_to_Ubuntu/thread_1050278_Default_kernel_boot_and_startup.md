---
title: "Default kernel boot and startup"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Comzee on 2009-01-25
I have an Asus EEE PC 1000. I installed Intrepid Ibex on it. There was two stipulations with the installation. I had to install a custom kernel, and a eee-control panel program.

My Ubuntu system boots the default kernel on start-up, I can press exit to choose the custom kernel, but it gets  annoying every time. How do I make my custom kernel the default one to boot into?

This is a simple one, my eee-control panel doesn't auto-start with Ubuntu. How do I make programs auto-start on boot-up?

thanks in advance for anybody's help, it is always appreciated!

---

### Post by sdennie on 2009-01-25
For the first problem, edit /boot/grub/menu.lst and change:

```

default 0 (or maybe 1)

```

To

```

default saved

```

Then change:

```

# savedefault=false

```

To:

```

# savedefault=true

```

Then run:

```

sudo update-grub

```

The next time you reboot, you will have to choose the kernel you want to use but, after that it will remember the one that was chosen every time you reboot.

---

### Post by Comzee on 2009-01-26
Thanks so much!! If anybody could also answer my "program on start-up" question that would be fantastic :D !!!

Thanks again Sdennie !!

---

### Post by sdennie on 2009-01-26
Forgot the "program on startup" part.  If the program needs to run as root, add it to /etc/rc.local.  If it runs as the user, go to System->Preferences->Session and add it there.

---

### Post by darksidedude on 2009-01-26
did you try installing "BUM" (boot up manager) Me thinks there will be a thing to select to start your control panel on boot up?

---

