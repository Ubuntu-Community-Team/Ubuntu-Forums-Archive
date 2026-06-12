---
title: "Windows blue screen boot from CD"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by I_MELT_FACES on 2010-08-24
Alright, I know this is not a windows forum, but I thought someone here would be able to help. First off I had windows vista. I had a very nasty virus on it. I did many virus scans and tried many things to remove the virus. Then eventually the virus would put popups even when I boot into safe mode! So eventually I got frustrated and tried to reformat the drive and install windows xp/vista again (i tried both with a CD) Both times I recieved the blue screen saying something about either my hardware is broken or I have a virus. Then I tried installing Ubuntu Lucid. It worked perfectly! There are a few flickers during boot up and shutdown as if the graphics card maybe slightly broken, but once it has loaded there are no errors. I even use compiz on the laptop and it works fine. Now this is my brother's computer and he wants windows xp on it. I tried the boot cd again after installing ubuntu, and I still get the blue screen claiming the virus is present, or the hardware is broken. Is there a way to fix this problem? is it hardware or software? Please help! Thanks very much for taking the time to read this/respond. Thanks very much!
-Justin

---

### Post by Zzl1xndd on 2010-08-24
It might be best if you could provided the exact message that is provided by Windows as this might point us in the right direction.

---

### Post by I_MELT_FACES on 2010-08-24
Alright here is the exact message:

A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this stop error screen, restart your computer. If this screen appears again, follow these steps:

Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated. Run CHKDSK /F to check for hard drive corruption, and then restart your computer. 

Technical information:
STOP: 0x0000007B (0xF78D2524, 0xC0000034, 0x00000000, 0x00000000)

That is the message I keep getting during windows xp boot from the CD. It loads everything correctly and then says "starting windows" And then I get this error message. Thanks again!

EDIT: There was absolutely NOTHING done with the hard drives. No newly installed HDD or HDD controller, the HDD was configuration was not changed in any way.

---

### Post by pricetech on 2010-08-24
That looks like a message from a running install, not from the installer.  You're getting this message booting to CD / DVD ??  Are you sure you're not missing the prompt to press a key to boot to CD / DVD ??

I'd run diags on the hardware just to be sure.  I'd also download and create a disk for DBAN.  Just boot to the DBAN disk and type in "autonuke" (without the quotes of course) and let it wipe the drive, then try again and see what happens.

---

### Post by Calash on 2010-08-24
7B is an error you will get when Windows cannot read from it's own media.  Commonly you will see this when you have a SATA enabled system but the drivers are not built into the install media.

Is this the install media that came with the computer?

You may be able to get around this by going into the BIOS and finding the SATA Operation option, sometimes called Function or Mode.  From the list see if you can find an option called "Comparability", "Legacy", "IDE", or any other option that does not have the word RAID in it.

Record the previous setting, save, and reboot and see if it helps.

Your other option is to use install media made for the computer, slipstream SATA drivers onto your install media, or try loading the drivers from floppy (F6 at the start).

---

### Post by no2498 on 2010-08-24
if the above does not work or apply to you
DO NOT TRY AN BOOT AGAIN
get barrow buy a new power supply

have had this happen to me with windows

---

### Post by I_MELT_FACES on 2010-08-27
@Calash: Thanks very much. You fixed the problem! there was a setting in the bios that was AHCI and I changed it to compatibility and it worked fine! Thank you very much!

---

