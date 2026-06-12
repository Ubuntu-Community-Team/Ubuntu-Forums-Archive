---
title: "Opening files through Samba...easy...right...?"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by eeffoc on 2010-09-27
First off, thank you so much for taking the time out to check this post out! I've been on #xubuntu irc.freenode.net frequently, to no avail with this issue. Nonetheless, I've got xubuntu on an older Toshiba Tecra M2 that I'm primarily using as an IRC, ereader and netbook machine. Since said laptop only has a 40 gig HDD I would LOVE to be able to leave all of my files on one of my network storage devices. I have setup Samba and can access my 2TB network storage device which houses all of my .cbr and .cbz files. I am trying to read comic books through a program called Comix in xubuntu. I can navigate through every parent directory just fine, being able to see all of the .cbr and .cbz files on the network. I just am not able to open said files through Comix or transfer them across the network... Is there a better way to get this to work? The files are housed on a Windows (ewww I know!) machine. Thank you so much in advance!

---

### Post by ddnev45 on 2010-09-27
I've had good luck with this method:

[Mount samba shares with utf8 encoding using cifs]("http://ubuntuforums.org/showthread.php?t=288534&highlight=cifs")

---

### Post by eeffoc on 2010-09-27
> **ddnev45 said:**
> I've had good luck with this method:

[Mount samba shares with utf8 encoding using cifs]("http://ubuntuforums.org/showthread.php?t=288534&highlight=cifs")

AWESOME! Success! Thank you so much! I am yet to get the method to display a mounted folder/drive on my desktop, but after looking in my /media/sharename, I discovered that everything is indeed showing up. I am now able to open my .cbz and .cbr files as if they were sitting right on my local desktop! Thank you so much for directing me to the right place!

---

### Post by TCHebb on 2010-09-27
I believe the disk appearing on the desktop only applies to GNOME and KDE.

---

