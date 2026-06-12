---
title: "Cant install printer software"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by mrakbrown on 2009-01-09
i just installed Ubuntu.....so far so good...however, for some reason my printer does not work now....i've tried to install the software that comes with the printer(Canon PIXMA iP1800), but instead of the software running as it would in Windows, several folders appear...can anyone help....THANKS

---

### Post by ValRoss on 2009-01-09
Same problem here, when running the CD I can find the pacage, but get the message: 

Could not open "Xerox-Phaser-6180-1.0-1.noarch.rpm"

Archive type not supported.

If I have to open terminal I need detailed instructions as I am an inexperienced Linux user!

---

### Post by mrakbrown on 2009-01-09
Yeah, i'm new to Linux as well...also cant open CD's with pics on them...keeps saying something about volume...what the hell does volume have to do with pictures?

---

### Post by taurus on 2009-01-09
You need to use alien to convert the .rpm to .deb before you can install that file.

```
sudo apt-get install alien
sudo alien Xerox-Phaser-6180-1.0-1.noarch.rpm
(Assuming you are in the directory where that file, Xerox-Phaser-6180-1.0-1.noarch.rpm, is.)
sudo dpkg -i Xerox-Phaser-6180-1.0-1.noarch.deb
```

---

### Post by oldos2er on 2009-01-09
> **mrakbrown said:**
> Yeah, i'm new to Linux as well...also cant open CD's with pics on them...keeps saying something about volume...what the hell does volume have to do with pictures?

 Can you please post the full error? "Volume" in this instance refers to devices (e.g. a CD) or partitions.

---

### Post by ValRoss on 2009-01-09
> **taurus said:**
> You need to use alien to convert the .rpm to .deb before you can install that file.

```
sudo apt-get install alien
sudo alien Xerox-Phaser-6180-1.0-1.noarch.rpm
(Assuming you are in the directory where that file, Xerox-Phaser-6180-1.0-1.noarch.rpm, is.)
sudo dpkg -i Xerox-Phaser-6180-1.0-1.noarch.deb
```

Seems the first part worked well. The Xerox file is on a CD, do I have to copy the file file to the harddisk before I can continue? And remember, detailed steps please!

---

### Post by oldos2er on 2009-01-09
> **mrakbrown said:**
> i just installed Ubuntu.....so far so good...however, for some reason my printer does not work now....i've tried to install the software that comes with the printer(Canon PIXMA iP1800), but instead of the software running as it would in Windows, several folders appear...can anyone help....THANKS

 Try the menus System, Administration, Printing, and see if you can setup your printer. Windows drivers aren't going to work on Linux.

---

### Post by shifty_powers on 2009-01-09
btw, if you want to learn more about ubuntu, go to

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

a fantastic resource for people new to ubuntu...

---

### Post by taurus on 2009-01-09
> **ValRoss said:**
> Seems the first part worked well. The Xerox file is on a CD, do I have to copy the file file to the harddisk before I can continue? And remember, detailed steps please!

```
cd /media/cdrom0
cp Xerox-Phaser-6180-1.0-1.noarch.rpm ~/Desktop
cd ~/Desktop
alien Xerox-Phaser-6180-1.0-1.noarch.rpm
sudo dpkg -i Xerox-Phaser-6180-1.0-1.noarch.deb
```

---

### Post by ValRoss on 2009-01-18
Have now managed to copy the file to the desktop, but this is the return for the last part:

arne@ubuntupc:~$ alien Xerox-Phaser-6180-1.0-1.noarch.rpm
Must run as root to convert to deb format (or you may use fakeroot).
arne@ubuntupc:~$ 


Solutions please?!

---

### Post by oyvindaa on 2009-01-18
> **ValRoss said:**
> Have now managed to copy the file to the desktop, but this is the return for the last part:

arne@ubuntupc:~$ alien Xerox-Phaser-6180-1.0-1.noarch.rpm
Must run as root to convert to deb format (or you may use fakeroot).
arne@ubuntupc:~$ 


Solutions please?!

sudo alien filename.rpm

When that's done you just do:

sudo dpkg -i filename.deb

---

### Post by bailbath on 2009-01-18
> **ValRoss said:**
> Have now managed to copy the file to the desktop, but this is the return for the last part:

arne@ubuntupc:~$ alien Xerox-Phaser-6180-1.0-1.noarch.rpm
Must run as root to convert to deb format (or you may use fakeroot).
arne@ubuntupc:~$ 


Solutions please?!
This command is running as you the user
arne@ubuntupc:~$ alien Xerox-Phaser-6180-1.0-1.noarch.rpm 
This command is running as the super user or root user it will ask for your password
arne@ubuntupc:~$ sudo alien Xerox-Phaser-6180-1.0-1.noarch.rpm

As this is a admin action it has to be run as super user or root. This is a security consideration and you will get used to doing it.
Ian

---

### Post by ValRoss on 2009-01-19
Well guys, it works fine now, both wired and wireless! I must admit that I did not fully understand what was going on at all times, but the step by step instructions you provided did the trick! THANK YOU!

---

### Post by halitech on 2009-01-23
for the future, instead of running through the hassle of finding the rpm file and having to convert it, why not download the driver from the xerox website?

[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=6180&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=6180&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=)

just simply download the file, extract it and then run through the add printer applet and browse to where you extracted the files.

---

