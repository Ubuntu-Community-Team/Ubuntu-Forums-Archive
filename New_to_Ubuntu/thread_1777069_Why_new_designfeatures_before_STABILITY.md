---
title: "Why new design/features before STABILITY?"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by bluepak on 2011-06-07
Can somebody answer this question, why ubunto has new features and design before fixing previous errors?

Also, I have tried installing ubuntu on several hp laptops and wifi doesn't work, nor the display on the latest hp I tried

Thank you

---

### Post by Peter09 on 2011-06-07
Functionality - well things move on, nothing stands still (unless its dead).
 
As for the HP systems, they normally will work, but they may require tweaking, have you come here for support - if so, request support on a particular machine and see if you can get it to work.

---

### Post by tapi0n on 2011-06-07
Are you drivers installed properly? You can check in Additional Drivers (in Administration).

As to why they're implementing new features before fixing buggs. No idea, but I do think the two aspects are not related. I think the descission to implement new stuff is made on another level then actual bugg fixes.

---

### Post by 3rdalbum on 2011-06-07
There are many reasons why Ubuntu developers do not fix problems. If the problem is not caused by Ubuntu-specific code, then there might not be anyone experienced enough with that code to fix it at Ubuntu's end. You should try reporting the bug upstream to the program's developers.

Second reason: Nobody has reported it as a bug, so the Ubuntu devs don't know the problem exists.

Third reason: The problem has been reported but not in sufficient detail to help track down theft problem.

Fourth reason: It's not a bug - it is intended behaviour or a "feature request". 

Fifth reason: it has been fixed in a later Ubuntu but the fix is too invasive or for too obscure a problem to backport it to the earlier Ubuntu.

If you would prefer stability over new features, use only LTS versions of Ubuntu such as 10.04. They are not necessarily less buggy, but their bugs are more predictable and are not going to changeover a new set every six months.

---

### Post by mikewhatever on 2011-06-07
Ubuntu tries to find a balance between new and stable, which is not always easy. If you feel that it's lacking in stability, I see a happy Debian stable user, give it a try.

---

### Post by mkornig on 2011-06-07
> **3rdalbum said:**
> Nobody has reported it as a bug, so the Ubuntu devs don't know the problem exists.

Do you mean that developers who release a new version don't check that it works beforehand? At least the basic/most common features?

> **3rdalbum said:**
> If you would prefer stability over new features, use only LTS versions  of Ubuntu such as 10.04. They are not necessarily less buggy, but their  bugs are more predictable and are not going to changeover a new set  every six months.

I've tried 11.04 64 bit and faced several serious problems. It was a mess. I didn't report any bugs because I was so disapointed with Ubuntu. Then I installed 10.04 32 bit and most of these problems went away. Newbies are better off with an old LTS version, I think.

---

### Post by mikewhatever on 2011-06-07
It is fairly obvious that developers can't test every possible software configuration on all possible hardware. Bugs always surface up in mass after any major release. That's why there are updates, service packs, and so on.

PS: Sorry that 11.04 didn't works for you, the 64bit version works beautifully here. Should I extrapolate my narrow personal experience onto the masses and recommend 11.04 64bit to everyone I meet? Guess not.

---

### Post by Paqman on 2011-06-07
> **mkornig said:**
> 
I've tried 11.04 64 bit and faced several serious problems. It was a mess. I didn't report any bugs because I was so disapointed with Ubuntu.

Reporting bugs on Ubuntu is really easy, just hit Alt-F2 and type:
```
ubuntu-bug packagename
```

This will add all the technical info to the bug report, and raise the bug on Launchpad. All you need to do is provide a brief description of what the problem is (the more detail you include, the better).

---

### Post by tapi0n on 2011-06-07
> **Paqman said:**
> Reporting bugs on Ubuntu is really easy, just hit Alt-F2 and type:
```
ubuntu-bug packagename
```This will add all the technical info to the bug report, and raise the bug on Launchpad. All you need to do is provide a brief description of what the problem is (the more detail you include, the better).

Can you do this too without loading it on Launchpad? For example to look trough it on your own? Just out of curiousity.

---

### Post by Paqman on 2011-06-07
> **tapi0n said:**
> Can you do this too without loading it on Launchpad? For example to look trough it on your own? Just out of curiousity.

Yes, you can check what is being sent before it goes. You can automate this if you want to capture the behaviour of a misbehaving app. To do this you can [enable apport]("https://wiki.kubuntu.org/Apport#How to enable apport"). If the program crashes apport will round up all the relevant info in readiness for reporting a bug. It's intended mostly for use on the testing branch, so don't expect instant action if you file a bug on a stable release.

---

### Post by tapi0n on 2011-06-07
> **Paqman said:**
> Yes, you can check what is being sent before it goes. You can automate this if you want to capture the behaviour of a misbehaving app. To do this you can [enable apport]("https://wiki.kubuntu.org/Apport#How%20to%20enable%20apport"). If the program crashes apport will round up all the relevant info in readiness for reporting a bug. It's intended mostly for use on the testing branch, so don't expect instant action if you file a bug on a stable release.

Cheers mate I'll definitely look into it after my exams :).

Of course I'm not expecting anything from this. Just want to see what's going on, get to know my new os.

---

### Post by mkornig on 2011-06-07
> **Paqman said:**
> Reporting bugs on Ubuntu is really easy, just hit Alt-F2 and type:
```
ubuntu-bug packagename
```This will add all the technical info to the bug report, and raise the bug on Launchpad...

This implies that you know which package is causing the problem. I've had several cases where I totally ignored this. What if the button to shut down the system suddenly disapears? A driver wizzard explicitly asks for the root password? The screen suddenly freezes? The cursor jumps around randomly? You asked for a French keyboard layout but still can't type certain French letters?

---

### Post by Paqman on 2011-06-08
> **mkornig said:**
> This implies that you know which package is causing the problem. I've had several cases where I totally ignored this. What if the button to shut down the system suddenly disapears? A driver wizzard explicitly asks for the root password? The screen suddenly freezes? The cursor jumps around randomly? You asked for a French keyboard layout but still can't type certain French letters?

It does yes, but you'll find the same problem when trying to file a bug report manually. If your problem is crashes then enabling apport should catch it for you.

However, it's not a *massive* problem if you file the bug against the wrong package. The devs will know if the failure mode is caused by their stuff, and will probably be able to reassign it to the correct package if it's not theirs. It's a bit of a waste of their time, but better than not reporting it and having it go unfixed.

---

### Post by hakermania on 2011-06-08
Well, if all of ubuntu developers stop developing to fix the bugs, how will they keep up with the other OS?

---

### Post by jtarin on 2011-06-08
> **hakermania said:**
> Well, if all of ubuntu developers stop developing to fix the bugs, how will they keep up with the other OS?By fixing the bugs.:p

---

