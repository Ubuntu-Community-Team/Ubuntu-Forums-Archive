---
title: "Disable the CD-ROM/DVD source"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by BriMan on 2009-02-15
Please tell me how I can do this?


Anyone?

---

### Post by Elfy on 2009-02-15
Software sources- System Admin menu - disable the dvd and then reload.

---

### Post by Kareeser on 2009-02-15
... or from a command-line perspective:

```
sudo nano /etc/apt/sources.list
```

and comment out the CD source.

---

### Post by BriMan on 2009-02-15
The first thing I tried (2 days ago) was the Systems Admin menu - software sources but I have no option to disable/enable the DVD drive.

Where it says "Installable from CD-ROM/DVD" above a window, the window contains the words "To install from CD-ROM or DVD, insert the medium into the drive."

As for command lines - I am a beginner and am loath to start screwing with this without more explicit instructions.

---

### Post by hansdown on 2009-02-15
Hi BriMan.

At one time that feature used to have a check box to activate or turn off.

My set-up is the same as yours, but I don't use it.

Is there a reason you want to change it?

---

### Post by Elfy on 2009-02-15
OK - do as kareeser says using a terminal - paste in the command given - the file will open - near the top will be a line looking similar to

#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - A

Your's will not have a # at the beginning of that line - put one there.

Now do Ctrl+X - then Y and enter.

Now in the terminal run this command

```
sudo apt-get update
```

I do apologise it's a long time since I looked in software sources - it does appear to be missing.

---

### Post by BriMan on 2009-02-15
forestpixie,
I appreciate the help very much but I am still uncertain...

The line looks this -
## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main$

Since I have ## does that change the instruction?

To answer hansdown's question, I am trying to install an HP printer driver and I need to temporarily disable the feature. I have Ubuntu 8.10.

Here's what the command says:

INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubunbtu installation media inserted in the drive.

It is easy to enable the repositories but the second note comes with no link where to find help.

Cheers!

---

### Post by drs305 on 2009-02-15
Software Sources will still list the install CD/DVD in the lower window ***if*** the CD/DVD is listed anywhere in sources.list  

If the CD/DVD is active (not commented) it will appear 'checked' in the lower window. If it is listed in sources.list but is commented out ( # ) it will be listed in the window but 'unchecked'.

If there is no mention at all in sources.list, you will get the:
*To install from a CD-ROM or DVD, inssert the medium into the drive. *

---

### Post by Elfy on 2009-02-15
well that line is disabled already - why don't you popst your sources list and we can have a look at it

```
cat /etc/apt/sources.list
```

---

### Post by BriMan on 2009-02-15
Here it is-

brian@dell-desktop:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates restricted main multiverse universe #Added by software-properties
## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy mainrestricted

When I installed the upgrade to 8.10 a few days back, it asked me if I wanted to enable the drive in question which one would normally want to do so I answered yes. Dont know why dont know how otherwise.

---

### Post by Elfy on 2009-02-15
Open the file to edit it again and completely delete the 3 gutsy lines

```
deb http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[COLOR="Red"]# deb http://archive.ubuntu.com/ubuntu gutsy universe
# deb-src http://archive.ubuntu.com/ubuntu gutsy universe[/COLOR]

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu intrepid-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu intrepid-updates restricted main multiverse universe #Added by software-properties
[COLOR="Red"]## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy mainrestricted[/COLOR]
```

Then try the update command once more

---

### Post by jon eric pipes on 2009-02-18
im trying to install my hp laserjet p1005 on a compaq with AMD sempron.  im running gutsy gibbon.  i tried the foomatic and it did not work.  then i read this thread:[http://ubuntuforums.org/showthread.php?t=1054338&highlight=hp+1005](http://ubuntuforums.org/showthread.php?t=1054338&highlight=hp+1005)
and decided to try that method.  so i went to this site as recommended in above thread:[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)
and when running the terminal got this message:


Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubunbtu installation media inserted in the drive.

i checked to find out that universe and multiverse are enabled - but didnt know how to disable the cd/rom drive and got this message:

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

### Post by Elfy on 2009-02-18
Do thisn from aterminal to open the file for editing

```
gksudo gedit /etc/apt/sources.list
```

Once the file is open lookk for a line looking similar to

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy mainrestricted
```

**** # at the beginning of the line - saev file and close gedit

From  aterminal

```
sudo apt-get update
```

Then try again to do what you are trying to, if you get errors with the install that aren't associated with getting the cdrom disabled please start a new thread on your issue.

---

### Post by BriMan on 2009-02-18
I was ultimately successful getting the driver to install by avoiding using the automatic install feature. All of this enable/disable crap was giving me a headache.

I used this link instead -

[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

This process was a little more cut-n-pasty on-hands but it was smooth as silk. My printer works great!!

---

