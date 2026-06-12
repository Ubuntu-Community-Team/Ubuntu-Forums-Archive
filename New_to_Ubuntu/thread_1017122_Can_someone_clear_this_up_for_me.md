---
title: "Can someone clear this up for me?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-12-20
just been reading into how to convert a .dmg file into an iso image.

Basically i have followed the instructions 

> 
Installation

Download the latest version from here and move the perl script for example into the directory: /usr/local/bin/

sudo mv dmg2iso.pl /usr/local/bin/

Usage

dmg2iso.pl <filename.dmg> <filename.iso>

Example

dmg2iso.pl disc1.dmg disc1.iso



but am confused at what to do when it says 

> Usage

dmg2iso.pl <filename.dmg> <filename.iso>

typing 

> dmg2iso.pl wiretapstudio.dmg wiretapimage.iso

brings up the error 

> bash: dmg2iso.pl: command not found
 

what am i doing wrong?

---

### Post by phantomjoker on 2008-12-20
also - i have tried but sudo at the beginning doesn't work

---

### Post by drs305 on 2008-12-20
Your system is not finding dmg2iso.pl

Did you move dmg2iso.pl to /usr/local/bin? 
Is /usr/local/bin in your PATH? You can check by running:
```

$PATH
*and:*
ls /usr/local/bin/dmg2iso.pl

```
Is the file wiretapstudio.dmg in the directory you are running the command in?

If all else fails, try using the full paths. For instance, if you have wiretapstudio.dmg on your Desktop, run:
```

/usr/local/bin/dmg2iso.pl ~/Desktop/wiretapstudio.dmg ~/Desktop/wiretapimage.iso

```

---

### Post by OutOfReach on 2008-12-20
Apprantly you needed to download a Perl script, did you do so?
Is the script in the working directory?
Is the perl script executable?

Try doing:
```

./dmg2iso.pl wiretapstudio.dmg wiretapimage.iso

```

---

### Post by nhasian on 2008-12-20
you can get acetoneISO from getdeb:

[http://www.getdeb.net/search.php?keywords=acetoneiso](http://www.getdeb.net/search.php?keywords=acetoneiso)

that will allow you to use the mdf file

---

### Post by phantomjoker on 2008-12-20
my perl script is on my desktop. and so is the .dmg file

---

### Post by phantomjoker on 2008-12-20
> ubuntu:~$ sudo /home/mckenzie/dmg2iso.pl ~/home/mckenzie/desktop/wiretapstudio.dmg ~/home/mckenzie/desktop/wiretapimage.iso
[sudo] password for mckenzie: 
sudo: /home/mckenzie/dmg2iso.pl: command not found


?

---

### Post by phantomjoker on 2008-12-20
> **nhasian said:**
> you can get acetoneISO from getdeb:

[http://www.getdeb.net/search.php?keywords=acetoneiso](http://www.getdeb.net/search.php?keywords=acetoneiso)

that will allow you to use the mdf file


Thanks, but im trying to convert a .dmg file (apple not windows)

---

### Post by StevenHarper on 2008-12-20
Then  do this

Open a terminal (applications -> terminal)

```
cd ~/Desktop
chmod +x dmg2iso.pl
./dmg2iso.pl wiretapstudio.dmg wiretapimage.iso
```

---

### Post by handydan918 on 2008-12-20
You quoted the installation instruction thus:
> Download the latest version from here and move the perl script for example into the directory: /usr/local/bin/


But then you said the script was on your desktop. You desktop is not in your $PATH. Move the script to /usr/local/bin, like it says, and do ```
chmod a+x filename
```

---

### Post by RaZoR1394 on 2008-12-21
Why are you using dmg2iso? It's obsolete. Use dmg2img.

:confused::lolflag::rolleyes:

[http://vu1tur.eu.org/tools/](http://vu1tur.eu.org/tools/)

---

### Post by RaZoR1394 on 2008-12-21
And to clear things up.

chmod +x dmg2iso.pl
./dmg2iso.pl

is not the correct way.

perl dmg2iso

is.

---

### Post by bulletxt on 2008-12-22
I'm not undersanding what's going on here... anyways to convert a DMG to ISO use AcetoneISO. 

[http://www.acetoneteam.org](http://www.acetoneteam.org)

---

### Post by nhasian on 2008-12-22
that's what i said but apparently its an apple dmg file and not a windows dmg file...

> **bulletxt said:**
> I'm not undersanding what's going on here... anyways to convert a DMG to ISO use AcetoneISO. 

[http://www.acetoneteam.org](http://www.acetoneteam.org)

---

### Post by bulletxt on 2008-12-23
try this:

[http://hem.bredband.net/catacombae/dmgx.html](http://hem.bredband.net/catacombae/dmgx.html)

---

