---
title: "Bios: Problem booting from CDROM"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by held7over on 2010-11-29
I am looking for ideas concerning what I am doing wrong. I have been messing with this for a couple of weeks now, off and on.I have never had problems changing the bios to boot first from CDRom before. 

I recently acquired a Compaq Presario SR1303WM which has the XP Operating System on it. My plans are to make this computer a Ubuntu System.

In the beginning I couldn't get the bios to let me change anything at all, so I went to the manufacturer page and updated the computer to the newest bios for it.

Then, after fiddling with the bios, it let me boot ONCE from the CDW/DVD. But since then, I have not been able to repeat the boot from cd, which really makes it difficult to do an install from CD!

If I press ESC in the boot process, I get:
----------------
BOOT MENU

Select a Boot First Device:

> HDD GROUP
     - 1st Master:  ST340015A
> CD-ROM GROUP
     - 2nd Master:  TSST CDW/DVD  TS-H492A

-> <-: Expand/Close   up/down arrows:Move   Enter:Accept   F4:Exit
----------------------------
So, I collapse the HDD Group and expand the CD-ROM Group and highlight "2nd Master: TSST CDW/DVD TS-H492A" and hit ENTER to accept the CDROM as the first boot device.  BUT THAT DOESN'T SEEM TO GIVE ME A BOOT FROM CD.

So, on the next boot up I press F10 to enter Setup to make sure I have that done correctly (and nothing has changed). This is what it looks like:
-------------------------------------
BOOT DEVICE PRIORITY

1st Boot Device         [ Disabled ]
2nd Boot Device         [ CD-ROM Group ]
3rd Boot Device         [ HDD Group ]
4th Boot Device         [ Network Boot Group ]

> Floppy Group Boot Priority     [ Not Installed ]  <--grayed out
> CD-ROM Group Boot Priority     [ TSST CDW/DVD ]
> HDD Group Boot Priority        [ ST340015A ]
> Network Group Boot Priority    [ Not Installed ]   <--grayed out
---------------------------------------
So, I press F10 to SAVE and EXIT, but this does not work either.
I have also tried making both the 1st and 2nd Boot Device above the CD-ROM Group, but that doesn't seem to work either, as shown here:

1st Boot Device         [ CD-ROM Group ]
2nd Boot Device         [ CD-ROM Group ]
3rd Boot Device         [ HDD Group ]
4th Boot Device         [ Network Boot Group ]

It only worked once, early in my fiddling, and I have forgotten what the settings were at that time.....but whatever they were, they were not repeatable for some strange reason.

Does anyone have any idea what could be stopping the boot from CD?

Thanks! :D

---

### Post by bwhite82 on 2010-11-29
Can you bring up the Windows boot menu by pressing F8? There you should have an option to boot to CD.

---

### Post by Rex Bouwense on 2010-11-29
If you have changed the boot order and it still will not boot, my first guess would be that the CD is not bootable.  When you were able to boot once from the CD drive was it with the same CD?  I assume that it has a Ubuntu image on it.  Did you do an md5sum on the downloaded image?  Did you burn the ISO at the lowest speed possible?  Can you boot from a flash drive?  That is another option.

---

### Post by held7over on 2010-11-30
Just before the boot begins, the firmware shows at the bottom of the screen,
Esc = Boot Menu,  F1 = Setup,  F10 = System Recovery

Soldierboy:  I tried repetitively pressing F8 from the time I hit power on until the XP Desktop showed up, but the computer ignored the key taps on F8.  Perhaps the Esc key which gives me a menu which allows me to pick either cdrom or hard drive boot, is what you are talking about. I described this BOOT MENU above, and from what I can tell, the computer ignores my choice.  


OrRex Bouwense:  Yes. I did a md5sum and it was burned slow. Actually, I am trying with two different liveCDs:  Ubuntu 10.04 and Puppy Linix.  Both LiveCD's have booted up just fine on my other comptuers and never failed to boot.

In the boot I can see the cdrom light flashing and just when you think it is going to boot from cd, it switches to the hard drive and boots XP. 

Ha! I did the ESC to Boot Menu and again chose the cd by highlighting it and pressing ENTER, and this time it booted up on the CD....or rather it booted up to XP, and I then did a restart and it then booted on the CD. 

I would have thought it would have immediately booted on the CD if I chose it on the Boot Menu, as after you hit ENTER, you see the 3 choices of Esc, F1 and F10 again, like it is starting over....but evidently it doesn't start over and choice only works on the second boot???

Maybe something is kind of iffy?

---

### Post by wilee-nilee on 2010-11-30
Many have problems with the cd boot in bios you now know the secret now that esc button is your friend.

Everybody should know this per-session boot key it just makes life easier boot from what you want without ever going into the bios.

---

### Post by held7over on 2010-11-30
Ah Yes!  It worked twice in a row, so it is repeatable. It's just very touchy and must be done just right, else it fails....at least on this system.
I must first highlight "CD-ROM GROUP" and press ENTER, then
I must highlight "- 2nd Master: TSST CDW/DVD TS-H492A" and 
then press ENTER which restarts the boot.

Thanks everyone!  I'm going to try and figure out how to mark this thread solved.

---

