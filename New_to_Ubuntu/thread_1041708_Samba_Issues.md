---
title: "Samba Issues"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by emarkd on 2009-01-16
Hello all.

I'm having issues getting samba to behave.  The host in question is an Ubuntu 8.10 box and it's computer name is 'tesseract'.  I'm trying to browse it from an XP box.  If I use the "network places" bit in XP to browse the network, I see the server, but it shows up as 'Tesseract.' When I double-click 'Tesseract' from Windows, I get a "network path not found" error.  If I type '\\tesseract' into the address bar, I get the same error, but if I use the IP and type '\\192.168.1.101' everything works great.  Why can I browse the computer based on IP and not on computer name?

Here's the output of running testparm:

```

[global]
	server string = 'Tesseract'
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[media]
	comment = Shared Media
	path = /home/mark/Documents/media
	valid users = mark
	create mask = 0770
	directory mask = 0770
	guest ok = Yes

```

I filled in the 'server string' bit hoping it would help with the capitalization, but it doesn't make any difference.  If you need something else, let me know.  Thanks!

---

### Post by JoshuaRL on 2009-01-16
I noticed this too, but hadn't tried the IP address.  But I did find a workaround though.  When in the Map Network Drive dialog, do several things.  First, change username and password to what you want it to be.  Then, browse for your share.  Mine is under:
```

Microsoft Network
* LXHOME
* * servername
* * * sharename

```
But at first, it wont show anything after LXHOME.  So I right-clicked it and chose Explore.  It asked for a Username and Password, then allowed me to browse in Explorer.  So I closed Explorer and retried the Browse option to find the share.  And it was there.  So just make sure it autoconnects at startup and you should be good.

At least, that is what worked for me.  It was almost like Windows wanted me to find the share I was trying to find before I authenticated myself.  Weird.

---

### Post by emarkd on 2009-01-16
Well, it's clearly been a long time since I used Windows.  I never considered adding a network drive map.  That actually solves my problem since my wife can now access the media server from her laptop without having to type in an IP address by using a mapped drive instead of the network browser.  So thanks for that!

But my original problem is that using the network browser in Windows Explorer shows the server, but then can't seem to connect.

---

### Post by JoshuaRL on 2009-01-16
Try that exact series of steps I outlined.  It seems really dumb, I know.  But its the only thing that worked for me.

[list]
Open Map Network Drive Dialog
Change username and password to what is needed
Browse to correct workgroup
Explore workgroup
Enter correct username and password AGAIN
Close Explorer
Browse to share
Finish Map
[/list]

---

### Post by emarkd on 2009-01-16
Maybe you didn't understand.  Mapping the share to a drive letter works fine and then she can browse the network share through the drive letter.  Simply browsing to the share using the network places widget is what doesn't work - at least not without typing in the IP address.

I've got no issues mapping the share to a drive in Windows.  Thanks for your help because I hadn't even considered that.

---

### Post by JoshuaRL on 2009-01-16
> **emarkd said:**
> Maybe you didn't understand.

Apparently not, sorry dude.  And is she on Vista?  I could never get the network places thing working right.  I just use the My Computer place to get to it, unfortunately.

---

### Post by Kellemora on 2009-01-17
Hi emark

I didn't see a line that said the name of your WORKGROUP.

In Samba the default is WORKGROUP = WORKGROUP

If you didn't make a workgroup in windows, I think the default is MSHOME, so you would then have WORKGROUP = MSHOME in your smb.conf file.

MSHOME would of course be replaced with the name of your Workgroup if you did in fact assigned one.

If you are running the Ultimate Spyware OS known as VISTA, you may want to UPGRADE to Windows XP-Pro or Windows 7 if it's available yet.

TTUL
Gary

---

### Post by emarkd on 2009-01-18
Thanks again for all your suggestions.  Mapping the drive letter continues to work fine for her purposes.  And yes, she's using XP.  I thought of the workgroup issue as well, so I made sure to change her laptop to the workgroup "WORKGROUP", but it didn't help except to make discovering the server on the network faster.  It shows up fine, but you can't click on it to browse it.  Oh well, at least we've got something usable going.

Windows 7 is out in beta, by the way, and I've tried it.  It seems ok so far.  I'll never use it for my primary os, but it may find a permanent home on my xp box.  We'll see.

---

### Post by Kellemora on 2009-01-18
Hi ear

Besides Samba, make sure you have smbclient installed, and I would install smbtree also.

If you have smbfs installed, uncheck it so it gets removed or turned off, it blocks some shares from showing.

And FWIW:  There was a bug in Nautilus for 2 years or more that I think they may have finally got fixed.  At least it works on my machines since the last update of the Samba and Networking packages.

If you can see all of your shares in smbtree, both Samba and Networking are functioning properly.
That Don't mean you will be able to see those shares in Nautilus all the time.  Works about 3 to 4 days, then takes a day or 2 off, then works again.  But as I said, that got fixed a couple of weeks ago, finally.  Maybe it's not all the way fixed yet?

One trick that has worked for me in the past was to reboot my Ubuntu machine three times in quick succession.
I did this to force smb.conf to be written into the var/lib/samba configuration file, which is a binary and not editable by us humanoids.  THAT'S the file Samba reads for it's configuration when you boot up once.  If you boot twice, it thinks Hmmmmmm, wonder why he did that, maybe I should look at smb.conf, which it does on the second boot.  If you reboot again a third time, it will make the changes that appear in smb.conf into the /var/lib/samba configuration file.
It probably don't actually work that way, but that's how it appears to work to me!

TTUL
Gary

---

