---
title: "windows 7 install over ubuntu?"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by nick4 on 2010-03-14
i have challenge for the ubuntu community.  i have a eee 1005hab and i have ubuntu netbook remix on the whole computer.  i have a windows 7 iso but every time i plug in my WD 250gb external hd with it mounted on it, it won't run.  what should i do?  thanks in advance

---

### Post by ndefontenay on 2010-03-14
I think it's a pretty complexe installation you have.

When you installed linux on your laptop, did you have your external HDD plugged?

If you had both plugged, I believe you would have had both options in grub and you would have been able to pick.

If it wasn't the case, I believe you have a windows boot installed on your external hard drive. As soon as you plug in that external HDD, it's detected as a bootable device by your BIOS and therefore boots straight to windows without checking on ubuntu.

If you want to access to your HDD from ubuntu without having to choose between windows and linux, I suggest you go to your BIOS and change your boot option to remove USB (or put it after your internal HDD).

Nico

---

### Post by linux_believer on 2010-03-14
Are you trying to replace Ubuntu with windows 7 or dual boot?

Did you make the USB drive bootable? You can't just run the iso image.

---

### Post by nick4 on 2010-03-14
hey i solved it. thanks for your help anyways.  i was working on it off and on for a week and getting frustrated.  i think i just needed to take a step back and then solve it.  Rock on ubuntu fourmers!:D

---

### Post by ndefontenay on 2010-03-14
Glad to hear that. Enjoy your ubuntu :)

---

