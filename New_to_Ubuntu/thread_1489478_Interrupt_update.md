---
title: "Interrupt update"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by jakeeee on 2010-05-21
Okay.
So, i was upgrading to 10.04 today, and I had to leave to take the computer to my friend.
So i went to the terminal and xkill'd the dist upgrade window.
Then I shut it down like usual
Now I just tried turning it back on and it says it cant mount /dev
So idk I need to reinstall ubuntu I guess.
But my computer is too old to boot from usb
And I dont have any spare cdr's
Is there some other way I can install it?
I have a flash drive and my netbook that I'm on right now.

---

### Post by Peter09 on 2010-05-21
Ouch -- Killing an update while its in the middle of something is about the same as throwing the O/S over a cliff. 
 
Unless you can generate a LIVECD your on a loser. Do you know anyone with a windows machine, they could do it. Or you could borrow a usb CD drive (if you can get one) and put it on your netbook

---

### Post by Peter09 on 2010-05-21
Thinking about it I am sure there is a utility which you put on a floppy drive. You boot your machine from it and then boot your USB stick from there - I'm just not sure where you get it from.

---

### Post by jakeeee on 2010-05-21
Ahhh I didn't know that till now..

I dualboot windows7 and ubuntu on my netbook.
So what do I do?

---

### Post by Peter09 on 2010-05-21
Suggest the simplest would be to find a windows machine with a CD drive. You could transfer the .iso using a usb memory stick.

---

### Post by Peter09 on 2010-05-21
Are you actually getting to a terminal prompt? Or is it just dead.

---

### Post by jakeeee on 2010-05-21
Idk its just hanging now it was booting it looked like.
It says checking battery state [ OK ]
then a underscore blinking.

if i press alt - fsomething it goes to the login thingy where i can do commands and stuff.

---

### Post by Peter09 on 2010-05-21
Thats good, try logging in with your user name and password and if you get a prompt enter the following code
 
```
sudo apt-get upgrade
```
 
and tell us what happens.

---

