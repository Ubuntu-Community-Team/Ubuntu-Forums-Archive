---
title: "Finding Apps After Synaptic Install"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2011-01-17
OK I looked thru the tutorial guides first. If someone can point me to the area where information on finding installed apps is located.

I ran synaptic pkg mgr and installed "musica." I know it's there as I have seen it with the terminal program "aptitude."

Could not find it under Applications >Edit Menu.

I just installed Gnome-Do and Ubuntu-Tweaks as well. Haven't tried them out yet. 

Synaptic should have an area that tells you where the newly installed program runs from or something. I know where the installed files reside (ie /etc and other folders) but can't get the program invoked either thru Desktop or Terminal.

Yeah, I have so far to still go.... :D

---

### Post by smurphy_it on 2011-01-17
whereis musica

if no luck, try this command:

find / -name musica

---

### Post by smurphy_it on 2011-01-17
whereis musica

if no luck, try this command:

find / -name musica


Also, found this:

Filelist of package musica in lucid of architecture all

/etc/apache2/sites-available/musica
/etc/cron.hourly/musica
/etc/musica/apache.conf
/usr/share/doc/musica/README
/usr/share/doc/musica/changelog.Debian.gz
/usr/share/doc/musica/changelog.gz
/usr/share/doc/musica/copyright
/usr/share/musica/book_open.png
/usr/share/musica/cd.png
/usr/share/musica/control_play_blue.png
/usr/share/musica/disk.png
/usr/share/musica/group.png
/usr/share/musica/index.php
/usr/share/musica/music.png
/usr/share/musica/star_off.png
/usr/share/musica/star_on.png

---

### Post by philinux on 2011-01-17
> **ozark_hillbilly said:**
> OK I looked thru the tutorial guides first. If someone can point me to the area where information on finding installed apps is located.

I ran synaptic pkg mgr and installed "musica." I know it's there as I have seen it with the terminal program "aptitude."

Could not find it under Applications >Edit Menu.

I just installed Gnome-Do and Ubuntu-Tweaks as well. Haven't tried them out yet. 

Synaptic should have an area that tells you where the newly installed program runs from or something. I know where the installed files reside (ie /etc and other folders) but can't get the program invoked either thru Desktop or Terminal.

Yeah, I have so far to still go.... :D

I'm guessing at Applications>Sound and video.

Or Apps>Internet

---

### Post by ozark_hillbilly on 2011-01-17
Apps> Sound/Video = Bad guess. It ain't there. 
I know where the files are fellas.
How do you invoke the program?????

---

### Post by The Cog on 2011-01-17
Here is a description for musica:
> Musica is a web application for browsing and listening to your music. Songs
are organized hierarchically in folders of Artists, and sub-folders of Albums.
The PHP script presents an interface for navigating among artists and albums.
It dynamically generates playlists, allows for downloading single songs,
entire albums, and links to Wikipedia articles on artists and albums.The package lists apache as a dependency. I guess you need to use your browser to connect to [http://localhost](http://localhost), or maybe [http://localhost/musica](http://localhost/musica).

---

### Post by The Cog on 2011-01-17
Here is a description for musica:
> Musica is a web application for browsing and listening to your music. Songs
are organized hierarchically in folders of Artists, and sub-folders of Albums.
The PHP script presents an interface for navigating among artists and albums.
It dynamically generates playlists, allows for downloading single songs,
entire albums, and links to Wikipedia articles on artists and albums.The package lists apache as a dependency. I guess you need to use your browser to connect to [http://localhost](http://localhost), or maybe [http://localhost/musica](http://localhost/musica).

---

### Post by SunnyRabbiera on 2011-01-17
> **The Cog said:**
> Here is a description for musica:
The package lists apache as a dependency. I guess you need to use your browser to connect to [http://localhost](http://localhost), or maybe [http://localhost/musica](http://localhost/musica).

Yup thats what it does.
Its not an application per se

---

### Post by Elfy on 2011-01-18
Closed - more specific duplicate here [http://ubuntuforums.org/showthread.php?t=1669554](http://ubuntuforums.org/showthread.php?t=1669554)

---

