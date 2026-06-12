---
title: "Accidentally overwrited /etc/modprobe.d/options"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by DurandalArauz on 2009-03-07
hey

So  i was trying to make my SAA7134 based tv card in Ubuntu 8.10 and i fond some stuff that should work, but since i was doing something wrong Gedit didnt have the priviledges to add the code that i needed to put on it even tho i was adding sudo to the command...so as a total noob i decided to "cp" the missing code into it thinking that it would *add* the stuff into the file not overwrite it.

So the terminal overwrote it....is there anyway to restore it? I didn't back it up.....

The card doesn't work on a Windows XP virtual machine, so if it just doesn't work imm going to have to format the hard drive (my micro$oft XP cds like to feel dominant so i need to format before installing it) and put ubuntu on a vritual machine, which i don't really want to do :|

Help me plz ;-;

(right now i don't see any effects of overwriting it, but i guess it at least deletes any chance on getting the card to work, and i heard that the card works better on linux, overall the card is not good hardware and the 100% indispensable software it needs to run in windows SUCKS)

---

### Post by taurus on 2009-03-07
If you are using gedit, there is a backup copy with the same name with a ~ at the end.

```
ls -la /etc/modprobe.d
```

---

### Post by DurandalArauz on 2009-03-07
Found it lol 

Thanks dude

---

