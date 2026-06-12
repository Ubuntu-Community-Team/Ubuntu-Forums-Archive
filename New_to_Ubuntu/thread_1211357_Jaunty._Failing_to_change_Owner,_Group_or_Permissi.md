---
title: "Jaunty. Failing to change Owner, Group or Permission"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by wetinwales on 2009-07-12
Hi All

I have a 250GiB external drive which has been working well on my older machine in Heron 8.04.
No I am on a new machine in Jaunty (dual core AMD etc) I try to copy over all the contents of the 250GiB drive. Try as I will, I cannot get permissions to change in order to move them.

chmod -hR, chown, chgrp. None of them will alter the status of the permissions on the Ext drive.

I promise I have been reading forums and Linux tutors for days. No avail. So I now post in desperation..!

How do I get this damned external drive to accept a change of...ANY DAMN THING..?

WiW

---

### Post by Delever on 2009-07-12
sudo chmod -R a+rw /drive

-R : recursivelly
a : for all users
+ : add
r : read
w : write

---

### Post by wetinwales on 2009-07-12
Thanks for your reply.
Tried every version I can with your line ... but nothing works.

The drive appears as:- /media/WD Combo2   (which I write as :- /media/WD\ Combo2  )
Thus in root:- sudo chown -R a+rw /media/WD\ Combo2  gives me... chown: invalid user: `a+rw'

Going to the WD Combo2 directory and trying to modify the directories within gives:-

user@computer:/media/WD Combo2$ sudo chown -R a+rw /*
chown: invalid user: `a+rw'

Thanks
Wiw

---

### Post by LewRockwell on 2009-07-12
why do we need three threads for one trouble-call?


[http://ubuntuforums.org/showthread.php?t=1205049&highlight=chown](http://ubuntuforums.org/showthread.php?t=1205049&highlight=chown)

[http://ubuntuforums.org/showthread.php?t=1211209&highlight=chown](http://ubuntuforums.org/showthread.php?t=1211209&highlight=chown)

[http://ubuntuforums.org/showthread.php?t=1211357&highlight=chown](http://ubuntuforums.org/showthread.php?t=1211357&highlight=chown)


.

---

### Post by wetinwales on 2009-07-12
The answer is simple.

Many of us trying to use Linux are not mathematical or logical or... young.

I rarely understand the complex logic and the philosophy of the software.
I am so confused and frightened by computing I can never remember what I did last.

The three posts you refer me to have no meaning... and yes! they are mine... but I don't truly understand what I am doing.


There is nothing I can do to become younger or more clever.
Linux is for techno people.

I am embarrassed but thank you anyway.

---

### Post by LewRockwell on 2009-07-12
> **wetinwales said:**
> There is nothing I can do to become younger or more clever.

I'll grant you quarter on not being able to become "younger"...

But you shall receive absolutely NO quarter regarding a failure to become more "clever"...

.

---

### Post by wetinwales on 2009-07-12
no quarter for not getting more clever...!
Then Sir you have found the elixir for everlasting growth... or you must be younger than 45... or of course you are a computer generated reply from Kernel Linux..!

---

### Post by oldos2er on 2009-07-12
You appear to have confused the chown and chmod commands. Try this:
```
sudo chown -R username:username /media/WD\ Combo2
```
Replace "username" with your own username.

---

### Post by egalvan on 2009-07-12
> **wetinwales said:**
> **no quarter for not getting more clever**...!
Then Sir you have found the elixir for everlasting growth... or you must be younger than 45...
 or of course you are a computer generated reply from Kernel Linux..!

What LewRockwell meant was that even ancient dogs can learn new tricks.

I'm north of 55, ten years past your 45... ):P
and I'm learning every day.

I started using Linux on a daily basis with the Hardy distro...
April of 2008.
Yes, I had used it before, but never as my main OS.
I've worked my way up to installing it on many different machines,
and now use Linux almost exclusively...

PDA -- Palm Pilot TX
Phone #1 -- Palm Centro
Phone #2 -- Palm Treo 650

These keep me tied to XP...

I've acquired a tremendous amount of computer skills, adding to what skills I already had.


The super-geeks and uber-geeks on this forum are more than happy to share their knowledge and skills...

but almost all of them want you to show an interest in LEARNING something.

Your mind and brain can be kept younger by learning something new EVERY day...
medical science accepts this... you should also.

Only when you stop learning will you truly grow old.

---

### Post by LewRockwell on 2009-07-12
> **oldos2er said:**
> You appear to have confused the chown and chmod commands. Try this:
```
sudo chown -R username:username /media/WD\ Combo2
```
Replace "username" with your own username.

oh, good grief...I didn't even notice that...

.

---

### Post by wetinwales on 2009-07-15
oldOS2er

thanks for your reply.
Neither the chown nor chmod lines make any change to WD\ Combo2.

In both cases terminal flies through the files but appended to each line comes the same expression 'Operation not permitted'

Historically the WD\Combo2 was set up and used in Windows. Perhaps it is an NTFS or fat32.... ah! jaunty is running an AMD A8N-SL1 dual core which I believe is 64bit. Could that affect anything?

Daf

---

