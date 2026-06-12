---
title: "Reformating XP partition"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Bruv on 2009-02-15
Is it possible to reformat and re-install XP on my PC, but leave Ubuntu intact ?
They are both living side by side happily right now, but XP has got a few problems and its not worth the effort to sort out, a re-install would clear up anything.

---

### Post by golusweet on 2009-02-15
Yea,but you would not able to boot ubuntu.

Just use Live cd,and re-install grub.


Type these commands in terminal

sudo grub

find /boot/grub/stage1

(Use the output from this command in the next command)

root (hd0,1)

setup (hd0)

quit

---

### Post by Bruv on 2009-02-15
Sorry just to get it straight, Re-installing XP would only damage grub, but not the Ubuntu installation.
So once XP has reformatted and re-installed, using the live CD to boot into Ubuntu, gives me the option of re-installing grub ?

Have I got that correct ?
I don't want to get it wrong at this stage.

---

