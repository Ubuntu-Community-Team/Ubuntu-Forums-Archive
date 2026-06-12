---
title: "shutdown doesn't power-off"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by s1wood on 2011-01-28
I've installed lubuntu on my old P3 desktop and when I shutdown it halts the system but then stops with the logo and dots showing on the monitor and the lights still on on the front of the computer.  All the answers I can find for this involve shutting down using the terminal but I want to be able to pass this computer on to a complete novice, so everything needs to work by GUI.
I have had this with some of the other systems I have tried out on this computer, but not with all.

Any suggestions?

Susan

---

### Post by SteveDee on 2011-01-29
> **s1wood said:**
> ...I have had this with some of the other systems I have tried out on this computer, but not with all...
Susan

There may be a clue here, which OS can power-down & which cannot?

---

### Post by supererki on 2011-01-29
Do you see any errors on dmesg ?

Remove quiet and splash from /grub/menu.lst and shut the computer down :

sudo shutdown -h now

Do you see any errors then ?

---

### Post by SteveDee on 2011-01-29
> **supererki said:**
> ...Remove quiet and splash from /grub/menu.lst ...

Lubuntu 10.10 does not have a /boot/grub/menu.lst file as it uses Grub2.

---

### Post by s1wood on 2011-02-01
I don't remember exactly which systems I've been trying (I've been doing a lot of playing) but I think  PCLinux Zen Mini was OK but I had the  problem with PC Linux LDE light. Puppy 5.1 is OK. 

Susan

---

### Post by heron7 on 2011-02-01
yep , i think you've been hacked , had ... :lolflag:

 Rather it's probably set to go in hybridization mode ,than switching off completely ... i'm sure i saw it somewhere in the config. something something

---

### Post by s1wood on 2011-02-03
I've decided to go for Ubuntu 10.10 instead - for various reasons.
 It's still not turning off completely but I've got so many people wanting it in spite of its many limitations that  I think the new owner can just get used to pressing the button! 
If anyone has an answer I would still be interested in case I come across this again (I have been offered another old computer to play with).

Thanks for advice.

Susan

---

### Post by SteveDee on 2011-02-04
One thing you could try is to modify your /etc/default/grub file.

Adding "acpi_osi=Linux" sometimes fixes power related issues (fan control, shutdown & so on), Although other Linux operating systems that you have tried seem to be OK.

Edit the grub file and try adding:-
```

GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""

```

Or edit your existing line from (say):-
```

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

```

...to...
```

GRUB_CMLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

```

You may find other examples by searching the net for "acpi_osi=Linux"

---

### Post by -kleve on 2011-02-16
GREAT !!
GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""
Thats the trick on my old acer aspire 1680 ( and , I believe , many other )
thx

---

