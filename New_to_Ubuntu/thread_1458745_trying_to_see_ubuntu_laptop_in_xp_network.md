---
title: "trying to see ubuntu laptop in xp network?"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by kapi on 2010-04-20
Hi, followed several tutorials from youtube in relation to installing samba and accessing files from my ubuntu laptop on to a works laptop.

I cant seem to see ubuntu on xp anywhere

can you help

---

### Post by cariboo on 2010-04-23
When you run **smbtree** in a terminal do you get a similar output to this:

```
smbtree
Enter my password: 
APLUS
	\\WILLY          		willy server (Samba, Ubuntu)
		\\WILLY\IPC$           	IPC Service (willy server (Samba, Ubuntu))
		\\WILLY\Images         	iso images
		\\WILLY\Iso            	Mounted iso's
		\\WILLY\Stuff          	Everything Else
		\\WILLY\Documents      	Documents
		\\WILLY\Music          	Music
		\\WILLY\Movies         	Movies & TV Shows
		\\WILLY\print$         	Printer Drivers
	\\RISKY          		XP Computer
		\\RISKY\C$             	Default share
		\\RISKY\ADMIN$         	Remote Admin
		\\RISKY\EPSONSty       	EPSON Stylus Photo R340 Series
		\\RISKY\All Users      	
		\\RISKY\SharedDocs     	
		\\RISKY\print$         	Printer Drivers
		\\RISKY\IPC$           	Remote IPC
```

You can see from the above example that "willy" is running Ubuntu and "risky" is running XP.

---

### Post by archkidd on 2010-04-23
I am a newbie having had ubuntu 9.10 for about 10 days now, but I run my ubuntu laptop within an xp network.  I confess that I did nothing (I did add the restricted-extras and the medibuntu package)  The laptop is wireless and when I go to Places and go to 'network' my other xp computers show up.  In my xp computers, when I go into the explorer and go to 'My Network Places/Entire Network/Microsoft Windows Network/workgroup' there is my ubuntu laptop.  It is just as everybody says with ubuntu, too easy.  I dont even know what samba is.  I don't know that this helps you but I can tell you that it works.

---

### Post by anewguy on 2010-04-23
It might also be that the domain name you have for Windows (MSHOME??) doesn't match that in Samba.

Dave ;)

---

