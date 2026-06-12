---
title: "VNC and Torrents"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Taoh15 on 2009-03-25
Hi all

I'm not exactly a newbie to Linux but this is my first real attempt to set up something useful. I want to set a small Ubuntu machine which will download my torrents at night. To that end I thought that I would set up a Ubuntu 8.10 machine using an old Epia machine. This I have done using desktop and standard setup. I then wanted to set up VNC to access this machine from my main XP machine. I found the article [How To: Set Up VNC on Ubuntu in Four Steps]("http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php") and followed it and got VNC working. I then went to System | Preferences | Sessions and added a VNC startup program as per step 4.
However when I rebooted the box and tried to access it the VNC server seems to be running but it won't accept my password!!!
Any ideas?

I then found the further discussions on using xorg sop decided to try that route however I can't find any sign of xorg.conf in fact there is no /etc/x11 directory

Second thing I need is a bittorrent client that has web access (internal lan) and scheduling so that I can limit when it downloads to between 10pm anf 7am.

Cheers
Taoh

---

### Post by gletob on 2009-03-25
Well for number two you can use Transmission, the torrent client that comes installed on the default ubuntu install.  It has a web interface and scheduling in the preferences.

EDIT AGAIN: That guide is outdated you can just go to System>Prefs.>Remote Desktop and easily set up vnc with a few mouse clicks.

---

### Post by snova on 2009-03-25
> **Taoh15 said:**
> I then found the further discussions on using xorg sop decided to try that route however I can't find any sign of xorg.conf in fact there is no /etc/x11 directory

No idea about the rest, but if you're doing this from the command line (where it is less evident), /etc/X11 must be capitalized, as Linux is case-sensitive.

---

### Post by lovinglinux on 2009-03-25
Best torrent client in my opinion is Deluge. It does what you need, is very user friendly and has several important features.

---

### Post by gletob on 2009-03-25
> **lovinglinux said:**
> Best torrent client in my opinion is Deluge. It does what you need, is very user friendly and has several important features.

I wish deluge had scheduling.  It is the ONE feature it needs.

---

### Post by lovinglinux on 2009-03-25
> **gletob said:**
> I wish deluge had scheduling.  It is the ONE feature it needs.

Version 0.5.x has a scheduler plugin.

---

### Post by llamabr on 2009-03-25
I like deluge, too.

This could also easily be accomplished by a very simple script, running btdownloadheadless or btdownloadcurses, and a cronjob.

---

### Post by Taoh15 on 2009-03-27
> **snova said:**
> No idea about the rest, but if you're doing this from the command line (where it is less evident), /etc/X11 must be capitalized, as Linux is case-sensitive.

Damn! I forgot about Linux case sensitivity. Found it!
:P

---

### Post by Taoh15 on 2009-03-27
> **lovinglinux said:**
> Best torrent client in my opinion is Deluge. It does what you need, is very user friendly and has several important features.

Deluge up and running with scheduling - exactly what I needed.

Cheers
Taoh

---

