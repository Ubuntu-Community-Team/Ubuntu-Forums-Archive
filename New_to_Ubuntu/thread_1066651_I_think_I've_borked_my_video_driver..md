---
title: "I think I've borked my video driver."
date: 2009-02-11
forum: New to Ubuntu
---

### Post by oopsie on 2009-02-11
Okay, been playing about with Ubuntu for a bit now. And I've been trying to get various things working under Wine with varying degrees of success.

Anyhoo, in search of better FPS and such, I've been doing various things to my drivers. Installing/uninstalling and twiddling with settings.

It was going great. I got HL-1, HL-2 and WoW working pretty well.

But, I've done one thing too far it seems, and now HL-1 runs at about 1fps and WoW and HL-2 even less than that. Plus, Ubuntu semi-crashes sometimes when I try to run things. Bumping me to the Ubuntu login screen. I also got an error thing on booting Ubuntu a few times, about some driver configuration thing, but that doesn't come up now.

I've read a few guides and done some searching. But, fixing the mess I've got myself in is beyond me =S

Anyone know what I can do?

---

### Post by Temposs on 2009-02-11
Have you tried reinstalling your video driver and reconfiguring xserver?

To reconfigure, do this:

```
sudo dpkg-reconfigure xserver-xorg
```

It might undo your tweaks, but it could also restore your stability. This command will save a backup of your current xorg.conf.

Here's an article on doing this:
[http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server](http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server)

---

### Post by oopsie on 2009-02-11
> **Temposs said:**
> Have you tried reinstalling your video driver and reconfiguring xserver?

To reconfigure, do this:

```
sudo dpkg-reconfigure xserver-xorg
```

It might undo your tweaks, but it could also restore your stability. This command will save a backup of your current xorg.conf.

Here's an article on doing this:
[http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server](http://wiki.freespire.org/index.php/Reconfigure_a_Broken_Xorg_Server)

Thank you. Although I still have terrible FPS after I've done those things. I had already tried installing my video driver. No luck


Okay, I installed and uninstalled the FGLRX driver, and now everything seems to be working okay. Thanks everyone

---

