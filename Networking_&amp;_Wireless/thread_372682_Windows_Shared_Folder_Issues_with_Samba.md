---
title: "Windows Shared Folder Issues with Samba"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by ArchStanton on 2007-02-28
I recently installed Edgy on an old computer to use as a media center.  I would like it to access videos, music, photos, etc. from the other computers on my network so that I can access them all easily in my living room. My primary work computer (I work from home) that contains most of the files I want access to  is running Windows XP.

The problem I'm having is that most applications can't see the Samba shares. Amarok will play music from the shared folder, but won't add it to the Library. It seems if I want to do anything with files on the Samba shares, other than play songs in Amarok, I need to copy the files to the local computer. This would mean two copies of everything.

The solution as I see it would be to mount the network folder as a local folder (much the same way as you map a network drive in Windows), so that the network folder is access much the same way as local folders.

I've done some googleing but can't find out a way to do this, so before I give up and say its impossible, does anyone know of a way to accomplish what I'm trying to do?

---

### Post by jhansonxi on 2007-03-04
In Gnome:  Places > Connect to Server > Service type > Windows share

---

