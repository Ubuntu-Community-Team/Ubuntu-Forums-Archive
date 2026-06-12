---
title: "WINE problems"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by Neil Purling on 2010-05-13
I was going to install PSP V6. If I look for  "Setup.exe" and double-click on it I get this error message:

Archive:  /media/PSP6/PSP/setup.exe
[/media/PSP6/PSP/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/PSP6/PSP/setup.exe or
          /media/PSP6/PSP/setup.exe.zip, and cannot find /media/PSP6/PSP/setup.exe.ZIP, period

I also wanted to get a Epson 3200 Photo scanner I use for scanning normal documents and large-format negatives.
I have also got a Plustek OpticFilm 7300 25mm negative scanner.

---

### Post by 3rdalbum on 2010-05-13
Go to the terminal and type 'wine', then a space, then drag the file you want to run to the terminal:

```
wine <drag file in here>
```

Otherwise it might be mistaken for a different type of file.

Also make sure that Wine is installed.

Device drivers don't work in Wine because they require an actual Windows kernel to be running. Statistically, most programs don't work in Wine. Wine is a last-resort; if you absolutely can't get your work done in any Linux software, then you should try Wine.

---

### Post by Azrael3000 on 2010-05-13
did you try vuescan ([http://www.hamrick.com/](http://www.hamrick.com/)), it comes in a linux version too and is most definately worth the little money it costs.

---

### Post by themusicalduck on 2010-05-13
You need to right click on the exe file, go to Properties and Open with tab. Select Wine in there.

---

### Post by Mark Phelps on 2010-05-13
What you REALLY need to do, if you're going to mess with Wine, is go to the WineHQ compatibility database site and look up the rating for the app and version you want to run.

I've done that for you, and as you can see in the link below, PSP v6 is NOT going to run -- no matter what you do:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=76]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=76")

---

### Post by Neil Purling on 2010-05-13
I have tried a number of game discs too and even Office '97.
When I right-click on "Setup.exe" and select 'Open with WINE Windows Program Loader' I get this:
*The file '/media/OFFICE97PRO/setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.*

It is the same story for every disc, not just Office. I wanted to Use Lotus Smart Suite as I have some docs I never got around to converting from it's native file format. The games I am interested in are the MOHAA original Trilogy, MOH Airborne, Call of Duty and GTA III.

---

### Post by themusicalduck on 2010-05-14
> **Neil Purling said:**
> I have tried a number of game discs too and even Office '97.
When I right-click on "Setup.exe" and select 'Open with WINE Windows Program Loader' I get this:
*The file '/media/OFFICE97PRO/setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.*

It is the same story for every disc, not just Office. I wanted to Use Lotus Smart Suite as I have some docs I never got around to converting from it's native file format. The games I am interested in are the MOHAA original Trilogy, MOH Airborne, Call of Duty and GTA III.

Normally with that error you would right click on the .exe, go to Properties, Permissions and check the box that says to allow executing, but I'm not sure if this will work when it's on a CD. It's worth trying it though.

You could try to copy the contents of the CD onto the harddrive and run the setup from there. You should be able to change the permissions if it's on the hard drive.

---

