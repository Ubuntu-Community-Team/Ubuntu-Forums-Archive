---
title: "Can Pentium 3 computer boot LiveCD?"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by musicguyguy on 2009-03-16
I've got an old Pentium 3 computer that has Windows 2000 and NT installed on it. It's got a new DVD writer drive inside that can read and write fine. I'm trying to boot Ubuntu 8.10 LiveCD.
Does Pentium 3 support booting from CD? Every time I boot the computer, it shows a P3 splash screen and then goes straight to the Windows 2000/NT selection screen. I've tried pressing Esc, F8, F10, and delete, but none seem to work.
Do I need to unplug the hard drive? Does anyone have any other keys I can press at bootup?

---

### Post by overdrank on 2009-03-16
> **musicguyguy said:**
> I've got an old Pentium 3 computer that has Windows 2000 and NT installed on it. It's got a new DVD writer drive inside that can read and write fine. I'm trying to boot Ubuntu 8.10 LiveCD.
Does Pentium 3 support booting from CD? Every time I boot the computer, it shows a P3 splash screen and then goes straight to the Windows 2000/NT selection screen. I've tried pressing Esc, F8, F10, and delete, but none seem to work.
Do I need to unplug the hard drive? Does anyone have any other keys I can press at bootup?

Hi and welcome, if you burn the cd you may look here [BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")
Yes the system will need to be set to boot to the cd. Some systems I have seen even use F2, Are you pressing the keys at the P3 splash screen?

---

### Post by musicguyguy on 2009-03-16
Alright, I achieved the setup screen by pressing the escape, F2, F8, and delete button simultaneously.
I set the first boot priority to Atapi CD-ROM, which I'm pretty sure is wrong, (it doesn't look remotely like my Sony DVD-RW's name) but the complete list is Floppy (original 1st boot), ARMD-FDD, ARMD-HDD, IDE-HDD (original 2nd boot), ATAPI CD-ROM, MBA UNDI, and Intel UNDI. So it's most likely the CD-ROM... I rebooted, and it still doesn't work.
I know that the DVD drive works, because the light flashes when I put in a disk.

---

### Post by Volt9000 on 2009-03-17
When the splash screen comes up, the bottom will usually have some text telling you how to access your BIOS. The most common key for that is usually DEL, but it varies from one system to another.

Once in BIOS go to your Boot settings, and change the boot order to boot from your optical drive first.
And this is just a matter of preference, but I also like to turn off the full-screen logo. I prefer to see what goes on during the POST.

[Edit]
Just saw your post.
Are you sure you burned the CD/DVD properly?

Also, sometimes when booting from an optical drive a message will come up after the POST asking you to specifically "press a key to boot from CD..."

---

### Post by musicguyguy on 2009-03-17
Is it possible that the BIOS doesn't support the DVD-drive? I don't think so... but here's a version number I found: CA81020A.86A.0006.P03.

---

### Post by Volt9000 on 2009-03-17
If you can access and use the drive from Windows, then it means BIOS supports it, and it's installed properly.

Try changing the primary boot device to the first item in the list, and disable all other boot devices, essentially forcing your system to try only one device then give up. Try this for each device BIOS lists.

Can you provide the make and model of the optical drive?

---

### Post by GosthShadow on 2009-04-05
you can boot it up (also works on pentium 2 lol)
at which speed did you burned the cd try at the minimal speed i guess.
Have a nice day ;)

---

