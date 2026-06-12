---
title: "Need help on making user and managing rights on folders."
date: 2010-04-01
forum: New to Ubuntu
---

### Post by neviltis on 2010-04-01
Hello i am kinda new there so i need some help if anyone can help ofc.
Situation. In company i have runing server on linux. There is folders that is shown when you logon from any pc to server. There is users that can accsees certain folders. Now i need to create 1 new user and 1 new catalog for that user. And allow for that user to accses his new folder and folder it is avalible for all users. Question how to do that.

I can log to server by using putty. Hope to get some answers soon. If you can help but need some more info tell and i will try to write.

---

### Post by Chesamo on 2010-04-01
```
mkuser USERNAME
```

---

### Post by neviltis on 2010-04-01
Well still need folder comand and acses rights.

---

### Post by Chesamo on 2010-04-01
```
man chmod
man chown
```
How long has this server been operational? Can't have been that long if the sysadmin doesn't know the Terminal commands. (Nothing against you, I just have a problem with companies that set up a system then depend on a single person to get the job done; when that guy leaves, no one knows how to run the server!)

---

### Post by neviltis on 2010-04-01
Well it was operational for year or so. And 1 moth ago guys who was doing all stuff disapeared. And now i have to do it my self :( And i have to do all. Thank yu for you help but as far i am very very new there just comands don't help me to much.

---

### Post by Chesamo on 2010-04-01
Ah, so it's exactly as I feared. Don't worry, we're here for you!

Do the users need read/write permissions, or just read? Also, should users *not* be able to write to/delete from the directories?

---

### Post by neviltis on 2010-04-01
Now i need to create 1 new user " lina " with any password. Then create directory called " linos " were only she can acses and do there whateva she likes. 
There is 8 other folders. And only to 1 she can have acses. " bendras ". There she can do anything to. Read, write, delete etc.

---

### Post by Chesamo on 2010-04-01
It sounds like the type of scheme you want is:
[LIST]
[*]Multiple users
[*]Each user has their own Home directory
[*]Each user can also access one shared folder
[/LIST]
Ubuntu already has a system in place for the first two: Whenever you create a new user, a folder under /home is created with their name attached to it. Additionally, creating the second system is as simple as making the owner of the folder "bendras" a group of your choice, then adding each user to that group. After that, you give the folder (and its contents) the u+rw flag through chmod.

Is this on a single computer, or is this a network of computers?

In all honesty, it's a lot easier to set up this system if you know exactly how it works from the outset.

---

### Post by neviltis on 2010-04-01
Well it is server and 4 other pc's. All user of pc already have folders they can acses in server. Now i just want add one more user. And give that user rights to see one folder everyone sees.

I hope you understood what i mean.

---

### Post by Chesamo on 2010-04-01
Argh, now you're into network sharing and things I am extremely inexperienced with.

How is the network set up? NFS, Samba, LDAP?

---

### Post by neviltis on 2010-04-01
As i understand it is in this way. Server conects to wireles accses point. All pc's conects to it by wireles. As far i know in server there is samba isntaled for sure. And if recon corectly it is some other stuff to.
Now it is like this user from pc x conects to server //<servername>  security bar pops pc x user gives his login/pass and it is allowed to see all folders in server. But can acses only he is allowed. Almoust in all cases 2 folders his own and " bendras "

---

### Post by Chesamo on 2010-04-01
....It sounds like you're using Windows, not Linux.

Or, rather, you have a Linux server and a Windows client. Do I understand this correctly?

---

### Post by neviltis on 2010-04-01
yes linux server and windowses on users pc's

---

### Post by neviltis on 2010-04-01
So anyone ? If what i am on skype donceka aka varnas

---

### Post by neviltis on 2010-04-05
Still need help plzz

---

