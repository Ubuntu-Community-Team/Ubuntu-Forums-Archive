---
title: "Wifi adaptor not functioning (was: Uhh....Crap....)"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by SHIFTY101EASY on 2007-02-13
okay i just installed Ubuntu and am really just hoping and guessing that somehow i figure out how to install Wine so i can install my wireless WIFI adapter on the computer...so anyways, i read something about repositories and i think i deleted the "default" ones....i dono if this matter or what but theres an error thing that keeps coming up and i cant figure out what i did or what a repository even is.....???

someone just please help me....lol

---

### Post by aktiwers on 2007-02-13
The Repository is something you can use to download free software from.
You can browser them doing: Startmenu=>System=>Administration=>Synaptic Package Manager.

Or open Terminal and type: sudo apt-get install nameofprogram

I recommend you to install all the basic software like flash, java, wine and so on using Automatix2
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Its really easy :)

Good luck..

---

### Post by Titus A Duxass on 2007-02-13
Try using Automatix to install wine, it's at [www.getautomatix.com](www.getautomatix.com).

Damn! Too slow!

---

### Post by Jussi01 on 2007-02-13
> **SHIFTY101EASY said:**
> okay i just installed Ubuntu and am really just hoping and guessing that somehow i figure out how to install Wine so i can install my wireless WIFI adapter on the computer...so anyways, i read something about repositories and i think i deleted the "default" ones....i dono if this matter or what but theres an error thing that keeps coming up and i cant figure out what i did or what a repository even is.....???

someone just please help me....lol

Hei, you dont need wine to get the wireless running. If the driver is not supported by linux then you need to use the ndis wrapper tool. What is your wireless card?

---

### Post by Maestro23 on 2007-02-13
Some links for the OP to read/bookmark:

Enable Extra Repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Installing in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
                              [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by SHIFTY101EASY on 2007-02-13
okay well basically anything i tried its been giving me that error because i deleted the original repositories....im currently reinstalling and will try what you guys suggested again....

this is pretty frustrating but im determined..... been going since this afternoon and its now 6:15 in the morning......

i wish linux just had the regular old double click and it starts installing....lol

---

### Post by kittyhawk63 on 2007-02-13
*...this is pretty frustrating but im determined..... been going since this afternoon and its now 6:15 in the morning......*

Hey Shift,
I've been working three days to install Ubuntu. I had a video card incompatability...computer kept crashing every time I went into Ubuntu. I hung in there. With the help of the good people here at the forum I have learned much and have things running smoothly. Don't get discouraged. Just stay with it to the end. It will be well worth the effort. There is a sizeable learning curve. No more ".exe" stuff. The best thing, no more Gates controlling your life. You will learn more how a computer works. Once you get over the "don't touch this" syndrome you will be okay...**BUT**, I highly recommend that you not touch system files without asking a techie here first. Got a question or need help, you have found the place for both.
Good luck newbie...from another newbie! :)

---

### Post by aktiwers on 2007-02-13
> **SHIFTY101EASY said:**
> okay well basically anything i tried its been giving me that error because i deleted the original repositories....im currently reinstalling and will try what you guys suggested again....

this is pretty frustrating but im determined..... been going since this afternoon and its now 6:15 in the morning......

i wish linux just had the regular old double click and it starts installing....lol

It actually has.. but its on .deb files. :)

Did you delete all the links in your sourcelist?

If you have edgy (6.10), you can use mine:

> deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy main restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy-updates main restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
#AUTOMATIX REPOS END

# Treviño's Ubuntu edgy Beryl-SVN Repository (GPG key: 81836EBF - DD800CD9)
# Daily Updated Beryl (and related projects) Packages...
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

# Ubuntu edgy
deb [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy main restricted universe multiverse
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy main restricted universe multiverse

# Ubuntu edgy updates
deb [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy-updates main restricted universe multiverse

# Ubuntu edgy backports
# deb [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy-backports main restricted universe multiverse

# Ubuntu edgy security fixes
deb [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy-security main restricted universe multiverse
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) edgy-security main restricted universe multiverse

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

## E17 repository "edevelop.org"
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17
deb-src [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17

deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib


Just copy paste it into your /etc/apt/sources.list
```
sudo gedit /etc/apt/sources.list
```

---

### Post by Brunellus on 2007-02-13
Thread title edited to reflect nature of support request.  Please use the thread title to sum up your problem briefly--that way users who CAN help you know that they can help you.  Expressions of regret, humility, or self-flagellation are unlikely to elicit competent technical advice.

first:  WINE will not solve your wifi adaptor problem.  Put that out of your mind completely.

Post the name and manufacturer of your wifi adaptor, and we'll see what we can do to help you get it running.

---

### Post by MCSE_Crossover on 2007-02-13
> **SHIFTY101EASY said:**
> 
i wish linux just had the regular old double click and it starts installing....lol

It does! :) that is really what synaptic is for. It is your package manager. You do a "search" for the program you want, select "Mark for Installation" and then click "Apply!" It is that easy. All of your programs, source code, and application in one centralized, searchable location. Enjoy!

---

### Post by SHIFTY101EASY on 2007-02-13
okay well i think i either had a bad install or did something wrong but i kill disked the computer, burned new cd and reinstalled and it went perfectly...installed automatix2 and i am installing stuff through that now.

is automatix2 basically just a "overlay" of the terminal or something?

---

### Post by Brunellus on 2007-02-13
automatix is a script that automates a number of terminal commands.

The terminal is always there.  it is the man behind the curtain controlling the "Wizard of Oz" that you see in your fancy X session.

---

### Post by SHIFTY101EASY on 2007-02-13
okay well back to the main topic....i installed a program through automatix2 that said i could use windows drivers for my wireless adapter i think. what do i do now? just install the drivers like i would do on XP or something?

---

### Post by SHIFTY101EASY on 2007-02-13
i have a linksys WUSB54GC and downloaded the driver .exe but i dont think i will be able to run it in the driver wrapper tool since its an .exe...at least thats what it says....what do you guys suggest as the first step towards getting it done...?

i really want my family off my computers so this one NEEDS internet so they can use (and probably wreck it) it far away from me lol.

---

### Post by SHIFTY101EASY on 2007-02-14
bump.

---

### Post by Brunellus on 2007-02-15
see [this wiki page](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

