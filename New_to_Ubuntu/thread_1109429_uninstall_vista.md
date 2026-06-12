---
title: "uninstall vista"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-03-28
what is the easiest way to uninstall vista and reclaim the space for linux without installing ubuntu.

---

### Post by asmoore82 on 2009-03-28
You can boot up an Ubuntu live CD and use the GParted partition editor off of that.

Alt+F2 and
```
gksudo gparted
```

---

### Post by Sef on 2009-03-28
For clarity:

1) You are currently dual booting Ubuntu and Vista.

2) You wish to delete your Vista paritition without reinstalling Linux.

3) Are 1 and 2 correct?

---

### Post by trinidadflores on 2009-03-28
> **asmoore82 said:**
> You can boot up an Ubuntu live CD and use the GParted partition editor off of that.

Alt+F2 and
```
gksudo gparted
```

should this be done from the live cd? and what about the grub? will that still be needed?

---

### Post by trinidadflores on 2009-03-28
> **Sef said:**
> For clarity:

1) You are currently dual booting Ubuntu and Vista.

2) You wish to delete your Vista paritition without reinstalling Linux.

3) Are 1 and 2 correct?

yes thats right.

---

### Post by Delta28 on 2009-03-28
You need to put Ubuntu on first then remove vista if you don't use his way but I wouldn't recommend taking off vista even though linux is better vista is a good program for a backup incase linux boot up fails or crashes

---

### Post by trinidadflores on 2009-03-28
> **Delta28 said:**
> You need to put Ubuntu on first then remove vista if you don't use his way but I wouldn't recommend taking off vista even though linux is better vista is a good program for a backup incase linux boot up fails or crashes
i have a way of doing my backups so vista is not needed.

---

### Post by Paqman on 2009-03-28
> **trinidadflores said:**
> should this be done from the live cd? and what about the grub? will that still be needed?

You can do it from either the LiveCD or from Ubuntu. If the latter, you might need to unmount the Vista partition. Gparted won't let you modify or delete a partition that's mounted.

If you want to expand your Ubuntu partition to use the new space then, yes, you'll need to use the LiveCD. If you have a Vista recovery partition then don't delete that. You might want Vista back in the future.

You'll still need Grub, but you can just remove the Vista entry in /boot/grub/menu.lst

---

### Post by trinidadflores on 2009-03-28
> **Paqman said:**
> You can do it from either the LiveCD or from Ubuntu. If the latter, you might need to unmount the Vista partition. Gparted won't let you modify or delete a partition that's mounted.

If you want to expand your Ubuntu partition to use the new space then, yes, you'll need to use the LiveCD. If you have a Vista recovery partition then don't delete that. You might want Vista back in the future.

You'll still need Grub, but you can just remove the Vista entry in /boot/grub/menu.lst
I have my anytime upgrade disk from microsux to reinstall winblows if needed.  but currently i have winblows--xp flavor installed in  virtual for everything that vista was needed for.

next step is for microsuxs to go bye bye for good!!

---

### Post by Paqman on 2009-03-28
> **trinidadflores said:**
> I have my anytime upgrade disk from microsux to reinstall winblows if needed.

I think that will only work if you already have Vista installed. I'd never heard of an "Anytime upgrade disk", but if it's [this](http://www.microsoft.com/windows/windows-vista/get/anytime-upgrade-overview.aspx) then you'll definitely not be able to use it to install Vista.

PS: *How* expensive!?!?!!

---

### Post by ranch hand on 2009-03-28
I wouldn't worry about Vista.  You have XP.  Vista is a down grade.

Do not wipe Vista from installed Ubuntu if it is on the same drive, use the CD.  If Vista is on another drive you should be able to use gparted from your Ubuntu installation.  Just reformat the partitions to ext2 or 3.

---

### Post by Paqman on 2009-03-29
> **ranch hand said:**
> I wouldn't worry about Vista.  You have XP.  Vista is a down grade.


Yeah, but if you've paid for a licence why remove your ability to use it? Besides, Vista vs XP is largely a matter of opinion. XP might be better for one user, and Vista for another.

---

### Post by carml on 2009-03-29
I want to know that user:lolflag: I have got Vista and I know what I speaking about. Apart from jokes Vista or Xp can be used to do any things you can't do wit Linux,amongst play with any of most recent games or use any software you strictly need to,which don't have an equal under Linux. :)

---

### Post by ranch hand on 2009-03-29
I will take your word for the game playing abilities of MS products.  I do not now nor have ever been a game player.

If that last sentence did not bring a smirk to you face - it is the oath that was required by Sen. McCarthys committee when investigating comunists in the 50s if you replace game player with "a member of the comunist party" and do with "am".

---

### Post by carml on 2009-03-31
I heard some voices about the poorness of CAD software in this forums,I don't remember in which thread,this is an example of what I meant,apart from games world that at the moment is quite thought for M$.

---

### Post by ranch hand on 2009-03-31
Most people do not use CAD.

I actually am somewhat interested in it and looked into is years ago for designing Blacksmithing jobs.  Cost is too high to pay for itself.  There are some things that really work better on paper.

If you are unfamiliar with the technology look into it.  It is really interesting and you can use it even in power failures if you have oil lamps.  The user interface is very interactive and personal too.

---

