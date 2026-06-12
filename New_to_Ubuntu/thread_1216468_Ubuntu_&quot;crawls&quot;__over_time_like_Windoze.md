---
title: "Ubuntu &quot;crawls&quot;  over time like Windoze"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by Delawaredave on 2009-07-18
I've been running Ubuntu for about 9 months.  

Ran fast in beginning, now it crawls like Windoze used to.

I never installed any additional applications or added things.

Is this supposed to happen ? I did procedures outlined in below:
[http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/]("http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/")

What a bummer.  Appreciate any thoughts.

---

### Post by NightwishFan on 2009-07-18
Do you know what applications are lagging?

Edit: A lot of tips in that article seem fairly useless, and potentially dangerous.

---

### Post by Delawaredave on 2009-07-18
Thanks for reply.  I really just use the computer for web browsing - and firefox is much slower than when initially loaded.

Overall startup and shudown of machine is slower too.

And unrelated, the hibernate and doesn't work anymore with version updates.

All the hell of windoze that I tried to get away from I seem to now have with ubunut....

---

### Post by NightwishFan on 2009-07-18
Personally I have never noticed any gradual slowdowns. (I am actually pretty observant for that sort of thing as well.)

As a good test, log in as the 'guest user' on the user switch panel applet or make a new user temporarily, and see if you notice slowdowns. If the other user is fast, then you might have some odd configuration bug that is causing problems.

Do you have sufficient RAM/CPU/GPU to run Ubuntu?

CPU: Anything, over 700mhz recommended.
RAM: 400+ is good
GPU: Nvidia 6 series and up seems to work well.


As for Firefox, make sure you have smooth scrolling disabled.

---

### Post by wyliecoyoteuk on 2009-07-18
How much spare disk space do you have?
If the / partition gets full, it can all sorts of problems.

Certainly sound slike something is screwed, I have Linux systems that have been running for 5 years with no slowdown.

Another thought, check your processor fan is turning properly, as that sort of symptom can be due to the processor overheating

---

### Post by TrakerJon on 2009-07-18
> **Delawaredave said:**
> I've been running Ubuntu for about 9 months.  

Ran fast in beginning, now it crawls like Windoze used to.

I never installed any additional applications or added things.

Is this supposed to happen ? I did procedures outlined in below:
[http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/]("http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/")

What a bummer.  Appreciate any thoughts.



Clear your web browser cache frequently.

---

### Post by @ntonius on 2009-07-18
> **Delawaredave said:**
> I've been running Ubuntu for about 9 months.  

Ran fast in beginning, now it crawls like Windoze used to.

I never installed any additional applications or added things.

Is this supposed to happen ? I did procedures outlined in below:
[http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/](http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07/)

What a bummer.  Appreciate any thoughts.

Crawling could happen for a variety of reasons and not only because of the operating system.

- a blocked cpu heatink from dust
- a hard disk failing
- a graphics card mulfanctioning
and many more

A small tip : Avoid reading articles that tell you how to keep Ubuntu clean and fast . As i have experianced till now Ubuntu doesnt need special treat to be kept clean.It is optimized for all us regular users and works fine as it is.

---

### Post by ddrichardson on 2009-07-18
Did you know about Computer Janitor - it's in System->Administration->Computer Janitor?

---

### Post by SecretCode on 2009-07-18
If you use it just for browsing, the sluggishness could be in firefox not in ubuntu. Clear your firefox cache as suggested. If that doesn't help, try creating a new firefox profile. I haven't done this on ubuntu but you ought to be able to find instructions by stw for "firefox profile manager".

Do you have many firefox extensions installed? Do you have many applications installed in ubuntu apart from the pre-installed ones? If so ... list them! :)

---

### Post by earthpigg on 2009-07-18
+1 to firefox being a possible culperet. another thing you can consider: if the # of addons has grown over the last 9 months, cut them back down by removing a bunch.

+1 to that article being not-so-great. if your grub menu being long *_bothers you_*, for example, then go ahead and trim it... but it isn't going to make your computer any faster once booted. half the advice given in the article is the same.

htop is also an outstanding tool to monitor what is slowing your machine down.

> sudo apt-get install htop

then, to run it:

> htop

click on "%CPU" to sort by CPU usage.... see what is frequently hovering near the top that doesn't need to be.

and if you dont need it, kill it.

---

### Post by Yownanymous on 2009-07-18
You know no-one's been willing to target the godly Ubuntu as the source of all this. Ubuntu is fast becoming the new Windows.

----------------
Now playing: [Pink Floyd - In the Flesh?](http://www.foxytunes.com/artist/pink+floyd/track/in+the+flesh%3f)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by VastOne on 2009-07-18
> **Yownanymous said:**
> You know no-one's been willing to target the godly Ubuntu as the source of all this. Ubuntu is fast becoming the new Windows.

So one individual has issues and gets 7-8 replies to help and now you reply that Ubuntu is now a MS shadow? 

I sure am glad I logged in today to see this...

I can now laugh my **** off all weekend

---

### Post by philinux on 2009-07-18
I've been running ubuntu over 2 years now. Not seen any crawling. But then again I've not followed any "guides". Just installed stuff from repo and updated.

---

