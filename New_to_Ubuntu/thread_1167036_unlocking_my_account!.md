---
title: "unlocking my account!"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by drjackal on 2009-05-22
i read through quite a few threads regarding my problem..although insightful i am still left with no solution. 

here is my problem: my account cannot be unblocked. everytime i try in the users settings panel (system>administration:>users and groups)the unblock button is kind of unresponsive. i press it. it depresses but no activity. i tried the console too. typed in 

usermod -U LOGIN

and it showed 

usermod: unable to lock password file

tried sudo usermod -a -G admin spike
 (in case i wasn't an admin altough the user privileges tab shows i have the right to administer the system. but i cannot check or unck=heck any other option)

and it asks for my passowrd but then noting happens.

PLEASE HELP!!! i need to change this so that i can connect to the internet using ubuntu.!!!

---

### Post by drjackal on 2009-05-22
or can it be a bug?

---

### Post by Didius Falco on 2009-05-22
I think it's a bug - it *is* an early Alpha. I'n getting the same thing right now.

This works for me, though: go to your Fast User Switcher (on your panel where you go to log out, etc.) and right-click it. Select **Edit Users and Groups** and try unlocking it from there.

Regards,

Didius

BTW, you should direct Karmic inquiries to the **Karmic Koala Testing and Discussion** threads:

[http://ubuntuforums.org/forumdisplay.php?f=359&order=desc](http://ubuntuforums.org/forumdisplay.php?f=359&order=desc)

---

### Post by drjackal on 2009-05-22
ooopsies ur method also didnt work on me... can it be that i might have screwed up? what can screw up my system like that?

---

### Post by Didius Falco on 2009-05-22
Well, being as it's an early Alpha, it could be any number of things. It could be something you did, or it could be a breakage in some recent code that was updates, or it could be a bug they just haven't gotten around to squashing yet.

I'd make a post in the Karmic area and see if anyone else is experiencing the same thing. Then I'd go to LaunchPad  [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) and search for that bug, or similar bugs and see what they have to say. You may find a workaround or fix there.

If you can't find a bug, and no one in the Karmic area knows anything about it, file a new bug report - read this for info on doing just that:

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

[http://ubuntuforums.org/showthread.php?t=1161570](http://ubuntuforums.org/showthread.php?t=1161570)

Regards,

Didius

---

### Post by drjackal on 2009-05-22
thanks a bunch..but is there a way i can create a new user with sudo abilities?? i can then get that system running!! :)

---

### Post by Didius Falco on 2009-05-22
Hi,

Try rebooting into recovery mode Root shell and typing ```
adduser username admin 
```, with username being your account name.

If that doesn't fix it after a reboot, go back into Recovery Mode again and use the same command, but add a new user. Be sure and tack the "admin" part onto the end, or else you'll just wind up with a 2nd user without admin privileges.

If that doesn't work, post again. Hopefully one of the real gurus will pop in and take over.

Regards,

Didius

---

### Post by nandemonai on 2009-05-22
You realise Karmic is an early release Alpha right?

Shouldn't be using it as a main desktop or anything yet. Things are bound to break.

---

### Post by drjackal on 2009-05-22
:P i seem to realise how many things can go wrong :P still helps me to learn through :

oh by the way i tried adding another user aand then deleted that user because i hadnt appended the root part.. it seems i wrote that part correctly..as i see how you have written too..

also i tried unlocking it again and alternately locking it by the cui...and well my user account is not at all accessible now!!!!

---

### Post by drjackal on 2009-05-22
and thank god its only on my laptop.. i have tried millions and zillions of s/w on it.. it has become kindof testing grounds :P i got this family desktop running xp faithfully...in case anything untoward were to happen :P to my ubuntu...which i manage to screw up pretty bad more often than not :P

---

### Post by drjackal on 2009-05-22
BRILLIANT!!! now i am not even able to add another user even on root shell prompt on recovery mode!!!!

added a new user but this problem came up:

/home/loginname could not be created..

*some error panel drop down that was simply too fast!* remember seeing X server though.

finally

"could not update ICEAuthority file /.ICEauthority

"there is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

---

### Post by Didius Falco on 2009-05-22
Okay, boot again into Recovery Mode, Root Shell.

When you get to the command prompt, type these three separate command, in order:

```
chown jackal:jackal /home/jackal/.ICEauthority
```

For jackal:jackal, substitute your username and computername. For /home/jackal/.ICEauthority, substitute your username for jackal. The same conventions apply for the next command.

```
chmod 644 /home/jackal/.ICEauthority
```

```
exit
```

Then resume your normal boot.

Regards,

Didius

---

### Post by drjackal on 2009-05-24
oops!! chown:cannot access '/home/loginname/.ICEauthority': No such file or directory!!

---

### Post by Didius Falco on 2009-05-24
Read through these two threads, and follow the instructions that apply to you. Hopefully, this will correct the problem. 

If it doesn't, you'll need the help of someone more advanced than I am...

[http://ubuntuforums.org/showthread.php?t=997068](http://ubuntuforums.org/showthread.php?t=997068)


[http://ubuntuforums.org/showthread.php?p=6138880](http://ubuntuforums.org/showthread.php?p=6138880)

Good luck!!

Regards,

Didius

---

### Post by drjackal on 2009-05-26
more advanced than u?? hehe...are there lvl's of knowing ubuntu too??

---

### Post by drjackal on 2009-05-26
i'll try the second thread..since i think my problems lie with the .ICEauthority rather than the .dmrc files because the settings load fine... :)

will try that and post a reply..pathetic power supply this week..wishing myself the best...here we go!!!

---

