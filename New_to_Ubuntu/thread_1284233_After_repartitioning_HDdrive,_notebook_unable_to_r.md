---
title: "After repartitioning HDdrive, notebook unable to read from cd"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by webwiller on 2009-10-06
Hi there!
I have a big issue here! As this notebook is not mine and I convinced a friend to try out Ubuntu and go for a Dual-boot for a while. He's very inexpert so I offered me to make a repartitioning and a dualboot for him, as I did plenty times.
I repartitioned the hard drive of his Acer Aspire 5100 with GParted from Ubuntu's live CD, everything nice and smooth.
After that I went for a WinXP install but the PC would not read the CD, so I tried another one and even a Win7 one. None of em worked. Pc continued to shut down and restart with bios screen only. Checked the Bios order to maker sure CD burner was on list.
I than tried with Ubuntu live CD again, planning to recover Grub later in case, but not even this worked no more!!!
Any clue?
I cannot be this bad lucky that I got a hardware failure the exact day he gave it to me!!!
Pleaseeeeeee!!!! Any help to check things out would be greatly appreciated!!! ;)
:-'''(

---

### Post by mikeyphi on 2009-10-07
Confirm that the CD drive is set as first priority on BIOS boot list.

I'm sure you've already done that! so it seems that in partitioning (rather than installing) you may have lost software required for CD drive.

A possible solution is to use 'Recovery mode' on the XP CD...this loads a CD driver.

If you are not even seeing anything on any CD - then it points to a (unexpected) CD drive failure.

Is there a USB slot? Could you use Ubuntu from a USB drive to access the HD?

---

### Post by Bartender on 2009-10-07
This sounds like a horrible situation.  You offer to help someone out, then it all goes to hell.

What do you have for getting the laptop back to where it was?  Did you burn recovery discs?

It seems highly unlikely that you had hardware failure at the same time.  You were able to use GParted from the optical drive, then suddenly the optical drive goes gunnysack?  Doubtful.

mikeyphi's advice sounds good to me - borrow an external USB CD drive, make the appropriate changes in BIOS, see what happens.

Can you borrow a USB dock from someone?  I can confirm that Ubuntu will boot from a HDD plugged into a USB dock.  Even if the HDD came from another PC!  Ubuntu will stop the first time, and say it has to fix something, then restart, and boot up.  This wouldn't help you to install XP, but might help to diagnose what went wrong.  You could boot from an Ubuntu HDD in a dock, then see if Ubuntu can access the optical drive.

---

### Post by _duncan_ on 2009-10-08
Check if there is an option on the bios screen to set the mode of the cd drive. Possible choices might be IDE, SCSI, etc. Play around with these settings and see if one of these will allow you to boot from the CD drive.

---

