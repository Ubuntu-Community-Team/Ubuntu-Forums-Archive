---
title: "how to make an installation flash drive with FreeBSD?"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by Ubunser on 2010-02-22
Hi! I want to install FreeBSD system from an USB stick. I've no experience though. Do I have to format it first? If yes, what should I consider when choosing a file system? Then, what software should I use to write an image to an USB stick? Do I need to have additional boot floppy, or not? I'm sorry, if these questions in some ways concern FreeBSD, but lots of explanation they give looks to be meant for their sustem. Like, I often encounter a command that starts with dd.... And I have no idea what to do with this "dd". But how am I supposed to make a flash drive that you could use to install FreeBSD?

---

### Post by Ozymandias_117 on 2010-02-22
If your fairly new to Unix type systems I would try Pc-BSD if your set on using BSD, or try Ubuntu ;) Unfortunately, FreeBSD starts out with only a command line, so... if you want a GUI and aren't comfortable with the command line, you'll have problems.

---

### Post by Ozymandias_117 on 2010-02-22
Otherwise, the formatting section of FreeBSD uses fdisk commands.

---

### Post by Ubunser on 2010-02-22
I am already using Ubuntu. But I am determined to try FreeBSD for Apache.

---

### Post by mikeyphi on 2010-02-22
Not a simple procedure! 

Read here for info: 
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

and here for the bsd software:
[http://www.livebsd.com/](http://www.livebsd.com/)

Apache is available in Ubuntu, look via Snyaptic. Better still, install Ubuntu Server
[http://www.ubuntulinux.org/getubuntu/download-server](http://www.ubuntulinux.org/getubuntu/download-server)

---

### Post by Ubunser on 2010-02-27
I made a bootable flash drive with FreeBSD image by using ImageWriter :p I was happy to realise this util isn't useless crap but actually does what it says:D Good luck

P.S. To do this a special release of FreeBSD meant for memorystick is needed, it's available from their official site

---

