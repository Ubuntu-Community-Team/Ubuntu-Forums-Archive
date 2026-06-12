---
title: "How do I share only one folder over my linux network?"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by AndyCat on 2007-07-18
Hello there. Im using linux on my 5 computers now. I have set the samba config so i can share folders to my xp computer. the problem im having is that I dont know how to share only one folder (i.e Shared Docs) I have the folder created and I told linux to share that folder but instead it is sharing my whole /home folder over the network. I dont want this to happen coz I only want to have one folder to share files and not my personal files runnin around every coputer o my network..

How do I fix this?????

Thanks in advance for your comments

---

### Post by ugm6hr on 2007-07-18
Is the SharedDocs on a Ubuntu machine?  

If so - just go to System->Shared Folders:
Click Add - go to correct path for SharedDocs (double-click on folder).

Works on my Xubuntu7.04 machines without a problem.

---

### Post by movrshakr on 2007-07-18
"System->Shared Folders:
Click Add - go to correct path for SharedDocs (double-click on folder)."

Chiming in...Did that, but it only lets me select "host" for the to-be-shared thing.  I want to select a sub-folder on the host filesystem (Windows)--not the whole host.  However, it does not provide for a drill down to the folder to select..."host" is just it. 

Specifically I want to share to the network a folder which appears in Windows as C:\Public, a sub-folder at the root of the main partition.  

I am running wubi-ubuntu--not running out of a separate partition install of ubuntu.

What am I missing?

---

### Post by ugm6hr on 2007-07-19
> **movrshakr said:**
> I am running wubi-ubuntu--not running out of a separate partition install of ubuntu.

What am I missing?

Probably the wubi issue.  

Afraid I don't know anything about wubi - maybe try asking on the wubi forum section, and perhaps best to mention wubi in the post title.

---

### Post by movrshakr on 2007-07-19
Sorry, I thought wubi was just an installer...that what you ended up with after install was ubuntu.

---

### Post by movrshakr on 2007-07-21
Following up on that...

So, when you install wubi-ubuntu, do you end up running ubuntu, or something else?

---

### Post by movrshakr on 2007-07-31
So, when you install wubi-ubuntu, do you end up running ubuntu, or something else?

---

### Post by movrshakr on 2007-12-14
It is now December 2007, and I have made the move to ubuntu desktop on the machine I was referring to.

I need some simple specific steps to finish the sharing setup.

I have a folder in my home directory--let's call it STORAGE.  I wish to share that folder to all other machines on the network--all are Windows machines.  I want the STORAGE folder to be RW and for Windows users to be able to create folders and files within the shared folder.

I have installed samba, samba client, and smbfs; I changed smb.conf to "security = share" authentication rather than "security = user".

Apparently more is needed.  What?  e.g., Where do I tell the ubuntu machine which folder to share to the net?  Else?

Please be specific, for example, not "you need to give everybody permission" but "open the XXX file located in /sssss/dddd, find the line _______, change what reads as hhhhhh to read gggggg."

I think I am close, but just haven't got the last tweak.

---

### Post by movrshakr on 2007-12-14
Hmmmm... in the last seven hours, I have solved some things, but am not there yet.

I did some editing in the smb.conf file, and created a new share point with these lines:
[STORAGE]
#above is name of the folder to be shared 
  path = /home/myusername/STORAGE
  read only = no
  writable = yes

After doing this, in Windows machine Networks, I can see the ubuntu computer, but when I try to "open" it to see the STORAGE share point, it pops up a login box.  I enter my username and my password (for the ubuntu computer) and it says logon unsuccessful - be sure name and password are correct.  They are.

I don't want it to even ask for logon to the share.  What needs to be different in the smb.conf?  (I used the one there from the samba install, and modified it to add my lines for the new share.

---

### Post by ugm6hr on 2007-12-15
Which version of Ubuntu are you using?

This might help get you started: [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

It is very easy to share a folder - and a simple tick-box allows you to make it read or read-write.  Perhaps the problem is the WINS server issue?

---

### Post by movrshakr on 2007-12-15
> Which version of Ubuntu are you using?

    7.1 Gutsy Gibbon desktop

> This might help get you started: 
> [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

According to the first message there, that thread is about XP/samba.  The word Vista is not mentioned anywhere in the thread. 
The problem is that VISTA doesn't want to play with samba.

> It is very easy to share a folder - and a simple tick-box allows you to make it 
> read or read-write. Perhaps the problem is the WINS server issue?

a.  If I am not mistaken, the GUI turn on of sharing only shares the folder to other Linux machines, no?
b.  Not using a WINS server.

---

### Post by movrshakr on 2007-12-15
Well, I was wrong about a. above.  The sharing facility in the folder manager does supposedly turn on smb sharing.  So I did it.

Great, now, the share point has disappeared from the network folder on the Vista machine (I did have it there before--but got the login request that always failed when trying to open the share).

A step backward.

So I still need to know how to see a samba shared folder from a Vista machine.

As an aside, does anyone know what ubuntu is really doing when you tell it to turn on a share in the folder manager?

---

### Post by biodoc on 2007-12-15
> **movrshakr said:**
> Hmmmm... in the last seven hours, I have solved some things, but am not there yet.

I did some editing in the smb.conf file, and created a new share point with these lines:
[STORAGE]
#above is name of the folder to be shared 
  path = /home/myusername/STORAGE
  read only = no
  writable = yes

After doing this, in Windows machine Networks, I can see the ubuntu computer, but when I try to "open" it to see the STORAGE share point, it pops up a login box.  I enter my username and my password (for the ubuntu computer) and it says logon unsuccessful - be sure name and password are correct.  They are.

I don't want it to even ask for logon to the share.  What needs to be different in the smb.conf?  (I used the one there from the samba install, and modified it to add my lines for the new share.

You are almost there but you need to set a samba username/password.

sudo smbpasswd -a username

the username is your ubuntu login name and then it will ask for your password twice. 

Go back to the Vista machine and use this username and password for the popup login box.

cheers!!

---

### Post by movrshakr on 2007-12-15
That was totally it!  Thank you.

Actually, I don't even get the login request when I hit it from the Vista machine, which is exactly what I want.  Perhaps one of the earlier changes I made to smb.conf is causing it not to ask for the pwd.

BTW, will this be sticky across reboots, or do I have to remember to enter it every startup?

And thank you SO much.  You have done a very good deed!

---

### Post by biodoc on 2007-12-15
> **movrshakr said:**
> That was totally it!  Thank you.

Actually, I don't even get the login request when I hit it from the Vista machine, which is exactly what I want.  Perhaps one of the earlier changes I made to smb.conf is causing it not to ask for the pwd.

BTW, will this be sticky across reboots, or do I have to remember to enter it every startup?

And thank you SO much.  You have done a very good deed!

My Machine remembers between reboots.  I'm not an expert but I found that last key step by extensive google searches!

---

### Post by movrshakr on 2007-12-15
I read the man page for smbpasswd.  It is the -a option that makes it permanent by adding it to the samba password file.

Musing, I wonder how/where I was supposed to have known to do this.  Even with ubuntu, things are not easy...and sharing is a pretty fundamental thing these days.

---

### Post by ugm6hr on 2007-12-15
> **movrshakr said:**
> I have installed samba, samba client, and smbfs; I changed smb.conf to "security = share" authentication rather than "security = user".


I am no networking expert, but smbpasswd should be essentially irrelevant if you are using the "share" option in smb, since you are never asked for the password to login (i.e. no login request).  I certainly never had to set it.

However, this can be a bit hit and miss - similar issues exist with Mac-to-Windows sharing with Samba.  I recall reading in a Mac OSX guide book that a prayer to the Windows gods is necessary to get things running smoothly :popcorn:

---

### Post by movrshakr on 2007-12-16
I essentially declare this issue solved for me.  I can now see the ubuntu machine's  STORAGE share from the Vista machine...even was able to map a drive letter to it on the VIsta machine.

All this is exactly what I wanted to do regarding share, and it was solved by the help here, especially biodoc's input.  I do have some other issues and will start separate topics for them.

Thanks to all.

.      --movrshakr

---

