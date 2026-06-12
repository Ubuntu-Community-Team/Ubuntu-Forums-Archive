---
title: "Permissions Messup"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by teamcoltra on 2009-03-11
Okay so I don't know how much of a beginner question this is, but since it was a noobish mistake I figure it goes here...

I have my home in its own partition, I came back to ubuntu from using crunchbang (loved it, but I am a Ubuntu guy). 

When I first started all my files were displaying from my home folder to my desktop.. .I tried to fix the issue but it just kept happening. I googled the issue, but none of the fixes worked, so I just created a new user with admin abilities and then moved my files over to that account, then deleted my original account, created a new profile under my original name with admin abilities and moved all my files back over and that pretty much fixed the issue (I am *SURE* there was a better way to do this, but my way worked) 

I have been noticing that some of my files have been giving me permission issues that I know normally doesn't happen so I went through gksudo nautilus and went to /home and set permissions to owner = teamcoltra Folderaccess read write

Group teamcoltra folder access ^ Same

and Others ^ (basically I set it to 777, yes that is a security risk upon itself... but security has never been high on my priority list opposed to ease-of-use) 

I also said "Apply permissions to enclosed files"

After I did that 2 things happened:
My desktop icons disappeared (they reappear when I hover over them) and if I highlight (on the desktop like if I was selecting multipul files) over conky... it makes that little spot disappear... until it refreshes or I change workspaces.

I know that it is permission related, but is this an easy fix?

What were the permissions originally? I, in my stupidity, didn't write them down. 


You guys rock, thank you! :)




UPDATE: THANK YOU GUYS SO MUCH! I followed the instructions below.. and that fixed my permissions issues... then I wound up reinstalling GNOME and it worked.. partially... now my CONKY wont work but thats my own issue and not related to this :)

---

### Post by Kareeser on 2009-03-12
Sheesh. That's nuts.

Don't quote me on this, but as a very VERY "quick draw" and "shotgun" solution:

```
sudo chown teamcoltra:teamcoltra -R ~/
sudo chmod 755 -R ~/
```

---

### Post by teamcoltra on 2009-03-12
Oh no... if my system dies.. I am blaming you, better hope I come back and edit this saying all is good ;)

.. brb.


EDIT: Okay didn't even make it to the rebooting stage... I keep getting this error 

teamcoltra@geeksparadox-desktop:~$ sudo chown teamcoltra:teamcoltra -R ~/
[sudo] password for teamcoltra: 
chown: cannot access `/home/teamcoltra/.gvfs': Permission denied


So I tried to delete it, said I couldn't because its a directory.

---

### Post by Kareeser on 2009-03-12
What the balls? How can a sudo'd command have its permissions denied?

I'm out of my element here. *bump* =P

---

### Post by mcla0203 on 2009-03-12
It might just be me but doesn't the -R come directly after the command... i.e.
```
chmod -R 755 path
```

---

### Post by sisco311 on 2009-03-12
~/.gvfs is a virtual file system. you can ignore that error message.

---

### Post by sisco311 on 2009-03-12
> **mcla0203 said:**
> It might just be me but doesn't the -R come directly after the command... i.e.
```
chmod -R 755 path
```

both works. 

i would set the directory permissions to 755 and the file permission to 644:
```
sudo chown -R teamcoltra:teamcoltra ~/
```
```
find ~/ -type d -exec chmod 755 {} \;
```
```
find ~/ -type f -exec chmod 644 {} \;
```
 
once again, ignore the error message complaining about ~/.gvfs

---

### Post by teamcoltra on 2009-03-12
Followed the instructions and my desktop icons still dissapear if not hovered over. 

After each one of those commands they would re appear for like... 2 - 3 seconds and then redisappar again. 

My permissions are now correct but grr @desktop icons... 

In a way I like it, it means that I get to have desktop icons, and a clean desktop.. HOWEVER ... it means there is something wrong with my system at the same time... I dislike that.

---

### Post by teamcoltra on 2009-03-12
I got an error message.. that I need to kill the bonobo-server or something like that and restart nautilis and my life will be complete when I killed conky.

---

