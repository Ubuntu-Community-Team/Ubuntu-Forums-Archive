---
title: "removing samba and libsmbclient"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by MaXqUE on 2007-02-07
Hello:

I have just installed Unbuntu with no problems. However, I notice that Samba is installed by default. Since my other OS is Mac OS X, I have no need for Samaba. I've removed samba using apt-get remove samba smbclient. That was no problem.

However I noticed libsmbclient being updated when I ran apt-get upgrade. When I went to remove libsmbclient, apt informed me that it would also be removing gnome-cups-manger, gnome-cups-utils, mozilla-pluggin-vlc, vlc and vlc-nox. Reason: I wouldn't need them if I removed libsmbclient. Also that I should remove things like libiso9660 and a whole host of other libraries since I wouldn't be needing them.

Is this some kind of apt dependency insanity? Why are things like the ISO CD standard so intimately connected with libsmbclient? The same question about VLC.

I get no real answers from apt-get describe, other than it is needed for SAMBA and CSIF -- I already knew that. 

What's up.... how  do I deal with this?

Cheers, 
MaXqUE

---

