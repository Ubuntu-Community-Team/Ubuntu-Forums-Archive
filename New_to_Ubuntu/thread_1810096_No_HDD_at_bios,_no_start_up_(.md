---
title: "No HDD at bios, no start up :("
date: 2011-07-22
forum: New to Ubuntu
---

### Post by Sithrin on 2011-07-22
HELP!!
I recently discoverd Ubuntu linux and think it's amazing.

now my computer goes immediatly to BIOS, starts blieping and there I see @ information tap-->HDD MODEL NAME: None

I have bought an acer aspire one A0A150 in apprx 2008, 1.6 GHZ Intel Atom.

WHY???!!? this is very bad! everything thats on it....A 160GB i mean sjeez is it lost?

Thank u if u can help or just simply know what happend, let me know please

Vincent

---

### Post by spiky001 on 2011-07-22
It might be worth taking the hard drive out and refitting just incase it got dislogged

---

### Post by mcduck on 2011-07-22
Sounds like a broken hard drive, which isn't much of a surprise for a 2008 Aspire One with a normal hard drive. Those were never designed to fit a normal hard drive but a small SSD instead, and the way the hard drives were squeezed in as afterthought to allow selling the machines with Windows caused plenty of hard drive problems. 

The drive is located right next to right speaker, without anything to protect it from the vibration the speaker creates at louder volumes so the drive's heads tend to hit the disc surface if you happen to play a wrong song at a bit higher volume.

On the other hand that would just create plenty of bad sectors on the drive, which wouldn't stop it from showing in BIOS. But perhaps the vibrations have just loosened the cables on the drive so opening the machine and checking the connections might help (I would definitely recommend checking the drive's SMART status for bad sectors if you get it working again.)

---

### Post by sadaruwan12 on 2011-07-22
This seems to be a loosening problem due to vibration try putting it back in to the hdd slot but with acer any thing could happen so hope for the best.

---

### Post by Sithrin on 2011-07-22
are you guys serious? open it up replugging the hdd... any thing i should keep in mind while trying this dangerous endavour?

BTW i did do a bad sector smart scan with ubuntu, it was awesome but showed like 482 failed sectors and a lot of quasi ones but ubuntu was the one finding them and designating them as unusable.

i got it with linux but got a xp running through a usb bootable version. it ran for 2 years until i put on ubuntu because it got so incredibly slow with xp.

anyway i blame the xp f%#*ers.

**thanks guys and btw is there any chance of recovering files from the HDD if my loyal aspire one died??**

ps. i'm carefully considering some new machine :)

Vincent

---

### Post by LemursDontExist on 2011-07-22
> **Sithrin said:**
> are you guys serious? open it up replugging the hdd... any thing i should keep in mind while trying this dangerous endavour?

BTW i did do a bad sector smart scan with ubuntu, it was awesome but showed like 482 failed sectors and a lot of quasi ones but ubuntu was the one finding them and designating them as unusable.

i got it with linux but got a xp running through a usb bootable version. it ran for 2 years until i put on ubuntu because it got so incredibly slow with xp.

anyway i blame the xp f%#*ers.

**thanks guys and btw is there any chance of recovering files from the HDD if my loyal aspire one died??**

ps. i'm carefully considering some new machine :)

Vincent

If your hard drive is dead - which sounds pretty likely - putting it in the freezer for a couple hours can sometimes restore it to working order (at least long enough to back up your data, sometimes longer).  Some [instructions]("http://lifehacker.com/5515337/save-a-failed-hard-drive-in-your-freezer-redux").  I had a friend do this with a broken hard drive, and it's still working a few months later.

---

### Post by mcduck on 2011-07-23
> **Sithrin said:**
> are you guys serious? open it up replugging the hdd... any thing i should keep in mind while trying this dangerous endavour?

BTW i did do a bad sector smart scan with ubuntu, it was awesome but showed like 482 failed sectors and a lot of quasi ones but ubuntu was the one finding them and designating them as unusable.

i got it with linux but got a xp running through a usb bootable version. it ran for 2 years until i put on ubuntu because it got so incredibly slow with xp.

anyway i blame the xp f%#*ers.

**thanks guys and btw is there any chance of recovering files from the HDD if my loyal aspire one died??**

ps. i'm carefully considering some new machine :)

Vincent

The bad sectors, and XP getting incredibly slow are symptoms of the issue I described. One the disc starst getting bad sectors, XP detects that there's something wrong with it and drops the hard drive from DMA mode to PIO mode. Which makes everything incredibly slow.

Lucky for you, I've been able to get Acer to replace the drives in three of those machines, regardless of if they had any guarantee left or not. All I had to do was describe the problem, and they immediately agreed to replace the drives without cost. They clearly know about the problem. It might of course depend on what ind of consumer right legislation exist where you live (here manufacturer is always responsible of manufacturing defects like this, regardless of if there's any guarantee or not or if it's already expired)

(The problem is even described in the Aspire One Wikipedia page, by the way. :D)

---

### Post by Sithrin on 2011-07-25
Ok so some wizzkid opened it took out the hdd put in a new and its working again.... the hard drive is completely f*#k#d,

I&#314;l try the freezing idee, thanks you all :):popcorn:

---

