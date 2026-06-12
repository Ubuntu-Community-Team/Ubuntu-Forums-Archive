---
title: "Offline File Synchronisation with Samba possible in Ubuntu?"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by MidBSD on 2007-10-10
There are a few threads similar to this one but my requirement is a bit more specific.

Windows has a feature called Offline File Synchronisation for files that are available on the network. In XP I just right-click and 'Make files available offline' and it basically makes a copy of those files available without network access. When I re-connect to the network it synchronises the files for me.

In Ubuntu I'm currently having to copy the entire directory and copy it back once I finish with it.

Ubuntu is already able to make use of SMB shares - is it able to 'make files available offline' (e.g. in Nautilus)? If not, am I pretty much stuck with rsync or, the now un-maintained, Unison? Ideally I'd like the system to be foolproof because I'm converting my girlfriend's laptop to Ubuntu too and I need to keep it really, really, really simple or I'll have to re-install Windows.

Ideally I'd like to stick with what's already installed in the Ubuntu core install. Have I overlooked something somewhere or will I need to install extra software?

---

### Post by terryeden on 2007-10-16
Bump!

Anyone know how to do this?  Setting up Samba to see another share was very easy - what I would like is a way to make shared files available when the host is offline.

I'd prefer not to install anything on the (Windows) host.

---

### Post by terryeden on 2007-10-17
I've found two ways to do this.

1) Set the Ubuntu box as the server.  So, place all of the files on the Ubuntu Desktop in a folder called "Bob's Files".  Share the folder.  On the Windows box, map the network drive to "Bob's Files" and set to make available offline.

2) Use [http://www.ifolder.com/index.php/Main_Page](http://www.ifolder.com/index.php/Main_Page)

HTH

T

---

