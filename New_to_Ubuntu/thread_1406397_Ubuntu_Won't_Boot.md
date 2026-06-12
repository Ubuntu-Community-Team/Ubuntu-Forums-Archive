---
title: "Ubuntu Won't Boot"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by LegendarySandwich on 2010-02-13
Hi guys. Well, I was being an idiot and following a guide on upgrading Alsa because of audio crackling in games, but I don't think I got it to work...and, I think I also upgraded GRUB and installed the package-maintainer's version. And now the Ubuntu logo that appears when Ubuntu is booting up stays there forever; it doesn't ever reach the login screen.. What do I do?

---

### Post by Julita on 2010-02-14
Most likely the problem with kernel that wouldn't load. Need your specs, though. Nonetheless, you can add parameters at the end of the kernel line when grub is loading. You have to select the line with kernel, press "e" and add to the end, for example, ro quiet splash nomodeset (at least I was able to boot with it), or noacpi...

---

