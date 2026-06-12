---
title: "Help with HP Laserjet p1005 printer"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by jon eric pipes on 2009-02-18
i posted this already on another thread but im going to repost it here.

im trying to install my hp laserjet p1005 on a compaq with AMD sempron. im running gutsy gibbon. i tried the foomatic and it did not work. then i read this thread:[http://ubuntuforums.org/showthread.p...hlight=hp+1005](http://ubuntuforums.org/showthread.p...hlight=hp+1005)
and decided to try that method. so i went to this site as recommended in above thread:[http://hplipopensource.com/hplip-web...all/index.html](http://hplipopensource.com/hplip-web...all/index.html)
and when running the terminal got this message:

> 
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information. Disable the CD-ROM/DVD source if you do not have the Ubunbtu installation media inserted in the drive.

i checked to find out that universe and multiverse are enabled - but didnt know how to disable the cd/rom drive and got this message:
> 
DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
|error: No output seen in over 300 sec... (Is the CD-ROM/DVD source repository enabled? It shouldn't be!)
fatal error: :hplip-install
error: Command failed. Re-try #1...
Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Command failed. Re-try #2...
Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Command failed. Re-try #3...
Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Package install command failed with error code 255
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y

a search of the ubuntu forums and i discovered what "main" was and how to disable the cdrom drive, so now that was done but this is what i get now:
> 
Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Package install command failed with error code 255
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Package install command failed with error code 255
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Package install command failed with error code 255
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Package install command failed with error code 255
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo aptitude install --assume-yes build-essential'
Please wait, this may take several minutes...
error: Package install command failed with error code 255
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ?

where do i go from here?

---

### Post by NewJack on 2009-02-20
This is your printers listing on the OpenPrinting Database: 

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_P1005](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_P1005)

Says it works "Mostly", meaning some features may not work.  Also there is a recommended printer driver for it on that page.

Good Luck!

---

### Post by jon eric pipes on 2009-02-25
i have no idea of how to use the information on this link
perhaps i should take the printer back 
jon

---

### Post by mikechant on 2009-02-25
> but didnt know how to disable the cd/rom drive and got this message:


The link you mentioned, i.e.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

shows you (right near the top of the article) how to enable/disable the various repositories. At the bottom of the repository selection screen there is a tick box to enable/disable software installation from CD/DVD. Just untick this box and click the close button and try again.

---

