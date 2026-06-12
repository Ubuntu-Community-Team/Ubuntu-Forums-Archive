---
title: "Blank CD/DVD opening GnomeBaker?"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by CVGH on 2011-05-05
When I insert a blank CD/DVD, 10.10 does not know what to do with it and does not offer any choices. Is there a way to set this action to open GnomeBaker?

Thanks!

---

### Post by Tamlynmac on 2011-05-05
1.
Open the Nautilus file browser (places/home folder). Select "edit/preferences" and go to the media tab. At the bottom of the media tab page, you should find a section called "Other Media".

In the "Type" drop down menu: Select - blank cd or blank dvd
In the "Action" drop down menu: Chose - "Open with other application". It will open a file browser and I suspect your executable will be found in file system/usr/bin?

If the entire Media tab section appears grayed out, just below the Action menu you should find a statement like "Never prompt or start programs on media insertion". Make sure this is unchecked then perform the steps above.

2.
If it still doesn't open and it appears that the drive is not mounting - Open the Gnome Configuration Manager (System Tools menu). Under "apps/nautilus/preferences" confirm that both the "media_automount" and the "media_automount_open" are checked and that the "media_autorun_never" is unchecked.

Good Luck & Hope This Helps

---

### Post by CVGH on 2011-05-06
After checking this, still does not allow me to set a action for these media types. GnomeBaker is in /usr/sbin.

---

### Post by gordintoronto on 2011-05-06
How far did you get in the suggested steps before "it does not allow" you to continue?

---

### Post by CVGH on 2011-05-06
When I get to the "in the "Type" drop down menu: Select - blank cd or blank dvd", the options underneath are grayed out.

GConf-editor is set just as Tamlynmac said.

---

### Post by Tamlynmac on 2011-05-06
I believe the problem is that your system may not be recognizing your cd/dvd drive(s). Which is the reason the action section is grayed out. Is it being recognized in your system's BIOS? Available during the system restart/boot. What brand and model is the drive?

If it's not being recognized by your BIOS, you might wish to check and assure the power supply and data cables are connected on the back of the drive. Most BIOS will automatically do a search for existing hardware. If the BIOS isn't finding the drive, either it's not connected or it may have failed.

Are you using a dual boot system (Windows & Ubuntu)? If so does the drive work in Windows?

---

### Post by CVGH on 2011-05-07
I can put a CD/DVD in and it will mount ok. I can burn it just fine or if it's got files on it I can see them and play/run/copy etc them just fine.
I'm using a Dell 9300 laptop with 10.10 as the only OS. I do have XP as a VM, but haven't got around to figuring out how to tell it to use the CD drive yet......

---

### Post by Tamlynmac on 2011-05-07
When the blank cd/dvd are in the drive and mounted, does the grayed "Action" box change in Nautilus and permit you to select an option at that point? Odd...

---

### Post by jtarin on 2011-05-07
And what would be the media type of a "blank" disk?

---

### Post by CVGH on 2011-05-09
Cannot change options after media is mounted.
Checking the properties of the mounted disc I see in 
permissions: "the permissions of CD/DVD creator could not be determined"
Ok, so maybe there is a permissions issue?

Brian

---

### Post by CVGH on 2011-05-16
Ubuntu-Tweak file type manager let me associate blank CD/DVD's with gnomebaker.

---

