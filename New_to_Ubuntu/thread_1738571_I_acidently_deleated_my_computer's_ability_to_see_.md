---
title: "I acidently deleated my computer's ability to see wireless"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by bhgfarms on 2011-04-24
Ok, first you need to know I do everything on the computer by accident.  Most of the time I am accidentally pretty good.  How I got to be an Umbuntu user was I accidentally deleted my whole windows system.  I have become pretty good at Umbuntu...really.  I get click happy though..cleaning things out....BAD!  I was helping a young friend down load a picture to her cell...I had seen a blue tooth icon...I thought I would try it...I don't have the equip. for that...so I thought great..why do I need this on my computer..I will just delete all the blue tooth stuff...so click happy I went..took it all off.:confused:  now my computer will not see the wireless.  I have since hooked my comp up to the wire...and tried to down load all that I took off..no good, not happening.  I can not, no matter what I try get it to see the wireless network.  Now I could really use your help...but you will have to talk to me like I am an idiot..because when it come to this kind of stuff...well...I am.  Please if any one can walk me though..I would be so thankful!
Blissfully 
A computer idiot!!
Cathy

---

### Post by llamabr on 2011-04-24
My favorite part is how you call it 'umbuntu'.  Nice.

I think all you did was remove network manager.  I couldn't get all the way through your explanation to be sure, though.

Can you log in as another user, and access your wireless?  If so, we can put network manager back for you.  Try, from the terminal:

```
sudo adduser user2
```

set it up, reboot, log in as user2 and report back

---

### Post by bhgfarms on 2011-04-25
Can you walk me through getting on as a different user..I tried..but a password is needed..never did that.  Sorry.:confused:

---

### Post by dcsoldschool53 on 2011-04-25
I think this thread will solve your problem.
[http://ubuntuforums.org/showthread.php?t=622052](http://ubuntuforums.org/showthread.php?t=622052)

Tell us if it worked.

---

### Post by Aidanomatic on 2011-04-25
When you went through the "adduser" steps, didn't it ask you for a password? If it did make one up, then use that to log on as user2.
Also, unless you're using a dual-boot where you've got restricted space, don't uninstall things you think you dont need. Chances are they're needed to satisfy dependancies that keep other bits and bobs working

---

