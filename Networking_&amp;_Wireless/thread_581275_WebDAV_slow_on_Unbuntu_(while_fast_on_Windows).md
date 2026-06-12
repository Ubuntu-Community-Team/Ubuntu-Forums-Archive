---
title: "WebDAV slow on Unbuntu (while fast on Windows)"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by cbourbou on 2007-10-19
Dear all

Just upgraded to 7.10 and reevaluated a problem I also hit with 7.04 - it's still there.

Our company provides a central document server with a WebDAV interface. I have 2 notebooks side by side, one with Ubuntu 7.10 and one with Windows XP.

When I navigate the WebDAV folders from XP, the reaction takes 3 seconds or less.
With Ubuntu, it takes in average 50 seconds even for simple navigation, for instance navigating into a subfolder.

The server (I think) can be ruled out as the cause for the problem, since I have no problems accessing it from Windows.

Thanks for your ideas and feedback.
Tino

---

### Post by bburg on 2007-10-28
The same behavior here.  Anyone a solution?

---

### Post by PlancksCnst on 2008-01-15
Same problem here.  Dav is very slow, locks up nautilus and Firefox for minutes at a time.

---

### Post by satbunny on 2008-01-17
Same here, it has sucked since 6.04..
It's fine on OS X and XP, poo on Linux :mad:

---

### Post by rvarnam on 2008-01-25
Same here, with several different WebDAV servers - appallingly slow on Ubuntu.  Sadly, it's meant our department choosing not to consider a switch to linux

---

### Post by carpex on 2008-01-25
Same here. Completely unusable in Gutsy. 

Don't know if I did it at the right place, but I filed a Launchpad bug for this:

[http://bugs.launchpad.net/ubuntu/+source/davfs2/+bug/185986](http://bugs.launchpad.net/ubuntu/+source/davfs2/+bug/185986)

CP

---

### Post by geog_eric on 2008-01-28
Same problem. Waiting forever for the WEBDAV to connect. When it does, prone to crashing.

Eric

---

### Post by satbunny on 2008-02-04
Who is working on the code and where?

---

### Post by findus on 2008-02-24
Same problem here, sometimes it works (very slowly) otherwise it hangs the system requiring a reboot. It's a shame cos I hate having to use my Windows laptop, but its the only reliable way of getting access to my school resources.

---

### Post by Optimus Prime on 2008-02-27
I too have experienced this, and I've discovered that using davfs2 instead of the gnome-mount dav works at full-speed, and is just as easy to use once it's set up.

Install davfs2:
```
sudo apt-get install davfs2
```

Create mountpoint:
```
sudo mkdir /media/dav
```

Add your DAV share to fstab to mount as non-root user. As sudo, edit **/etc/fstab** and add the following line at the end:
```
https://example.com/yourdir /media/dav davfs rw,noauto,user 0 0
```

Now as a normal user, simply mount using:
```
mount /media/dav
```

Type your username and password and it's done!



To automatically mount the DAV share on system startup, replace "noauto" with "auto" in the line added to /etc/fstab
Then put your username/password in /etc/davfs2/secrets. As root, do:
```
echo "https://example.com/yourdir username password" >> /etc/davfs2/secrets
```

---

### Post by satbunny on 2008-03-01
Thank you..  shall try this.
I have raised the issue on the Ubuntu Brainstorm, can you vote for it?
It may be the fix is to change the standard Ubuntu build to use the davfs2 as default, but it needs fixing as a standard and working option, not something that has to be tolerated and either abandoned or fixed..

[http://brainstorm.ubuntu.com/idea/2196/](http://brainstorm.ubuntu.com/idea/2196/)

---

### Post by satbunny on 2008-03-03
Ok.. problems as follows:

> [https://webfolders.ncl.ac.uk/mmme/New%20Rail/](https://webfolders.ncl.ac.uk/mmme/New%20Rail/) /media/NCLnewrail davfs rw,noauto,user 0 0

The I try to mount as normal user:

> thomaszunder@Dell:/media$ mount /media/NCLnewrail/
/sbin/mount.davfs: program is not setuid root


So I try as sudo

> /sbin$ sudo mount /media/NCLnewrail/
Please enter the username to authenticate with server
[https://webfolders.ncl.ac.uk/mmme/New%20Rail/](https://webfolders.ncl.ac.uk/mmme/New%20Rail/) or hit enter for none.
Username: [foobar]
Please enter the password to authenticate user ntz2 with server
[https://webfolders.ncl.ac.uk/mmme/New%20Rail/](https://webfolders.ncl.ac.uk/mmme/New%20Rail/) or hit enter for none.
Password: 
/sbin/mount.davfs: Mounting failed.
500 ( The request was rejected by the HTTP filter. Contact your ISA Server administrator.  )


So no joy. I can mount using the normal gnome DAV, but it is narcaleptically slow and unreliable.

Any help? Ideas?

---

### Post by satbunny on 2008-03-03
The I followed the steps here:

[http://www.howtoforge.org/davfs_ubuntu]("http://www.howtoforge.org/davfs_ubuntu")

Which got me logged in to a different DAV folder but not the other, it also creates a config file that then start to error up the whole process until you go in and comment out the user settings.

I did that (the error tells you the file) and stil I get

> 500 ( The request was rejected by the HTTP filter. Contact your ISA Server administrator. )

---

### Post by Eothred on 2008-07-08
I have had problems with webdav as well. I have used automounting of the server using davfs2, but now I have problems writing to the server. I have best experience with the webdavs:// kio-slave in konqueror. Compared to nautilus this is quick and responsive, and seems trustworthy enough. Davfs2 was easier to use (could mount the server as a folder in home, which I liked), but not possible to trust anymore it seems. 

Aren't webdav opensource?? Don't understand why this should be so difficult, when they manage to get it to work on other platforms...

Anyway, just wanted to mention the kio-slave option in konqueror. Just type in webdavs://your.server/your/folder and it prompts for username and password.

---

