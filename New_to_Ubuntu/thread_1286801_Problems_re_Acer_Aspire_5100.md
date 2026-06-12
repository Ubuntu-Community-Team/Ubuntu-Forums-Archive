---
title: "Problems re: Acer Aspire 5100"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by webwiller on 2009-10-09
Hi all & ty for your kind help!
I convinced a friend of mine to try out Ubuntu and switch from bloody Windows starting out with a dual boot, less scary.
He owns an Acer Aspire 5100.
I first tried to repartition with GParted but the notebook would not read the cd. I tried with Ubuntu live cd and it worked beatifully, so I repartitioned the hdd as I always did.
I obviously decided to go for the win install first, to avoid troubles with recovering Grub but all my winXP install cd's didn't want to work.
I finally thought of an hardware fault but I found out cd were read from Ubuntu's live cd. Dvd burner is ok than.
I lately asked my friend if he had specific recovery cd's from Acer, in case it was a driver's problem. He gave me the WinXP Acer install cd but it also does not work.
I managed to install Ubuntu easily but I cant manage to install WinXP.
Is there any known issue, or something I can check-out for? I'm stuck with this...tx again!:confused:

---

### Post by webwiller on 2009-10-09
Nobody has a clue or it's about the fact that you might think this is a Windows issue??!! Well, if this is the case, it is not!
It might be a Bios issue, it might be an hardware issue, it might be anything, but not a windows issue.
Also considering the fact that I tried re-formatting the whole hdd, but not GParted by itself, neigher GParted from inside ubuntu's live cd wont boot at startup.
Now that Ubuntu's installed, it will boot only the installed version, nothing else will boot.

---

### Post by LewRockwell on 2009-10-09
```
sudo fdisk -l
```

---

### Post by k3lt01 on 2009-10-09
My father has that model but his had Vista not XP. Acer didn't supply him with a Recovery/Install CD instead they pre-installed a recovery partition. Problem is that stopped working which is why dad asked me about Ubuntu. Since installing Ubuntu he has had no problems and never talks about Windows.

About the "Windows Issue" I am afraid it still may be. Windows sent through hardware driver updates that stopped the hdd from booting properly and it even affected the DVD drive. It was an ATA driver or something like that I can't remember as it was about 12 months ago.

---

### Post by PrePenguin on 2009-10-09
Make sure you go into the bios and choose to boot from the CD drive before the Hard drive in the boot list and windows should install.. You can change it back after words if you would like..

---

### Post by PrePenguin on 2009-10-09
> **k3lt01 said:**
> My father has that model but his had Vista not XP. Acer didn't supply him with a Recovery/Install CD instead they pre-installed a recovery partition. Problem is that stopped working which is why dad asked me about Ubuntu. Since installing Ubuntu he has had no problems and never talks about Windows.
  

The no CD Acer windows partition you can access by hitting F11 on boot up and if you get into windows you can burn a restore CD .. Its just another way for them to save money..

---

### Post by roger_1960 on 2009-10-09
Hi

These particular laptops suffer from motherboard faults (design/manufacturer problem)  I have one which works still but has all 3 USB ports completely useless.  If it has a deformed (melted) small area of casing about 35mm to the left of the touchpad and just below the windows key, it is probably suffering from this.  In my case it has only affected USB function.......

---

### Post by LewRockwell on 2009-10-09
> **PrePenguin said:**
> Make sure you go into the bios and choose to boot from the CD drive before the Hard drive in the boot list and windows should install.. You can change it back after words if you would like..

Ab-so-lutely LOVE the avatar!

Silence is Golden, Duct Tape is Silver!

ROTFL!

.

---

### Post by LewRockwell on 2009-10-09
> **PrePenguin said:**
> The no CD Acer windows partition you can access by hitting F11 on boot up and if you get into windows you can burn a restore CD .. Its just another way for them to save money..

Also, it should be noted that the recovery/restore disk(s) creation function doesn't last forever

Supposedly windows will continue to offer the option to burn these each time you boot until you do...and then you only get to do it once...

However, it has come to our attention that many people did not accomplish this task and are now left with no recovery/restore disks

Which means if your hard drive goes bad or your on-drive restore function/partition gets corrupted somehow...you are screwed unless you made back-ups/clones via something like Clonezilla

.

---

### Post by k3lt01 on 2009-10-10
> **PrePenguin said:**
> The no CD Acer windows partition you can access by hitting F11 on boot up and if you get into windows you can burn a restore CD .. Its just another way for them to save money..Windows has been gone for about 12 months. I was unable to access the restore partition and the Windows partition failed to boot any time Windows attempted, it didn't even have to succeed, to install the hdd driver update. Acer themselves were of no help so Ubuntu was a very attractive option. We have not looked back since.

---

### Post by webwiller on 2009-10-10
I understand your points, and I almost agree with all of you: ubuntu beats windows 100times! 
But as you can understand I believe, a newby feels always more secure with his win partition. At the beginning it happens you cant figure out something that you desperatly need instantly and, if you have your win, you can just switch to win and do your staff and calm down. Later you'll be back to linux for sure :-)

Said that...

I did many hardware check-ups and I do believe it is NOT an hardware fault.
I found out that in BIOS menu it seems like there's no option for internal cd drive but only for usb cd drive. I was thinking of a Bios update but I'm scared of messing up everything worse than now.

This is how the Bios menu looks like:

1: IDE 0: Hitachi HTS54574735434256AT00-(PM
2: IDE 1: HL-DL-ST DVDRAM GSA-T10N-(P
3: SATA:
4: PCI BEV: REALTEK BOOT AGENT
5: USB HDD:
6: USB CDROM:
7: USB FDD
8: USB KEY:

I tried moving up #2 to first position, but I dont understand if that is the dvd burner as it's written :HL-DL-ST DVDRAM bla..bla (as above).
I also tried moving #6 to first position, but I believe it's an eventual external cd drive, right?

Any suggestions?

---

### Post by k3lt01 on 2009-10-10
> **webwiller said:**
> This is how the Bios menu looks like:

1: IDE 0: Hitachi HTS54574735434256AT00-(PM
2: IDE 1: HL-DL-ST DVDRAM GSA-T10N-(P
3: SATA:
4: PCI BEV: REALTEK BOOT AGENT
5: USB HDD:
6: USB CDROM:
7: USB FDD
8: USB KEY:

I tried moving up #2 to first position, but I dont understand if that is the dvd burner as it's written :HL-DL-ST DVDRAM bla..bla (as above).
I also tried moving #6 to first position, but I believe it's an eventual external cd drive, right?

Any suggestions?IDE 0: Hitachi should be your DVD drive. Doing a Google search brings up nothing but this thread.
IDE 1: does bring up a few things such as it is an LG manufactured drive. Does this machine have 2 dvd drives?
SATA is your hdd.

How are you trying to move IDE1: to the top? Are you selecting-highlighting and then pressing F6 to move it up?

---

### Post by webwiller on 2009-10-12
I really dont know how I worked it out. But I did.
What I did was move up choice # "2: IDE 1: HL-DL-ST DVDRAM GSA-T10N-(P" to position #1 by pressing F6 and than F10 to save and quit bios.
One of the many tries it just worked.
Who knows...
ty all anyway ;)

---

