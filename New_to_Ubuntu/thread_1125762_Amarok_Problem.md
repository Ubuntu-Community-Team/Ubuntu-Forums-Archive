---
title: "Amarok Problem"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by thraxsa on 2009-04-14
I can't play mp3's in amarok - it appears I have d/l the codecs but when  i play something I can see the equalizer graphic working away but no sound ???

My sound is fine for other Mp3 applications - a mystery why it is not working ...

Any suggestions ????

---

### Post by Virtualboxbuntu on 2009-04-14
Do other file formats (like .ogg) play in Amarok?

---

### Post by Castor68 on 2009-04-14
I got the same problem with MP3. All other formats are fine in Amarok.

---

### Post by Castor68 on 2009-04-14
Ok. I think is something about the codecs.

I did this command in terminal

**sudo aptitude install xine-ui libxine-extracodecs**

After this, I can play MP3 files in Amarok.

---

### Post by Castor68 on 2009-04-14
I think Xine has the codecs for Amarok.

---

### Post by thraxsa on 2009-04-15
wierd - i installed as above, but I can play Amarok fine in gnome but not in kde !!!!

How does that work ? consider it is a kde application ????

Any other suggestions ( besides biting the bullet and only using it in gnome) ??

---

### Post by Virtualboxbuntu on 2009-04-15
Hmm... that means that it's either some extremely strange bug in KDE, or something in your user account that's messed up, in ~/.kde.

What if you created a new user account (keeping your current one as well) and tried playing mp3s from it (in KDE)? And are you on KDE 3 or 4?

---

### Post by thraxsa on 2009-04-16
> **Virtualboxbuntu said:**
> Hmm... that means that it's either some extremely strange bug in KDE, or something in your user account that's messed up, in ~/.kde.

What if you created a new user account (keeping your current one as well) and tried playing mp3s from it (in KDE)? And are you on KDE 3 or 4?

kde 4 - I am not overly worried, Exaile ( the gnome based Amarok ) works fine in kde and gnome !!!!

---

### Post by thraxsa on 2009-04-16
> **Virtualboxbuntu said:**
> Hmm... that means that it's either some extremely strange bug in KDE, or something in your user account that's messed up, in ~/.kde.

What if you created a new user account (keeping your current one as well) and tried playing mp3s from it (in KDE)? And are you on KDE 3 or 4?

created another user account - same thing, amarok not playing in kde

---

### Post by Virtualboxbuntu on 2009-04-16
Hmm... something strange is going on, something is messed up in the way KDE handles KDE programs' sound. During the entire time you've had this installation of your distro, has Amarok ever played mp3s properly, or did it just stop playing them recently? And what distro are you using?

And what appears when you run the following commands in the terminal?
```
dpkg-query -s phonon
``````
dpkg-query -s kdebase
```

---

### Post by thraxsa on 2009-04-17
> **Virtualboxbuntu said:**
> Hmm... something strange is going on, something is messed up in the way KDE handles KDE programs' sound. During the entire time you've had this installation of your distro, has Amarok ever played mp3s properly, or did it just stop playing them recently? And what distro are you using?

And what appears when you run the following commands in the terminal?
```
dpkg-query -s phonon
``````
dpkg-query -s kdebase
```

As far as I can remember, I have never got Amarok working in KDE but it works in gnome.  

The strange thing is that Exaile, Sound Juicer, Rythm Box, KSCD, VLC - all work in kde and gnome without any problems.

I will try the code you suggested when I get home ( currently at work again).


Using Ubuntu 8.10

---

### Post by thraxsa on 2009-04-17
ajh@ajh-desktop:~$ dpkg-query -s phonon
Package: phonon
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 76
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Architecture: all
Version: 4:4.3.1-0ubuntu1~intrepid1
Depends: phonon-backend-gstreamer | phonon-backend, libphonon4 (>= 4:4.3.1-0ubuntu1~intrepid1)
Suggests: phonon-backend-xine, phonon-backend-vlc, phonon-backend-mplayer
Description: metapackage for Phonon multimedia framework
 Phonon is the Qt4 multimedia API, which provides a task-oriented abstraction
 layer for capturing, mixing, processing, and playing audio and video content.
 .
 This metapackage ensures a working Phonon (libphonon4 and a backend).
Homepage: [http://phonon.kde.org/](http://phonon.kde.org/)
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qtajh@


ajh-desktop:~$ dpkg-query -s kdebase
Package: kdebase
Status: install ok installed
Priority: optional
Section: kde
Installed-Size: 180
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Architecture: all
Version: 4:4.2.2-0ubuntu1~intrepid1
Replaces: kdebase-kde4
Depends: dolphin (>= 4:4.2.2-0ubuntu1~intrepid1), kappfinder (>= 4:4.2.2-0ubuntu1~intrepid1), kdebase-bin (>= 4:4.2.2-0ubuntu1~intrepid1), kdepasswd (>= 4:4.2.2-0ubuntu1~intrepid1), kfind (>= 4:4.2.2-0ubuntu1~intrepid1), konqueror-nsplugins (>= 4:4.2.2-0ubuntu1~intrepid1), konqueror (>= 4:4.2.2-0ubuntu1~intrepid1), konsole (>= 4:4.2.2-0ubuntu1~intrepid1), kwrite (>= 4:4.2.2-0ubuntu1~intrepid1), libkonq5 (>= 4:4.2.2-0ubuntu1~intrepid1), kdebase-plasma (>= 4:4.2.2-0ubuntu1~intrepid1)
Conflicts: kdebase-kde4
Description: base applications from the official KDE release
 KDE is produced by an international technology team that creates free and open
 source software for desktop and portable computing. Among KDE's products are a
 modern desktop system for Linux and UNIX platforms, comprehensive office
 productivity and groupware suites and hundreds of software titles in many
 categories including Internet and web applications, multimedia, entertainment,
 educational, graphics and software development.
 .
 This package provides core applications for the KDE 4 desktop.
Homepage: [http://www.kde.org/](http://www.kde.org/)
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
ajh@ajh-desktop:~$ 

[email]-kde@lists.debian.org[/email]>


... here is my screen dump from those 2 commands

---

### Post by thraxsa on 2009-04-18
looks like I might have fixed the problem - upgraded to Amarok 2 for kde4 and appears to work fine ....

---

### Post by Virtualboxbuntu on 2009-04-18
It never occurred to me that you might be using Amarok 1... that would certainly explain it.

So it's working now?

---

### Post by thraxsa on 2009-04-19
yep - working well !!!  thanks for your help in any case : )

---

### Post by sumitsen on 2009-04-20
> **Castor68 said:**
> Ok. I think is something about the codecs.

I did this command in terminal

**sudo aptitude install xine-ui libxine-extracodecs**

After this, I can play MP3 files in Amarok.

Thanks Castor68 for your suggestion. I was having a similar problem in Ubuntu 9.04 RC fresh install and installed amarok but it will not play mp3 and even not add it in the library.

Now its fixed.

Thanks & Cheers/Sumit

---

