---
title: "Network share issues."
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Waste on 2008-09-25
I am currently running three Ubuntu boxes in my home.
Been having issues with my network shares either not working or not even showing up at all.
Are there any guides to setting up a proper home network with reliable network shares and/or could someone give me a hand with this?
I'm decently versed in Linux, but Samba seems to always give me trouble.

All three PCs are running the same version of Ubuntu and Samba.
They are all hooked up to my Linksys router, two wired, one wireless, and I have no issues running remote desktop with them so I'm sure it's not a connection issue.
They also each have their own hostname.

Any help is greatly appreciated.

---

### Post by Waste on 2008-09-26
Bump.
Any help on this at all, I've looked around on Google a ton and nothing really gives me much help as it is mostly posts/guides about fixing problems between XP/Vista and Ubuntu.

---

### Post by Iowan on 2008-09-26
Realize that there are options besides Samba to share files between Ubuntu machines (NFS and SSHFS).  Otherwise, it *may* help to install Winbind, and edit nsswitch.conf.
[Here]("http://ubuntuforums.org/showthread.php?t=891876") is a thread with (hopefully) some useful information.

---

