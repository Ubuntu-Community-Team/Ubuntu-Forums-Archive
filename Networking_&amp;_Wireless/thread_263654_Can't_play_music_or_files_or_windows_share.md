---
title: "Can't play music or files or windows share"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by idn on 2006-09-23
Hi, I have set up samba so that I can see and browse the files ok, even drag them to my desktop and view the movies and music from there, but I cant seem to find a way to play the files with my media player, I have the correct codecs installed but I just can't the error 'Can't read from resource'. Is there something I have to install to get the media player to play the files directly from the share, it would certainly make things easier for me.

Thanks!

---

### Post by madmorpheus on 2006-11-24
I am getting the same thing since I upgraded from breezy to egdy.  I have no idea what it could be, but I would take a stab at the selinux policy.  I can actually play music from the samba share on a Windows pc so I would hazard that the issue is on the Edgy desktop.  I home someone one can help us.

---

### Post by doclivingston on 2006-11-24
> **idn said:**
> Hi, I have set up samba so that I can see and browse the files ok, even drag them to my desktop and view the movies and music from there, but I cant seem to find a way to play the files with my media player, I have the correct codecs installed but I just can't the error 'Can't read from resource'. Is there something I have to install to get the media player to play the files directly from the share, it would certainly make things easier for me.

What media player are you using? For this to work the player needs to support either GnomeVFS (gnome apps) or KIO (KDE apps).

On the Gnome side, Rhythmbox does and Totem might, but I don't think many others do. I don't really know about the KDE apps, but I think Amarok does.

---

