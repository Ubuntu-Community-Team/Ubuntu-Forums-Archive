---
title: "Hibernation and Suspending Doesn't Work..."
date: 2010-12-24
forum: New to Ubuntu
---

### Post by Vi3tHoneyX on 2010-12-24
Hey all, it's my first time using Ubuntu and my laptop won't hibernate or suspend correctly... What can I do or what should I check to see what's wrong? Thanks!

---

### Post by steve161 on 2010-12-25
What version of Ubuntu are you using, and what is your laptop make and model? Such information may help to find a solution to whatever issues you may have.  Oh, and welcome to the forum.

---

### Post by _0R10N on 2010-12-25
> **Vi3tHoneyX said:**
> Hey all, it's my first time using Ubuntu and my laptop won't hibernate or suspend correctly... What can I do or what should I check to see what's wrong? Thanks!

Hey there! what do you mean by "won't hibernate or suspend correctly"? Anyway, I recommend you to take a look at your Power Management configuration.

Kind regards!

---

### Post by marl30 on 2010-12-25
I'm sure the OP is not the only one with this issue. I have had this issue since installing 10.10. I even set my swap file to double my ram and still no luck.

---

### Post by steve161 on 2010-12-25
It is somewhat of a common issue.  However, Ubuntu has been the only distro where suspend worked on my Toshiba laptop.

---

### Post by Vi3tHoneyX on 2010-12-25
I'm on 10.10 using an Asus K52F-BBR9. Whenever I choose to suspend my laptop it goes to the right screen, but when I move my mouse or click a key the login page shows up and before I can type in my password the screen goes black yet it is still on. When my laptop is hibernating and I press a key the screen turns on all black. I always have to turn off my laptop and turn it back on again so I stopped using suspend and hibernate on it.

---

### Post by marl30 on 2010-12-25
> **Vi3tHoneyX said:**
> I'm on 10.10 using an Asus K52F-BBR9. Whenever I choose to suspend my laptop it goes to the right screen, but when I move my mouse or click a key the login page shows up and before I can type in my password the screen goes black yet it is still on. When my laptop is hibernating and I press a key the screen turns on all black. I always have to turn off my laptop and turn it back on again so I stopped using suspend and hibernate on it.

This is exactly what has been happening with my computer as well. I do hope someone knows a work around. I'll be following this thread closely.

---

### Post by Vi3tHoneyX on 2010-12-25
On a random note...

Happy Christmas from Florida!!! ^_^

<3 <3 <3 <3 <3

---

### Post by marl30 on 2010-12-25
> **Vi3tHoneyX said:**
> On a random note...

Happy Christmas from Florida!!! ^_^

<3 <3 <3 <3 <3
Happy Holidays to you too. 

I wonder if there is any fix for this issue. This is not the first thread I've followed on this topic and still no solution.

---

### Post by Vi3tHoneyX on 2010-12-27
I have found a solution to the suspending problem on my laptop! :D I used this guy's solution.

[http://ubuntuforums.org/showthread.php?p=10283020#post10283020](http://ubuntuforums.org/showthread.php?p=10283020#post10283020)

However, the hibernation problem is still here and I'm not sure what to do... I think my best bet is to wait until someone else figures it out like this guy. xD

You should search the forum by typing in your computer model to see if others have the same problem! That's how I found the suspending solution. :)

Good luck. 

<3 <3 <3 <3 <3 <3 <3 <3 <3 <3

---

### Post by Vi3tHoneyX on 2010-12-27
Actually, the solution I mentioned above did fix my hibernation!!!! It just takes a veryyy long time (3-4 min) staying on the black screen until the login box pops up. I'm really happy about this. :D

---

### Post by LSenf on 2011-02-19
You might try uswsusp which does some compression, that might speed it up. Also, clearing the cache reduces the amount of memory to be saved.

---

