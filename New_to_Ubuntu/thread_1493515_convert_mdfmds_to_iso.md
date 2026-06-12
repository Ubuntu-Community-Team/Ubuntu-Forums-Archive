---
title: "convert mdf/mds to iso?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by stevek123 on 2010-05-25
I acquired an mds & mdf file of a pc game I want to play and would like to burn it to cd. I searched this and found the prog to do it... i downloaded iat-0.1.7. Then I found this command to perform the conversion... 
cd iat
./configure && make && sudo make install (made/installed fine)

$ iat CD.mdf CD.iso

this looks like it will convert the mdf file to the iso image... but how do I include the associated mds file??? Don't I need this file also?  
I ALSO found this command...
$ iat --iso --input=*.mdf -o *.iso
which also does not include the mds portion (table of contents if I understand it correctly)
Some help/direction please...
--- yes i saw that i can run it directly using CDEmu... but wanted to burn it

---

### Post by nhasian on 2010-05-25
see if this guide helps you out:

[http://www.howtodothings.com/computers-internet/how-to-convert-cue-bin-nrg-img-mdf-files-to-iso-files-on-ubuntu-linux](http://www.howtodothings.com/computers-internet/how-to-convert-cue-bin-nrg-img-mdf-files-to-iso-files-on-ubuntu-linux)

---

### Post by stevek123 on 2010-05-26
Thanks - that _does_ confirm the command that I need to use to convert the mdf file to iso with iat (iat replaces mdf2iso). But what do I do with the mds (tbl of contents) file?????

---

### Post by stevek123 on 2010-05-27
OK so I used this command to generate an iso file (the iat --help option was useful!)
~/Downloads/Quake2$ iat --iso -i Quake2.mdf Quake2.mds -o quake2.iso

It looks like I produced a file quake2.iso  but it does not look like it used or referenced the Quake2.mds file at all and only used the mdf file. How do I know if I got it right? Its a fair amt of work to get this game running and I'm such a noob that I wont be able to tell if I setup wrong or if my iso file is no good... ???

---

