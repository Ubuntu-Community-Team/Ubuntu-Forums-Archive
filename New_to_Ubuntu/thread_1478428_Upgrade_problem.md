---
title: "Upgrade problem"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by bobmcquaid on 2010-05-09
Yesterday I upgraded Ubuntu to 10.04, after the upgrade I am unable to dual boot to XP pro. I had Ubuntu as default and when I choose XP from the boot list, I am ignored. Please help.

Bob

---

### Post by Teber on 2010-05-09
the issue is known. it happened to me after a fresh install of lucid. the search function should produce some answer for you. i would seem to be a matter of overwritten bootloader on the windows side.

i myself decided to use linux only from now on.

---

### Post by romeug on 2010-05-09
> **bobmcquaid said:**
> Yesterday I upgraded Ubuntu to 10.04, after the upgrade I am unable to dual boot to XP pro. I had Ubuntu as default and when I choose XP from the boot list, I am ignored. Please help.

Bob
first try:
Try **sudo update-grub**
there are numerous solutions you will find with a search, this would be an excellent and simple start...

---

### Post by flyfishingphil on 2010-05-09
> **bobmcquaid said:**
> Yesterday I upgraded Ubuntu to 10.04, after the upgrade I am unable to dual boot to XP pro. I had Ubuntu as default and when I choose XP from the boot list, I am ignored. Please help.

Bob
I have Vista, and I don't know if the dual boot choices look the same, but I found that I needed to go to Vista Recovery selection instead of Vista Loader to open up Vista properly after upgrading to 10.04.

Hope this is a choice that helps.

---

