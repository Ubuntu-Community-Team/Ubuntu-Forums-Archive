---
title: "Xsane Errors"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by Lojames on 2011-01-20
I am currently using a hp 4200 all-in-one(print,scan,copy)and installed xsane.It worked great for a very short while, then all of a sudden when I tried to access my scanner xsane gave the following:ERROR during CMS conversion  could not open scanner ICM profile.I then went to the terminal and ran xsane.It outputted;lcms:error #12288;file"not found.Can anyone help me with a resolution with this problem?

---

### Post by khelben1979 on 2011-01-22
What version of Ubuntu are you using?

---

### Post by Lojames on 2011-01-22
I am currently running version 10.10

---

### Post by khelben1979 on 2011-01-22
Apparantely your system lacks a profile file, according to [this link]("http://www.mail-archive.com/lcms-user@lists.sourceforge.net/msg01808.html"). I'm not sure how you do that myself, but it seems to be the reason to your problem.

Do you have any devices to choose from when you open up the [XSane]("http://en.wikipedia.org/wiki/Xsane") application?

---

### Post by Lojames on 2011-01-23
The only device xsane looks for is my scanner and gives me PREVIEW Deskjet F4200 and it's serial.And finally the error.

In regards to the link you provided,I've been there but according to Launchpad under system/preference/monitor I get unknown,and no way to even access profiles.

I trust I am understanding all of this correctly.

---

### Post by khelben1979 on 2011-01-24
Have you tried using the [GIMP]("http://en.wikipedia.org/wiki/GIMP") software to scan images? You click on file / aquire / xsane or xscanimage. It might require installing some GIMP plugins to work.

Also, I think your problem might be that the support you got from your scanner is in alpha status, look [here]("http://hp4200-backend.sourceforge.net/"). You will be better off using another scanner, if you have one.

---

### Post by Lojames on 2011-01-26
Using xsane ability to override it's errors I was able to scan a image into gimp.However,since I am a visual artist,the whole point of using xsane is to get the image in decent shape at the scanning phase before bringing it into gimp.

I also think you are right concerning support because I don't see anything @ HP 4200 Sane Backends for HP 4280 all-in-one

Do this mean I'm stuck,other than purchasing one of the following scanners(C,Cxi,Cse)?

---

### Post by khelben1979 on 2011-01-26
> **Lojames said:**
> Do this mean I'm stuck,other than purchasing one of the following scanners(C,Cxi,Cse)?

At the moment, I think so.

[SANE: Supported Scanner devices]("http://www.sane-project.org/sane-mfgs.html#SCANNERS").

---

### Post by PaulEdwards on 2012-02-14
My wife's PC running Ubuntu 10.10 with an Epson Perfection 1660 Photo scanner connected via USB began exhibiting this issue after having worked perfectly in Ubuntu for many years.

I tracked it down to the Color Management feature in XSane.
If you don't need perfect color correctness, you can simply turn off that feature by unchecking the box in XSane > Preferences > "Enable color management".

If you do need or want this feature, you must simply configure XSane to the correct ICC/ICM color profile for your hardware (both scanner and display) which you can do in XSane > Preferences > Setup > Color management.

On my wife's PC, the Scanner default color & gray ICM-profile were both set to "(null)" which is the source of the error in the first place. They must be pointed at a file which exists and is a valid ICC/ICM color profile. Once I did so, I got a slightly different error indicating that the Display ICM-profile must also be specified using a similar file.

I set hers to the following:
Scanner default color ICM-profile = /usr/share/color/icc/sRGB.icc
Scanner default gray ICM-profile = /usr/share/color/icc/Gray.icc
Display ICM-profile = /usr/share/color/icc/sRGB.icc

I found a bunch of preinstalled ICC / ICM profiles using the following command in the terminal:
```
locate --regex \.ic[cm]$
```


I know it's probably too late for the original post author, but I hope this helps someone!
:KS

---

### Post by PaulEdwards on 2012-02-14
> **bellrpmv said:**
> I also think you are right concerning support because I don't see anything @ HP 4200 Sane Backends for HP 4280 all-in-one
Several models in [the External Backends list]("http://www.sane-project.org/lists/sane-backends-external.html#S-HPAIO") could be a match. The original poster is not specific enough... HP's model numbers are kind of crazy.

Here's a more direct reference by model number:
[http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=4280&bus=any](http://www.sane-project.org/cgi-bin/driver.pl?manu=Hewlett-Packard&model=4280&bus=any)

:)

---

