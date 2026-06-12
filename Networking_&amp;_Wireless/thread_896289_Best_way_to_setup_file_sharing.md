---
title: "Best way to setup file sharing?"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by aesop12 on 2008-08-21
Hey guys,

I'm developing a Rails application on my local network. I have a Ubuntu Server that runs the rails application through Apache; and a Microsoft XP client that I want to write the code.

The problem is that i want to edit code directly on the server. Is the best way to do this via Samba, NFS, FTP or something I am missing?

Cheers guys.

Luke

---

### Post by Iowan on 2008-08-21
SSH via PuTTY? Probably not exactly what you wanted - you probably want to edit on XP, then save TO the server?

---

### Post by bab1 on 2008-08-21
Why not write the code at the Ubuntu server.  If you have a GUI interface.  I would use Bluefish (very dreamweaver (code) like).  There are others, I just like Bluefish.  If no GUI, then I use vi.  There is also emacs, and for GUI there is Xemacs.  If youhave to write the code from XP, then I would FTP the files to the server, as Dreamweaver does.  If you use ssh you will be at a command line and will end up using the above mentioned non GUI editors.

---

### Post by Paul41 on 2008-08-21
FTP is easy to set up but can be kind of a pain because before you can see and of your changes you have to FTP the files over to the server. I would try Samba.

---

