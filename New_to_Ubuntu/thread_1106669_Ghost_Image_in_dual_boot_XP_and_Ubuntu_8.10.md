---
title: "Ghost Image in dual boot XP and Ubuntu 8.10"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by annie22 on 2009-03-25
I've installed Ubuntu 8.10 using Wubi into XP,until I'm confident to move permanently to Ubuntu however long that may take.
I have been backing up C(XP)with Norton's Ghost v.14 and I'm wondering whether this would include everything(both OS's) or whether I need to separately "ghost" 8.10 with one of the alternative versions available for Linux?
Everything is running really well so I'm loathe to re install,plus all the downloads etc.to test.I'd rather seek advice from those who are experienced than mess with what "ain't broke".
Another question I have is how can I save all the updates and programs best?-I mean saving to avoid downloading the updates and chosen programs again for future reintallation?
Thankyou in advance,Annie

---

### Post by LTFC2020 on 2009-03-26
I`m not sure if Norton stuff will run on Linux
My general experience is that windows programs will not work on Linux
If as you say it "ain`t broke" then I would leave well alone
As far as I can remember backing up ubuntu is a different process (but would have to do a bit of searching to be sure)
Why not wubi it for a while and if you like ubuntu then dual boot
Use the live cd from the ubuntu website and partition the harddrive how you want, its very straight forward and then you can decide on whether you want windows or linux on starting the computer (plus ubuntu will probabily be quicker)
Hope that helps a bit

---

### Post by annie227 on 2009-07-08
Thankyou so much-I know this is in the wrong place (forum)but I've moved on having wubi'd it long enough to take the plunge.
My 9.04 arrived in the mail today-wasn't that confident my iso was ok but turns out it was,still,being a "newbie" I feel more confident with an authentic disk and having been a painter who loves photography I d'loaded 9.04 studio but that's on the burner(back i.e.) for the mo.
Been reading posts in the forum and have decided to take the plunge and attempt install on my secondary 500g sata,though not entirely sure of my motives.
I'm still fumbling and would like to take the plunge and look for an actual class somewhere with a live teacher-took me a year to go from totally com-illiterate to formatting,photoshop etc.,conquering this strange new medium(as well as I can)on my own and now am so hooked it's not funny.I am determined to ditch MS,for moral/personal reasons as much as anything.
yeah,life story behind now-C:160g ide,D:500g sata,64amd dual,5600+ processor,onboard graphics and sound(terrific),22" benq-yeah,graphics card on list,and ext sata 500g.
Thinking of installing on D: but have a LOT of important data there and it seems more complex disconnecting,reconnecting,messing with bios(had some BAAD exp's there).
I keep reading wubi's not as fast/efficient as a clean partition install and I already love the speed comparatively(to xp,yuk,bog down).My xp cannot be lost at this stage due to a key I forgot to record but I WANT MY UBUNTU!
It's late and I'm raving,sorry but THANKYOU,thankyou,thankyou
oh and me and Ghost are no longer talking,chucked it

---

### Post by jimsheep on 2009-07-08
> **annie22 said:**
> I've installed Ubuntu 8.10 using Wubi into XP,until I'm confident to move permanently to Ubuntu however long that may take.
I have been backing up C(XP)with Norton's Ghost v.14 and I'm wondering whether this would include everything(both OS's) or whether I need to separately "ghost" 8.10 with one of the alternative versions available for Linux?
Everything is running really well so I'm loathe to re install,plus all the downloads etc.to test.I'd rather seek advice from those who are experienced than mess with what "ain't broke".
Another question I have is how can I save all the updates and programs best?-I mean saving to avoid downloading the updates and chosen programs again for future reintallation?
Thankyou in advance,Annie
I have had some experience with ghosting ext3 partitions.  it seems you need to ghost them seperately from other filesystems (NTFS, VFAT).  when you boot the client machine, make sure you start ghost with this switch:

```
ghost -Ial
```

that will allow ghost to start and specifically use ghost on an EXT3 filesystem.  you will then have to:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

hope that helps.

---

