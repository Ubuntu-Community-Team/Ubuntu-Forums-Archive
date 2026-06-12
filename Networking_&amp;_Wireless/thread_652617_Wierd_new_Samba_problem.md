---
title: "Wierd new Samba problem"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by Mark Phelps on 2007-12-28
Have been using Ubuntu 7.04, and now, 7.10, and accessing shared volumes on a Windows XP box without problems -- until recently.

I didn't have to set anything up.  I simply clicked the Network Icon in Places, then double-cliked the name of the box (wwxpsrvr), and I was able to browse the 4 volumes I've set up for sharing.   I've set up a shared directory on each shared volume, such that this directory can be accessed read/write while all the others are accessed read-only.

Then, in the last couple of weeks, two things have happened. 

First, I was unable to browse volume Server_1 -- even though it's sharing options are set up exactly like the other four volumes.  Double-clicking that folder in Nautilus produces an error popup stating The folder contects could not be displayed. Sorry, couldn't display all the contents of "Server_1". 

Tried using Gnome-commander (which has also worked flawlessly ever since I started using it months ago), Double-clicking the shared folder there produces an error popup stating "List failed: Invalid parameters"

I've tried unsharing and re-setting the Sharing options on the XP box -- and it makes no difference.

The second problem is similar to the first.  I added two more volumes over the Christmas holiday: Server_5 and Server_6.  I set up sharing on both volumes using exactly the same settings (except for the share names) as the other four volumes.

But once again, Samba fails -- but in this case, only on Server-5!  Access to Server_6 is fine -- both read-write on the sole shared write directory, and read-only on the others.

I've made absolutely no changes to the Samba settings on my machine. In fact, I'm using the default smb.conf file that Ubuntu installed with 7.04. I saw no need to mess with it because, until recently, I had no problems accessing the XP box.

I can post the smb.conf file if anyone wants to see it, but seeing as how Samba works on some of the volumes but not on the others, and as how I've identified NONE of the shared volumes in the smb.conf file, I don't know what to look for to fix.

Please help.

---

### Post by empthollow on 2007-12-28
i've had some weird intermitent problems with samba myself.  although i can't give you a definite answer why yours is acting the way it is i will tell you what made a difference for me.  the most important part for me is under authentication, i use:
```
security = share
```
this does not request a pw but i have read/write access.

the second is where i setup my shares, i use other than home directories but these are the options that work for me
```
[data]
path = /media/data
available = yes
browseable = yes
public = yes
writable = yes
```

hope this helps

---

### Post by Mark Phelps on 2007-12-30
The actual fix had to be done on the Windows side, specifically, the XP box.

There's a parameter IRPStackSize that defaults to a low value.  It has to be increased in order to allow some file sharing to work.  Found it by googling on the error messages I was getting. 

Now, the Samba stuff is working fine again -- and I didn't have to do anything in Linux!

---

