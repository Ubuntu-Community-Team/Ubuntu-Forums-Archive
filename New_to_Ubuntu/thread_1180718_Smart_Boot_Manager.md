---
title: "Smart Boot Manager"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by altocumulus on 2009-06-07
May I ask someone to clarify this :


[LIST=1]
[*]Smart Boot Manager is on the Ubuntu install CD as /install/sbm.bin.  For more information and the newest version, please see [Smart Boot Manager]("http://sourceforge.net/projects/btmgr").
[*]Now we need to make a boot floppy.
[LIST]
[*]With Windows, use a utility called [rawwrite]("http://www.chrysocome.net/rawwrite").
[LIST=1]
[*]Format the floppy disk. For this you may open a command prompt (Start / Run / "cmd") and type format a:
[*]Then use rawrite command: rawrite -f sbm.bin (rawwritewin.exe sbm.bin)
[/LIST]
 
[/LIST]
 
[/LIST]
I can read the Ubuntu files on my CD, and run WUBI, (but it won't boot). sbm is on the CD.

I have downloaded rawwrite, and formatted a floppy.

Question :
where is rawwrite to be downloaded to ? c: or a:....

from a: I get ..... rawwritewin.exe is not recognised as an internal or external command, operable program or batch file.
from c: I get Error 2 opening image file 'sbm.bin'. The system cannot find the file specified.


On a separate note: 
Ubuntu CD boot helper fails because it cannot find the required installation files...

---

### Post by altocumulus on 2009-06-07
Okay - I've worked round this .....

running rawwrite directly and opened up the dialog boxes...

entering the sbm in the routine I have copied the file to the floppy.

SBM has allowed me to boot from the floppy and sbm has come up with an error

Disk error! 0x0C .... which I'm afraid tells me nothing as to where the error is, unless the C is significant......

---

### Post by kwacka on 2009-06-07
The error means there is a problem with the CD; how did you burn it? 

I.e. did you extract the .iso file and burn it, or did you use (e.g.) nero to 'burn cd image'? 

If you did the first, you need to burn another disk using the second method.


If you are trying to install on a Satellite 1900 you shouldn't need SMB - it should boot direct from CD.

---

### Post by altocumulus on 2009-06-07
> **kwacka said:**
> The error means there is a problem with the CD; how did you burn it? 

I.e. did you extract the .iso file and burn it, or did you use (e.g.) nero to 'burn cd image'? 

If you did the first, you need to burn another disk using the second method.



I downloaded the .iso file, Firefox automatically unzipped it using winrar, then I burned it as an image using _Nero_.

I have, also, downloaded the .iso file, then used _InfraRecorder_, and followed the documentation to the letter and burned the file as an image which did the unzipping during that process.

So I've done each at least 3 times, plus used Nero to create a boot CD - which of course failed.

The .iso file was successfully checked against md5sum.

> **kwacka said:**
> 
If you are trying to install on a Satellite 1900 you shouldn't need SMB - it should boot direct from CD.

Maybe it should, but it doesn't. I can read the files and can also run wubi from the disc. 
But I am unable to boot using it. The cd drive seems to be OK, as a boot option, otherwise I would not have been able to use Toshiba Recovery discs.


I'm running out of options, the only one left is to install under windows and then follow the suggestion in ubuntupocketguide and convert to a full disc installation from there....

---

### Post by LewRockwell on 2009-06-07
if your BIOS is set to check the optical drive first for bootable media then it's the disk and not your laptop.

and you said you've been able to boot up the Toshiba CDs so again, it's the disk and not your machine.

burn a new disk at the slowest burn speed available to you and then try it again.

also, get Puppy linux and try it also.

never give up, never surrender!

---

### Post by kwacka on 2009-06-07
You will need to burn the CD image - anything else is useless.

As you have nero, click on 'File' and then 'Burn CD Image'. browse for the Ubuntu .iso file (you may need to change the 'File Types' at the bottom of the browse window.

As has been said, burn at a slower speed to avoid burn errors.

---

### Post by altocumulus on 2009-06-08
> **LewRockwell said:**
> if your BIOS is set to check the optical drive first for bootable media then it's the disk and not your laptop.

and you said you've been able to boot up the Toshiba CDs so again, it's the disk and not your machine.

burn a new disk at the slowest burn speed available to you and then try it again.

also, get Puppy linux and try it also.

**never give up, never surrender!**


aye, it's only been 4 weeks that this whole process has taken me, so far ....  :D

---

### Post by altocumulus on 2009-06-08
> **kwacka said:**
> You will need to burn the CD image - anything else is useless.

As you have nero, click on 'File' and then 'Burn CD Image'. browse for the Ubuntu .iso file (you may need to change the 'File Types' at the bottom of the browse window.

As has been said, burn at a slower speed to avoid burn errors.


Thanks - but I've done that (at least 3 times) ...... 4th time lucky, though I'll stick with InfraRecorder, that is mentioned by example in the docs ....


good job cds are so cheap .... ;)

---

### Post by altocumulus on 2009-06-08
I've decided to install via wubi, under windows Xp.....

During the installation process, at the 20% installation, guided partitioning, I have an error statement....

"No root file system is defined. Please correct this from the partitioning window".

The only available option is a go-back "OK" button. 
This does not 'take me back' and I am stuck in a loop between the 

"no root file error" and the "checking the installation" windows.....

---

### Post by altocumulus on 2009-06-08
Me thinks cdrom drive is knackered.....

---

### Post by LewRockwell on 2009-06-08
Have you ever been able to boot up a live-run *nix distro in that machine?

---

### Post by altocumulus on 2009-06-08
> **LewRockwell said:**
> Have you ever been able to boot up a **live-run *nix distro** in that machine?


I'm going to have to confess ignorance of what you mean....


Last successful bootup on the drive was using Toshiba Recovery Discs, which are, of course, Windows......

That I no longer seem able to read any discs in the drive is a sign of something odd..

---

