---
title: "noob: Breezy 5.10, help w/dialup for multiple users"
date: 2005-10-21
forum: Networking &amp; Wireless
---

### Post by NoDough on 2005-10-21
I'm new to Ubuntu and, I must say, very impressed.

However, I'm having trouble with dialup settings.  What I'm trying to do is get the Modem Monitor (or something similarly GUI) working for regular desktop users so they can connect and disconnect at will.

There appear to be two different dialup worlds in Breezy.

World 1) I've read the Howto and setup dialup using `**pppconfig**`.  The setup worked as advertised and, after adding dialup users, `**pon**` and `**poff**` will work with through a terminal with any user logged in.  Seems good. :)  But this doesn't really help me at the GUI level.

World 2) I've added the Modem Monitor icon to the panel.  Trouble is, no matter which user is logged in, the `**Activate**` option is grayed out, even after completing world 1 above.  So, I go into `**Properties**` and re-enter my dialup settings.  Viola'!  Now `**Activate**` is enabled.  However, when I use it with the administrative user I must re-enter the user's password for it to work.  When I use it from a regular user, it asks me for a password but refuses to work no matter which password I give it.

Any hints? :confused:

---

### Post by migueljacq on 2005-10-21
[QUOTE=NoDough]I'm new to Ubuntu and, I must say, very impressed.

However, I'm having trouble with dialup settings.  What I'm trying to do is get the Modem Monitor (or something similarly GUI) working for regular desktop users so they can connect and disconnect at will.

There appear to be two different dialup worlds in Breezy.

World 1) I've read the Howto and setup dialup using `**pppconfig**`.  The setup worked as advertised and, after adding dialup users, `**pon**` and `**poff**` will work with through a terminal with any user logged in.  Seems good. :)  But this doesn't really help me at the GUI level.

World 2) I've added the Modem Monitor icon to the panel.  Trouble is, no matter which user is logged in, the `**Activate**` option is grayed out, even after completing world 1 above.  So, I go into `**Properties**` and re-enter my dialup settings.  Viola'!  Now `**Activate**` is enabled.  However, when I use it with the administrative user I must re-enter the user's password for it to work.  When I use it from a regular user, it asks me for a password but refuses to work no matter which password I give it.

Any hints? :confused:[/QUOTE]

Your other users need to be on the 'sudoers' list. I'm at work and for the life of me can't remember what the path is to that list. Probably under /etc. Sorry :(

---

### Post by Azrael on 2005-10-21
This is how you give users more priviledges: [http://ubuntuforums.org/showthread.php?t=78180]("http://ubuntuforums.org/showthread.php?t=78180")

But I don't know if that's what you want. It's probably better to change the uid or gid of the program you're trying to use.

---

### Post by jamesstansell on 2005-10-21
[QUOTE=Azrael]This is how you give users more priviledges: [http://ubuntuforums.org/showthread.php?t=78180]("http://ubuntuforums.org/showthread.php?t=78180")

But I don't know if that's what you want. It's probably better to change the uid or gid of the program you're trying to use.[/QUOTE]
Before you consider those, I'd suggest giving gnome-ppp (from universe) a try.  Or reading about how to setup automatic dialing.

---

### Post by elebrin on 2005-10-21
to get a user on the sudoers list:

su into the root account
run sudoedit /etc/sudoers
add lines like the one already in there, just with the correct user ID.
hit ctrl^o to save, ctrl^x to exit if the editor is nano (I think... I use vi)

Can I ask what kind of modem you have? I have a friend in another thread who needs to get a dialup modem working, and they are willing to buy a new one if need be (for easier setting up).  The modem we bought is still returnable :)

---

### Post by NoDough on 2005-10-21
elebrin,

I'm using a Zoom external serial modem.  Breezy didn't detect it automatically, but I simply set the port to /dev/ttyS0, and it worked.

NoDough

---

### Post by NoDough on 2005-10-24
FYI, the accepted answer was the installation of gnome-ppp, which allows each user to initialize dialup/disconnect without giving the user sudo priviledge.

---

### Post by migueljacq on 2005-10-24
No that it matters but people might be interested in other ways of doing things:

In pppconfig, under 'Advanced Options' you can add users for turning on and off the ppp. 
I personally use this way, and run 'pon provider' from the terminal. I'm a CLI man :-)

---

