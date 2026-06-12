---
title: "Graphics Driver Problem"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by Devon64327 on 2009-10-17
Well I just converted to pure Ubuntu for no reason and now I have a slight problem. that beryl and compiz everyone is drooling over can only be activated with the right drivers and when i search for my drivers they don't show up. Im no expert in hardware and i always thought i had to go to a store and buy a chip for this stuff but can anyone help?

---

### Post by Devon64327 on 2009-10-17
NEED HELP 
```~~~Bump~~~```

---

### Post by aesis05401 on 2009-10-17
Hello, 

You are bumping too quickly.  This is a volunteer community, and bumping more often than once a day is considered mildly impolite. 

What is your graphic chipset?

---

### Post by thunk77 on 2009-10-17
Hello,

Start a terminal and type:

```
lspci | grep VGA
```

This command outputs your graphics card. Then, copy/paste it here.

---

### Post by zachary83 on 2009-10-17
Hi, 
Dont know if this is cool to post, but cant seem to work out how to start my own post.

 I have a similar problem, I cant get the Graphics drivers to come up in Hardware Drivers app, cant get the 3D to work without problems and also videos are glitch when full screen.

Don't know if this is cool, sorry if not.

---

### Post by Devon64327 on 2009-10-17
its nvidia but im ot sure about model or even if i know what im talking about
---edit---
ahh it would appear i dont know what im talking about since this is what i got
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)



btw ive been eating lunch sorry

---

### Post by JoshuaRL on 2009-10-17
> **zachary83 said:**
> Hi, 
Dont know if this is cool to post, but cant seem to work out how to start my own post.

 I have a similar problem, I cant get the Graphics drivers to come up in Hardware Drivers app, cant get the 3D to work without problems and also videos are glitch when full screen.

Don't know if this is cool, sorry if not.

It's generally called "Thread Hijacking" but since it's all the same issue (I think) we can go ahead and help you out here.  In the future, go to the main ABT forum and look near the top left for the New Thread button.

As for your problem, please post the output of the terminal command posted above.  That will help us know what type of card you have.

---

### Post by Devon64327 on 2009-10-17
:( i thought i was getting help :(
and another problem i had was that amarok wont play any music -.- just this morning and ive reinstalled it 2 times

---

### Post by aesis05401 on 2009-10-17
Hello devon, 

The Intel chipset in your machine will be able to handle moderate loads, but due to architecture of that model there are some constraints.  Here is the manufacturer info page if you have any interest: [http://www.intel.com/support/graphics/intel845g/sb/CS-009078.htm ]("http://www.intel.com/support/graphics/intel845g/sb/CS-009078.htm").

The driver that shipped with Jaunty for this chipset is not set up for performance.  I am actually in the middle of writing a beginner level overview on this subject summarize manufacturer and community supplied info on the subject.. In the meantime, try reading through this guide: [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582").  There is a warning to beginners at the top of the guide - so if it looks too advanced for you hold off and we will come up with something else.

For informational purposes, the trouble with Intel chipsets are not limited to Ubuntu.  As for the sound problem, you will get the best help if you start a new thread with a descriptive title for that issue.

---

### Post by Devon64327 on 2009-10-17
Thank you! I will look up those links

---

