---
title: "creating smbmount launcher"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by teddmeister2 on 2007-02-12
I've got a linksys nslu2 attached to a 320 GB hard drive which it shares over my home network using samba.  I've had no problems using it, and use the smbmount command to mount the network share.  My question is about creating a launcher so that I can mount it simply with the click of a mouse.
(I considered making the mount run on boot up, but I use my laptop using different wireless networks throughout the day, so I want instead to be able to use the linux version of a shortcut to do it.)
The command I run in the command line is the following (with the names changed to protect the innocent):
sudo smbmount '//thedrive/ADMIN 1' /media/slugshare -o username=myusername,password=mypassword
This mounts the share nicely.
This is the same command that I tell the launcher to run, but nothing happens when I click it.

Appreciate it.

P.s. I've also tried unsuccessfully to give the command a simpler alias in my .bashrc, but I'm basically still a noob to linux and ubuntu, so I may have just done these wrong/followed howto's wrong or I may just not understand the system well enough, so any help would be appreciated.

---

### Post by teddmeister2 on 2007-02-12
Does anyone have any suggestions?????:-k

---

### Post by Boelcke on 2007-02-12
You could make a script file to run that command.  Make a text file that contains this:

```

#!/bin/bash
sudo smbmount '//thedrive/ADMIN 1' /media/slugshare -o username=myusername,password=mypassword
```

I use similar scripts to mount a number of different things.  The only drawback to what I just described is that I think you'll still have to type in your password, since you used a sudo.  Oh, and don't forget that you have to make it executable!  You can right click it in Nautilus and check the executable box, or some folks like the chmod 755 command.

Or, you can put this drive into your /etc/fstab file.  That's a text file that tells ubuntu what to mount on startup, basically.  If it doesn't find the drive, it'll just fail out.  As long as you don't mind the error message, who cares?

I won't go into the details of how to configure an smb drive in your fstab file (because I don't know of the top of my head!), but I'm sure you can find that advice written somewhere on here already.

---

### Post by teddmeister2 on 2007-02-12
Thanks so much for your help!!  I had tried the "write a script" option before and think I may have just not known that it required the #!/bin/bash line.  This works.  I may try the /etc/fstab thing sometime soon, but I'll just have to wait and see.  I always keep myself guessing.

---

### Post by Boelcke on 2007-02-13
I started using Linux and ubuntu full time about a year ago, so I have an idea where you're at.  That little detail helped me out -- now I script all sorts of things, which has been very empowering for me.

Yeah, that first line tells the system that it's a bash script.  There are a few other variations that look like that for other languages, such as a perl script.  It's a difference -- I was used to thinking in the DOS world where the file extension (*.bat) indicated what type of file it was.  This way, you can technically have any old extension you like, but that first line tells the system what it is.

Just don't forget to set the permissions to executable!

---

