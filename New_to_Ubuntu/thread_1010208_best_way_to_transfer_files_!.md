---
title: "best way to transfer files ?!?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by jackofallammo on 2008-12-13
I have a computer with xp pro, and ive installed ubunta on this one, im looking for an easy way to transfer 20 gigs of files from the xp machine to this one


trying to install aim is a real pain in the ***.. and i would like to use a IM, but im open to anything as long as its fairly simple


thanks,

    jack

---

### Post by Tyke91 on 2008-12-13
easiest way to transfer those files between computers - portable hard drive or usb memory stick.


use pidgin. much easier than installing AIM :)

you should be able to find pidgin in Applications>Internet

It can IM chat with people on AIM, Yahoo, GTalk, MSN, and whatever else you want.

---

### Post by adaptr on 2008-12-13
The easiest way to share files with a Windows machine is to configure Samba, alos known as Windows file sharing.
This should be doable right from the menus.

---

### Post by jackofallammo on 2008-12-13
at first i tried to use pigdin, but im pretty sure it wouldn't let me send files across using it..


and i have a usb drive.. but im trying to move 26 gigs of stuff..

---

### Post by Michael.Godawski on 2008-12-13
A little bit of reading but you will surely find the right thing here:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
or use some dvd-rw.:p

---

### Post by Tyke91 on 2008-12-13
actually, samba is the easiest way if they are on the same network. :p

[http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)


pidgin does indeed do file transfers.

---

### Post by jackofallammo on 2008-12-13
ok, i used pigdin.. and the problem is that for some reason i can't send a directory to my Ubuntu machine

---

### Post by albinootje on 2008-12-13
Much easier than samba, in this case, is to install ssh on the Ubuntu machine.
Then install winscp (from winscp.sf.net) on the xp-machine, and start copying right away.

---

### Post by Kellemora on 2008-12-13
Hi Jack

We're moving files around the office all day long using Samba!

There is one little hitch though that we avoid by doing it a certain way.

If we PUT a file from computer A ONTO computer B, often the permissions will get messed up.  Meaning the files have locks on them when opened on computer B.

To avoid this, we never PUT a file onto another computer.  Instead we FETCH the file from computer A using computer B, save it on computer B, then all permissions stay intact and NEVER mess up on us.

Don't know if it's a bug, some setting we have wrong, or whatever.  We just learned never to PUT, only to FETCH and it eliminated the problems, so thats the way we do it.

However, that being said, we have a master file (not a server yet) that does NOT give us this problem.  Just one computer loaded with drives where we keep most of our data.  I think the folders are somehow made to change all files put into it to the correct permissions.  But I don't have enough Schmartz yet to know why that works and to other computers don't.

Oh, one last thing, if you cut n paste to save, the files get new Creation Dates, instead of just Modification dates for some reason.  That's still bugging me too, although it's not that important to us on some things.  On others its very important.

TTUL
Gary

---

