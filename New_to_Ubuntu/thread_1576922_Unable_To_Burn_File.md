---
title: "Unable To Burn File"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by tb75252 on 2010-09-18
Brand new, INEXPERIENCED Ubuntu 10.04 LTS user.

I just downloaded an .iso file.  I select the file, right-click it and choose "Write to disc..".  I get a pop-up window where the "Select a disc to write to" box is grayed out and says "No disc available".

Yes, I do have a blank CD-R disc in the tray.  I tried several other blank CD-R's with the same result.  System->Administration->Disk Utility shows the CD-RW drive.  The CD-RW drive was working fine with Windows XP!!

What do I need to do for Ubuntu to see my CR-RW drive and burn this .iso file?

---

### Post by garvinrick4 on 2010-09-18
You want to BURN it to Disk use Brasero disk burner and choose burn a disk and follow instructions. I like to hit properties on face page and use slowest speed. I seem to always
get a good burn that way. Some say it does not matter anymore but I seem to stick with what works. Brasero is in Sound and Video and comes with install.

---

### Post by Clever_Username on 2010-09-18
Permissions issue?

---

### Post by shuamu on 2010-09-18
Applications > Sound and Video > Brasero Disc Burner -> burn image. Find the .iso.

If Brasero can't detect your blank disc, then chances are it's not blank. (or your disc drive has a problem. Do other discs work okay?)

---

### Post by tb75252 on 2010-09-18
> **shuamu said:**
> Applications > Sound and Video > Brasero Disc Burner -> burn image. Find the .iso.

If Brasero can't detect your blank disc, then chances are it's not blank. (or your disc drive has a problem. Do other discs work okay?)

Tried your suggestion (which brings up the same program as the one when I was right-clicking the .iso file and selecting "Write to disc...") but the "Select a disc to write to" box is still grayed out and shows "No disc available".

The disc drive was working fine before I installed Ubuntu.  (I was using Windows XP.)

---

### Post by tb75252 on 2010-09-18
> **Clever_Username said:**
> Permissions issue?

I am the only one using the computer and I believe that I have all the required permissions.  I have downloaded and installed software from Ubuntu Software Center without any permission problem.

Nevertheless, just to be on the safe side, how does one check if the permission for writing to a disc is ok?

---

### Post by garvinrick4 on 2010-09-18
> **tb75252 said:**
> Tried your suggestion (which brings up the same program as the one when I was right-clicking the .iso file and selecting "Write to disc...") but the "Select a disc to write to" box is still grayed out and shows "No disc available".

The disc drive was working fine before I installed Ubuntu.  (I was using Windows XP.)
You do not want to write to disk an .iso file needs to be BURNED to disk. Use a disk burning application and it will show up (not greyed out) Brasero is the Application as said in previous open it up and use it partner.

---

### Post by lisati on 2010-09-18
Perhaps some of the information here will be of some help: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by andymorton on 2010-09-18
Have you tried the Start-up Disk Creator? System>Administration>Start-up disk creator.

andy

---

### Post by Legendary_Bibo on 2010-09-18
I think what he means is that his disk drive isn't being detected. Go into "Places", and click on "Computer". It will show your hard drives and CD/DVD trays. Is there one that shows up?

---

### Post by tb75252 on 2010-09-18
> **Legendary_Bibo said:**
> I think what he means is that his disk drive isn't being detected. Go into "Places", and click on "Computer". It will show your hard drives and CD/DVD trays. Is there one that shows up?

Yes, there is an icon that says "CD/DVD drive".

---

### Post by Legendary_Bibo on 2010-09-18
Oh, well try a different disk. I've had disks that couldn't be detected before for no apparent reason.

---

### Post by tb75252 on 2010-09-18
> **lisati said:**
> Perhaps some of the information here will be of some help: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

The strange thing is that when I insert a blank CD-R into my burner I do not get the "CD/DVD Creator" window as the link you suggest shows (Ubuntu).

I am fairly sure that my CD burner works fine as it never gave me problems when I was using Windows XP.

---

### Post by tb75252 on 2010-09-18
> **garvinrick4 said:**
> You do not want to write to disk an .iso file needs to be BURNED to disk. Use a disk burning application and it will show up (not greyed out) Brasero is the Application as said in previous open it up and use it partner.

Did as you suggested but I still get this grayed out "No disc available" box.  As I was saying in other posts, I don't think that my CR-RW drive is bad as it was working with Windows XP.

---

### Post by lisati on 2010-09-18
*flash of inspiration*
Just a thought: It's not a RW disk by any chance? I vaguely recall seeing something in the forum some time back about how they don't always play nice.

---

### Post by shuamu on 2010-09-18
Yeah, is this just happening with detecting blank discs, or do you not have any disc drive to speak of?

When you throw in an audio cd, for example, does it show up?

---

### Post by soldier1st on 2010-09-19
what is the size of the iso? if it is 700mb or less it will need a cd disk or it won't burn but if it is larger than 700mb then it will need a dvd disk but the burn media must be a CDR or CDRW or DVD+R or DVD-R 4.7GB or 9.8GB Dual layer disk depending on the size of the iso. also consider installing K3B as i find it far better than Brasero.

---

### Post by sidzen on 2010-09-19
> **soldier1st said:**
> what is the size of the iso? if it is 700mb or less it will need a cd disk or it won't burn but if it is larger than 700mb then it will need a dvd disk but the burn media must be a CDR or CDRW or DVD+R or DVD-R 4.7GB or 9.8GB Dual layer disk depending on the size of the iso. also consider installing K3B as i find it far better than Brasero.

Even simpler and more dependable is wodim.  [PHP]mah@xxx-desktop:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'     rwrw-- : 'HL-DT-ST' 'BD-RE  UH10LS20'
-------------------------------------------------------------------------
mah@xxx-desktop:~$ wodim -sao dev='/dev/scd0' speed=8 /path/to/iso/xxxxxx.iso[/PHP]

---

