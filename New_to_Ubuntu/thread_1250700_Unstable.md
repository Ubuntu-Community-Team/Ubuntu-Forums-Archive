---
title: "Unstable"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by Wydo on 2009-08-26
This install is very unstable.  It freezes up every few minutes.  Help needed.

---

### Post by overdrank on 2009-08-26
> **Wydo said:**
> This install is very unstable.  It freezes up every few minutes.  Help needed.

Hi and welcome, a little more info could help. :) Some system specs and version of Ubuntu your are using?
Moved to Absolute Beginner Talk

---

### Post by running_rabbit07 on 2009-08-26
Edit: What he said^^^^

---

### Post by Wydo on 2009-08-26
I just downloaded it 3 days ago and I used Nero to burn to disk.
 
I have an Abit AB9 PRO motherboard.  Other than that I have an Nvida graphics card.
 
I had trouble with the install with other hard drives in this system so I disconnect all of them and installed to a single system hard drive and I used the whole disk space.  When the install was done I put all the other hard drive back.  One of the hard drive had Vista on it.
 
The first problem I had was with the update which did not complet and I solved this by hiting the ESC key at boot up and I ran restore and it seemed to solve the problem.
 
The next thing I noticed was when I would install applications where it would freeze at some point.  The next thing was when it froze when I played a video.  Some apps cause it to freeze.
 
I think if I boot up to Ubuntu and don't do anything it will not freeze.

---

### Post by celthunder on 2009-08-26
Which update didn't complete and did you stop the update half way through?  try aptitude update;aptitude safe-upgrade and see if it finishes updating your packages might help.

---

### Post by Wydo on 2009-08-26
Right after my first boot up a window popped up with a list of updates.  I really didn't look at the list but I just hit the update button and it went through the update until the end where they are all downloaded and they are being installed then everything frooze up.  I left it for about an hour but it had the same screen.  My mouse cursor wouldn't move so I hit the reset button.
 
After that I couldn't install an app or reinstall the updates. 
 
How do I reinstall that update you mentioned?

---

### Post by celthunder on 2009-08-26
in a terminal type aptitude update and then when thats done type aptitude safe-upgrade and see if that changes any packages. (if you aren't root add sudo before each of those commands)

---

### Post by Possum Films on 2009-08-26
Go to Applications > Accessories > Terminal, type the commands in (separately) and hit enter.

EDIT: Never mind, celthunder has already said this.

---

### Post by running_rabbit07 on 2009-08-26
Did you install 9.04 or 9.10?

---

### Post by Wydo on 2009-08-27
OK, did that and it went fine. What do I do now? Just test it out?
 
I went to insall apps and it froze up. Then I went into when into the file manager and when I closed the window it froze up.
 
---------------------------------------------------------------------------------------------------------------------------------------
 
Today when I booted up it went into a routine disk check. After it was done I was looking down the list and at the bottom it said, "failed" then it continued to boot. Is there a log of this where can I find it and what is the name?
 
At one point I did a recovery before I booted up. Is there a log of this and where can I find it and what is the name?

---

### Post by celthunder on 2009-08-27
Which version are you on? if you dont know cat /etc/issue and it should tell you.

---

### Post by Wydo on 2009-08-27
This is version 9.04

---

