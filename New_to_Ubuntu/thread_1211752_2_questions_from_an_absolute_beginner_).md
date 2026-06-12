---
title: "2 questions from an absolute beginner :)"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by FuneralQueen on 2009-07-13
Hi there :)

I literally installed Ubuntu yesterday and so far I seem to be ok (I removed XP from my laptop), however I have 2 questions that are probably pretty obvious, but I'm new so please be nice :)

1. I've started playing with GIMP, and after downloading some brushes I tried to transfer them into the correct file path but I get an error message that says "Error details: permission denied". I already googled it, and all the answers to the question seem to be some coding. I tried going through System>Admin>Authorizations and granted myself access in "Explicit Authorizations" but still no luck! So I was hoping smoeone could give me a process of how to fix it?

2. I've installed all the current Firefox plugins (that I'm aware of) but the MySpace music player never seems to show up??

I apologise if these are really simple things I should already know, but thanks to anyone who can help!

:)

---

### Post by mano cazalet on 2009-07-13
I've never used gimp but maybe your problem is related to file permissions.
Try to see if it happens when u transfer your brushes as root, starting nautilus in terminal with 
gksudo nautilus

some reading a forum member wrote for beginners, lots of interesting stuff. It might interest you.
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

and further documetation on file permissions>
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Possum Films on 2009-07-13
If you need to copy files to any directory other than your home directory (usually /home/<your user name>) just right click on the folder and select "Open as Administrator". You may be prompted to enter a password and then a new file browser window will open where you can place your files. See [this article]("http://en.wikipedia.org/wiki/Superuser#Unix_and_Unix-like") for more details about why this is necessary.

Have you installed the Adobe Flash player plugin? I think that the MySpace music player needs this to run. 

I hope that you enjoy using Ubuntu :)

---

### Post by FuneralQueen on 2009-07-13
Excellent - thank you!
That first link was very well written and understandable from an ex-Windows person like me :) I figured out how to use it after reading that. Thanks so much :)

---

