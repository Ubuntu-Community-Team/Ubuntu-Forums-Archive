---
title: "jaunty won't boot after update"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by Falc7 on 2009-09-25
I did an update, and edited xorg (i did this: [http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)), and now jaunty won't boot. It gets to 
kinit: no resume image, doing normal boot
Then it gives me the console log in
Then the screen goes funny, the ubuntu logo and loading bar are distorted, with inverted colours, and there are two of them. 
It freezes there.

I think (but i'm just guessing really) that i may need to restore the original xorg.conf, i booted up using the livecd and have noticed there is a xorg.conf.failsafe, how can i use that?

---

### Post by Azrael3000 on 2009-09-25
you best make a copy of your old xorg.conf by invoking
```

cd /etc/X11/
sudo cp xorg.conf xorg.conf.old
```
and then copy the failsave onto the config by
```

sudo cp xorg.conf.failsafe xorg.conf
```

an other option would be to reconfigure xorg by
```
dpkg-reconfigure xserver-xorg
```

HTH
Arno

---

### Post by Falc7 on 2009-09-25
I get this message:

ubuntu@ubuntu:/etc/X11$ sudo cp xorg.failsave xorg.conf
cp: cannot stat `xorg.failsave': No such file or directory

So i tried some other conbinations:
ubuntu@ubuntu:/etc/X11$ sudo cp xorg.failsafe xorg.conf
cp: cannot stat `xorg.failsafe': No such file or directory
ubuntu@ubuntu:/etc/X11$ sudo cp xorg.conf.failsave xorg.conf
cp: cannot stat `xorg.conf.failsave': No such file or directory

---

### Post by philinux on 2009-09-25
Reboot. Choose the recovery option. At the recover menu use the up down arrow keys and choose xfix. After it's done resume normal boot.

---

### Post by Falc7 on 2009-09-25
Just tried that and my screen went crazy when i tried to normal boot.
It got to a couple of lines past 'loading samba' then like weird waves of colour came across it.

Might i have to do a clean install?

EDIT: However when booting up the livecd, i've noticed that xorg has indeed returned to how it was before, i'm guessing it wasen't xorg that caused the problem then, perhaps it was the update?

---

### Post by Azrael3000 on 2009-09-27
> **Falc7 said:**
> noticed there is a xorg.conf.failsafe

oh I'm so sorry, I had two typos in my code.

of course you should use

```
sudo cp xorg.conf.failsafe xorg.conf
```

do you remember if it was a kernel upgrade that asked you to reboot?

---

### Post by philinux on 2009-09-27
I'm running jaunty and there is no failsafe file in /etc/X11/

---

