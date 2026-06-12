---
title: "Dosbox and Dungeon Kepper 2"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-10-06
Hi all, hope your all well.

Ok I've got an urge to play Dungeon keeper 2 and a couple of older PC
games. I've got the original CDs and i've downloaded dosbox from the
repos.....So what do I do next?

I've had a quick look at the dosbox wiki, I'm getting the gist of some
of it. But I'm still struggling.

So where do I go from here?

I have the dungeon keeper 2 cd in the drive, now should I copy the
whole cd to my home folder (will this allow me to install the game via
dosbox later?

Is there a step-by-step guide to installing games/apps thats suitable
for begginers....or numptys...he he?

Thanks in advance for any help.

---

### Post by CatKiller on 2009-10-06
Dungeon Keeper 2 (IIRC) isn't a DOS game, so it won't work in DOSBox. Use something like [Wine]("http://www.winehq.org/") instead. That game is apparently [well-supported]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3696&iTestingId=40299").

---

### Post by bigboy_pdb on 2009-10-06
Apparently Dungeon Keeper 2 works with WINE. I don't know if it can be played in DOS.

I played Dungeon Keeper 1 by installing Windows 98 which I was running using VMWare (since I couldn't get the sound working with VirtualBox). You could probably do the same thing depending on your computer's hardware. It is easier to install games that were released during the Windows 95/98 era in an older version of Windows in a virtual machine than DOSBox.

I haven't used DOSBox in a while, but this is my old .dosboxrc configuration file (it goes in the user's home directory):

```

[dos]
# Enable XMS support.
# Default is true.
# xms = true | false
# Enable EMS support.
# Default is true.
# ems = true | false
ems = false


[sblaster]
# type -- Type of sblaster to emulate:none,sb1,sb2,sbpro1,sbpro2,sb16.
# base,irq,dma,hdma -- The IO/IRQ/DMA/High DMA address of the SoundBlaster.
# mixer -- Allow the SoundBlaster mixer to modify the dosbox mixer.
# oplmode -- Type of OPL emulation: auto,cms,opl2,dualopl2,opl3.
#            On auto the mode is determined by sblaster type.
# oplrate -- Sample rate of OPL music emulation.

type=sb16
base=220
irq=7
dma=1
hdma=5
mixer=true
oplmode=auto
oplrate=22050


[autoexec]
# Lines in this section will be run at startup.
mount C ~/dosboxC
c:
SET PATH=C:\WINDOWS;
SET TEMP=C:\WINDOWS\TEMP

```

I also had a folder "dosboxC" that was located in my home folder which was my C drive in DOSBox.

You'll have to check what sound and video cards it emulates in order to figure out what sound and video drivers to install.

---

### Post by GeordieJedi on 2009-10-07
Fantastic, thank you both very much!

I'll give it a whirl and let you know, how I get on.

---

