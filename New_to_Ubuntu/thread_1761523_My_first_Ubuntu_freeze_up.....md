---
title: "My first Ubuntu freeze up...."
date: 2011-05-18
forum: New to Ubuntu
---

### Post by Ken UK on 2011-05-18
Hi all,

So yesterday Ubuntu froze up on me for the first time, I think it was due to Firefox freezing up and crashing (because of a website it didn't like) and thus I couldn't do anything.

As this is Linux afterall I'm sure there is some solution to this that a beginner like me doesn't know, what do I do when Ubuntu freezes up and stops responding?

Yesterday I used the ol' Windows approach of hitting the power button which is what landed me in Ubuntu fully in the first place.

Regards,

Ken

---

### Post by powerpleb on 2011-05-18
Try this:
Right Alt - Print Screen - K 

As if you were doing CTRL - ALT - DEL.

It restarts the X server and lands you back at login screen.

---

### Post by Ken UK on 2011-05-18
Thank you!

I will write that down and give it a try. I might make a little crib sheet to help remember these things.

---

### Post by Wim Sturkenboom on 2011-05-18
You don't state which version of Ubuntu, but older versions used <ctrl><alt><backspace> instead of the earlier mentioned combination.

---

### Post by Ken UK on 2011-05-18
The latest, 11.04.

Why did they change it to such a random and set of keys? Surely it would have been better to leave it as it was especially for new uers.

---

### Post by mikewhatever on 2011-05-18
> **powerpleb said:**
> Try this:
Right Alt - Print Screen - K 
...

That just froze the screen for me, so that there was no escape from SysRq-reisub. Some more info should be useful for those like me.
[https://secure.wikimedia.org/wikipedia/en/wiki/Magic_SysRq_key](https://secure.wikimedia.org/wikipedia/en/wiki/Magic_SysRq_key)

---

### Post by marcio_mi on 2011-05-18
Before resorting to the magic sysrq keys, if it is that case that the GUI is frozen, you can try to access a terminal by CTRL+ALT+F1, login, and then type
```
sudo service gdm restart 
```

---

### Post by Ken UK on 2011-05-18
> **mikewhatever said:**
> That just froze the screen for me, so that there was no escape from SysRq-reisub. Some more info should be useful for those like me.
[https://secure.wikimedia.org/wikipedia/en/wiki/Magic_SysRq_key](https://secure.wikimedia.org/wikipedia/en/wiki/Magic_SysRq_key)

Nice link although I don't understand the descriptions of what each does lol

I also get the problem with Skype (I hate skype I always have problems with it on all platforms) where it crashes but the process is still running, I try to kill it graphically using system monitor but then it turns into a zombie! lol
As far as I read a zombie process is one that still has a parent running? Not sure what that is in Skypes case but could any of those shortcuts sort that problem out and flush the zombie skype out?

---

### Post by marcio_mi on 2011-05-18
here is a lengthier description of the magic sysrq keys:

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

cheers

---

### Post by marcio_mi on 2011-05-18
please delete

---

### Post by Ken UK on 2011-05-18
> **marcio_mi said:**
> here is a lengthier description of the magic sysrq keys:

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

cheers

That is spot on! Im going to make a note of it incase it happens again, thanks.

---

### Post by powerpleb on 2011-05-18
> **Ken UK said:**
> 
Why did they change it to such a random and set of keys? Surely it would have been better to leave it as it was especially for new uers.
I suppose if you felt nasty, you could walk into a room and hit CTRL - ALT - BACKSPACE on someones computer and they would lose all their unsaved work. You could do the same with the combo I mentioned, but it isn't as well known.

Perhaps that's why they phased it out. Or maybe they just expect users to stare blankly at the frozen screen and wait for tech support to come to the rescue whenever there is a lock up.


> **marcio_mi said:**
> here is a lengthier description of the magic sysrq keys:

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

That is so useful! Thanks!!! :smile:

---

