---
title: "Playing media over network"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by mabris on 2007-02-05
I can access my windows network just fine through my Edgy box.  It's set up in the same network domain; i can browse shared files on my windows box and can copy files onto my Edgy box.  The problem I'm having is in trying to play media files (mp3, mpgs...) directly from the network shares.  If I copy a file and play it locally, it plays fine.  If I try to play the file from the network, though, the player acts like it is an empty file (0:00/0:00 time bar, etc...)

This works fine in a windows-windows setup, so i know the network is up to it.  What could be the problem?  I want to try to get this working before point Mythtv to the network shared drive for media.

I have Samba installed and configured correctly (I believe...)

---

### Post by mabris on 2007-02-05
OK, i think i've gotten it working by mounting shared folder.  Now I just need to get it to mount automatically at login.

This works to mount it once:

mount -t smbfs //acer/D media/windows

But putting the following line at the end of /etc/fstab doesn't do the trick:

//acer/D media/windows smbfs rw


any ideas?

---

