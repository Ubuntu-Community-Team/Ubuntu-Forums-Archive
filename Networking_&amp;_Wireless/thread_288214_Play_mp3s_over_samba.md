---
title: "Play mp3s over samba"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by dmsn on 2006-10-29
Heya
I use samba on my server and laptop on lan.
When i stream a mp3 over network i cant play it in xmms.
I tested a program called gstreamer but that didnt work.
I must download the mp3 file for play it in xmms and i dont want that.
I want normal streaming over samba.

P.S it works perfect when i use windows on this laptop.


How can i fix this you think ?

---

### Post by pete on 2006-10-29
You have to mount the remote Samba share in your local filesystem (as opposed to just going the Nautilus "Connect to server" route).  XMMS and other apps don't understand how to find the files except through the filesystem.

You can do this either via the "smbmount" command or by adding the shares to /etc/fstab.  I'd recommend the latter, since stuff mounted via smbmount will only stay mounted for the duration of your session.

---

