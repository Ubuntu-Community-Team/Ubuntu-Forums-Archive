---
title: "How to make link to samba share on server??"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by rado3105 on 2008-06-11
How to make link to samba share folder smb:/192,168.1.1/media/X to be on desktop after restart or how to automount that share folder after restart using fstab??
That samba share is anonymous no password and no login, it is on local network.

---

### Post by Audiosears on 2008-06-11
rado,

one thing you can do on the desktop is head to the 'places' menu and choose 'connect to server'.  You can then put in one of many remote shares (i.e. ftp, win share, etc) with the address and sharename.  You should then be prompted for a password (and keyring if applicable), and once authenticated, it will behave much like a mapped drive in windows.  There should be an icon for that location in your 'places' menu from then on, and you can drag it to the desktop for easy access.

For a samba share, you should be able to use the 'windows share' option.  I have one of these mappings I use to dump stuff to a windows server share on another system.

---

