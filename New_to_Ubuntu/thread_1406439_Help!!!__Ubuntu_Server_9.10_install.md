---
title: "Help!!!  Ubuntu Server 9.10 install"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Down_with_Windows on 2010-02-14
Ok, so I am new to Ubuntu, but found it to be much faster and less headache than Windows has ever been.  I installed 9.10 on my Toshiba Laptop and liked it so much I had to load it on my old desktop PC.  It was a custom built system that I used for games years ago, and with a new hard drive, it works great.  Here is where the problems start, and I am no programmer so please try and keep your replies on the idiot level for me.  I wanted to set up the desktop PC as a print and mail server, and after reading on line how it could be done, I loaded the 32bit version of 9.10 server, and now, I cannot get past the user@ubuntu-server:~$.  I do not know what to do here.  I set up my user name and password, but when I log in, there is no graphical interface.  Can someone please help me, and I do apologize for my lack of knowledge.  I had the system working great for a common file and print server, but wanted to setup email.  Now I am at what appears to be square one again.  I will likely be reinstalling Ubuntu 9.10 again and giving up on the server edition if I cannot make any headway.

---

### Post by running_rabbit07 on 2010-02-14
If you want the Ubuntu Desktop Environment just enter this command. ```
sudo apt-get install ubuntu-desktop
``` I will warn you though, when you do this it will have to download more than 1200MB. There are other ways people get the GUI going on the Server Edition, but that is the way I did mine.

---

### Post by 3rdalbum on 2010-02-14
Ubuntu Server does not contain a GUI. You can install the "ubuntu-desktop" package to get a regular desktop:

```
sudo apt-get install ubuntu-desktop
```

It shouldn't download more than 700 megabytes.

Mathematical equation for you: Ubuntu Desktop - GUI = Ubuntu Server. In other words, you can install file and print servers on the desktop edition.

---

### Post by Down_with_Windows on 2010-02-14
Ok, so the server setup will not recognize my network cards at all, so I have no way to establish a network connection, or load the Ubuntu desktop, is there a way around this?  You guys are great, I can't believe I already have gotten responses.

---

### Post by d3ngar on 2010-02-14
Sure, you can download ubuntu dekstop from the ubuntu.com site. You can install this from a memory stick...

But you don't have a graphical browser either, ey?

Try this:
wget [http://releases.ubuntu.com/releases/karmic/ubuntu-9.10-desktop-i386.iso](http://releases.ubuntu.com/releases/karmic/ubuntu-9.10-desktop-i386.iso)

Let me know if this works... not sure if this is the right URL for you.

Next you can install it from a 1 GB mem stick. Here is a documentation:

[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")


Or you have to burn it to a disk.

But I have my doubts the drivers would be bundled in the desktop version if you can't find them in server.
What card is it, do you know? - Try: lspci

Best of luck though!

---

