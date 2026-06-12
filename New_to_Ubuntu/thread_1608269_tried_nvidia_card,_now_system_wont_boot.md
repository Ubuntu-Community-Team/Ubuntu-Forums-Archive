---
title: "tried nvidia card, now system wont boot"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by killabyte79 on 2010-10-28
Hi guys im newbie to linux, i just installed ubuntu in my PC running also XP. i attempted to install a nvidia riva tnt 2 video card and see what happens buy ubuntu system now crashes at startup and no way to make it run well. always crashes.

what can i do? i want to avoid reinstalling again

best 

killabyte79

---

### Post by sandyd on 2010-10-28
> **killabyte79 said:**
> Hi guys im newbie to linux, i just installed ubuntu in my PC running also XP. i attempted to install a nvidia riva tnt 2 video card and see what happens buy ubuntu system now crashes at startup and no way to make it run well. always crashes.

what can i do? i want to avoid reinstalling again

best 

killabyte79

Mash the shift/esc key right after you press the power button of your computer.

Press 'e' when the menu appears, and add
```

nomodeset
```
to the end of the line that has "kernel" in it.
make sure theirs a space.

press control+x

---

### Post by killabyte79 on 2010-10-28
Thanks dude, definitely Linux is a new road but i will walk it. what happened to the system and what im i supposing to do?  when os get recovered will then startup ok after a reboot? or will be something permanent screwed inside?

regards

Rodrigo

---

### Post by sandyd on 2010-10-28
> **killabyte79 said:**
> Thanks dude, definitely Linux is a new road but i will walk it. what happened to the system and what im i supposing to do?  when os get recovered will then startup ok after a reboot? or will be something permanent screwed inside?

regards

Rodrigo

nothing permanant.
its just what happens when the built in (neavou) nvidia screws up.
Nouveau is still quite new, so theirs some cards that it doesn't support.

yet.

If the fix works,
```

gksudo gedit /etc/default/grub

```
replace the entire line starting with```

GRUB_CMDLINE_LINUX_DEFAULT
```
with
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

```
save.
```

sudo update-grub
```

---

### Post by killabyte79 on 2010-10-29
Hi dude, it didnt work out. when i select "e" there is a small box with some commands but "kernel" is nowhere belive me i made throughful research, so i removed quiet and splash and wrote nomodeset as ive seen in other forumbs about the nvidia issue. anyway the system crashes at startup.

as i just installed ubuntu on wednesday i decided to reinstall, but, what a surprise it didnt work with the USB stick. it seems like the system is looking for a floppy drive:

/init: line 7 : cant open /dev/sr0:no medium found. but in the bios it is well set up to detect USB, it is the same setting for when i installed ubuntu from the USB stick few days ago.

i guess it has to do with the grub, but im a newbie and i really need help.

it all started when i installed a nvidia riva tnt2 video card and then booted in ubuntu. the nvidia use to work well in my dual screen Win XP.

please help

regards

Rodrigo

---

### Post by colin.p on 2010-10-29
if I'm not mistaken, the TNT card has a different (maybe obsolete?) driver. Soon after nvidia came out with that card, they bought out 3dFX Voodoo and incorporated their drivers into the current nvidia driver, maybe 10+ years ago?
I am pretty sure that the current nvidia driver, win or linux won't work, at least for that Riva TNT card. You will have to find a driver specifically for a Riva TNT video card.

---

