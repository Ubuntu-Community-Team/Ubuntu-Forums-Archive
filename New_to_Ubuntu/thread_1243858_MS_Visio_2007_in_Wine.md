---
title: "MS Visio 2007 in Wine"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by djmac on 2009-08-18
I have just installed MS Visio 2007 under wine. It loads up okay, but as soon as you try to do something (i.e. start a new file, load an old one) it crashes, (and wants to send an error report to microsoft). Has anyone had this problem, or had any success getting around it?

Thanks

---

### Post by Mark Phelps on 2009-08-19
Is it the "standard" or the "professional" edition?  

The CodeWeavers site (see link below) lists Standard as "garbage" and Pro as "bronze", meaning, that if you have Standard, it's not going to wory, period.

Link: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=119]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=119")

---

### Post by rodrigoeblanco on 2010-05-08
I have the same problem, by I installed Visio with Wine in my lab's computer and it works perfectly, but now i'm trying to install it in my laptop and It crashes when I try to open a file. I think it's just some wine config you have to deal with. Cause I'm running Ubuntu 10.4 on both computers. Maybe someone could give some advice about this, Thank you in advance!

---

### Post by sir_nasty on 2010-05-08
My online school required Visio (Kaplan University) I said forget it... I went with Open Office Draw and have yet to look back... just a thought...

---

### Post by lavinog on 2010-05-08
My advice is to check back every now and then.  Wine tends to be updated frequently (I think every 2 weeks)  Sometimes things get fixed and sometimes things break.

Would running winxp in a Virtual machine be sufficient?

---

### Post by nikefalcon on 2010-05-08
If everything fails and you have enough RAM(around 1GB) you could try running it on a virtual machine.
VirtualBox is a good one.

---

### Post by goltoof on 2010-07-13
I need to get Visio '07 working. I followed [directions]("http://ubuntuforums.org/showthread.php?t=1173365") for setting up Office 07 in Wine. Visio installs/opens/activates fine, but I can't get images or shapes to load. There is no shape library. I can only do lines and text. 

I'm using Lucid Lynx 10.04.

---

### Post by mlentink on 2010-07-13
> **goltoof said:**
> I need to get Visio '07 working. 
Why?

---

### Post by goltoof on 2010-07-13
> **mlentink said:**
> Why?

Yeah... notice I didn't say I 'want' to, but 'need' to.  

It's what everyone else uses at work.  I need the ability to work with vsd files.

---

### Post by mlentink on 2010-07-13
> **goltoof said:**
> Yeah... notice I didn't say I 'want' to, but 'need' to.  

It's what everyone else uses at work.  I need the ability to work with vsd files.

If so, you might want to consider either using a virtual machine to run windows/office, or dual booting. 
Do not, I repeat, do NOT try and run software on Linux that was originally written for an entirely different operating system. How many Windows software programs run on the Mac? Don't expect Ubuntu to be different. Just because Wine does run quite a few Windows programs doesn't mean it can run them all...

---

### Post by gandaran on 2010-07-13
> **goltoof said:**
> I need to get Visio '07 working. I followed [directions]("http://ubuntuforums.org/showthread.php?t=1173365") for setting up Office 07 in Wine. Visio installs/opens/activates fine, but I can't get images or shapes to load. There is no shape library. I can only do lines and text. 

I'm using Lucid Lynx 10.04.
maybe theres a missing DLL so it cant work properly (this is just an idea!), when I setup wine I always install a lot of DDL's like visual basic and others, well you can try but you would need to know which DLL's Visio needs.

---

### Post by goltoof on 2010-07-13
> **mlentink said:**
> If so, you might want to consider either using a virtual machine to run windows/office, or dual booting. 
Do not, I repeat, do NOT try and run software on Linux that was originally written for an entirely different operating system. How many Windows software programs run on the Mac? Don't expect Ubuntu to be different. Just because Wine does run quite a few Windows programs doesn't mean it can run them all...

That's the current scenario, I use my rd for anything MSO.  But it's laggy, and dual booting is too inconvenient, unless I find some other reasons to use windows more often.

I have to say I'm tickled pink by your assumption that I think windows and linux software is ANYTHING alike and should "expect" things to work.

And telling me to just "give up" on using Wine is in all essence completely missing the purpose of this thread, imho.

It's almost there, I can do everything I need to except get images to load, it's most likely some setting or plugin to patch into wine, the question is what.

---

### Post by beastrace91 on 2010-07-13
> **mlentink said:**
> Do not, I repeat, do NOT try and run software on Linux that was originally written for an entirely different operating system. How many Windows software programs run on the Mac? Don't expect Ubuntu to be different. Just because Wine does run quite a few Windows programs doesn't mean it can run them all...

Thats horridly narrow minded. Wine is a fantastic piece of software that runs MANY Windows applications just fine on a Unix system. 

And FYI just as many Windows applications run on OSX as run on Linux - Wine works on both ;)

~Jeff

---

### Post by goltoof on 2010-07-13
> **gandaran said:**
> maybe theres a missing DLL so it cant work properly (this is just an idea!), when I setup wine I always install a lot of DDL's like visual basic and others, well you can try but you would need to know which DLL's Visio needs.

Thanks.  I'll try that and get back with what works.

---

### Post by beastrace91 on 2010-07-13
Also - regarding your issue - have you seen [this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16692&iTestingId=45299")?

It recommends installing gecko and msxml3 via Winetricks.

Also - Visio 2007 has a silver rating under Crossover 9.0 Might be worth trying the demo and see if it works for you. If so, it is well worth the 40$ :)

[http://www.codeweavers.com/compatibility/browse/name?app_id=2840](http://www.codeweavers.com/compatibility/browse/name?app_id=2840)

Regards,
~Jeff

---

### Post by goltoof on 2010-07-13
> **beastrace91 said:**
> 
It recommends installing gecko and msxml3 via Winetricks.

Tried that, still nada..

---

### Post by beastrace91 on 2010-07-13
> **goltoof said:**
> Tried that, still nada..

Have you tried Crossover as I suggested?

~Jeff

---

### Post by Mark Phelps on 2010-07-14
> **goltoof said:**
> I need to get Visio '07 working. I followed [directions]("http://ubuntuforums.org/showthread.php?t=1173365") for setting up Office 07 in Wine. Visio installs/opens/activates fine, but I can't get images or shapes to load. There is no shape library. I can only do lines and text. 

I'm using Lucid Lynx 10.04.

Well ... if you go BACK to the link I posted, click it, and then click the test results, you will find out what others did to get theirs working.

Apart from that, as others have said, your only option is to dual-boot or virtualize.

---

### Post by mlentink on 2010-07-14
> **beastrace91 said:**
> Thats horridly narrow minded. Wine is a fantastic piece of software that runs MANY Windows applications just fine on a Unix system.

If you want to call 'realistic' 'horribly narrow-minded' that's totally up to you.
I do not want to disparage the efforts of the Wine team, they're doing a fantastic job. But just because they're doing such a fantastic job does not mean. like I said,  that every windows app will run in Wine. And, as proven by the WineHQ AppDB, many don't.
Personally, rather than trying to shoehorn an app in an environment it was never made for, when I absolutely have to run a windows app, I run it in a windows-VM.

If it's your hobby, of if you enjoy trying to solve a puzzle, then obviously you should. I would like to suggest you post your comments on the AppDB, which now lists a total of 8 tests for Visio 2007, the majority of which couldn't get it to work properly. I appreciate the testers' efforts and their willingness to share their results.

---

### Post by Ctrl-Alt-F1 on 2010-07-14
I would try a virtual machine if you have a copy of windows you can use.  VMware player is free on their site for non-commercial use or you could use virtualbox.

I run all my "school" software as a Windows guest on a Linux host machine.  (SQL Server, Visio, Office, Visual Studio, etc.)

---

### Post by goltoof on 2010-07-14
> **mlentink said:**
> If you want to call 'realistic' 'horribly narrow-minded' that's totally up to you.  I do not want to disparage the efforts of the Wine team, they're doing a fantastic job. But just because they're doing such a fantastic job does not mean. like I said,  that every windows app will run in Wine. And, as proven by the WineHQ AppDB, many don't. Personally, rather than trying to shoehorn an app in an environment it was never made for, when I absolutely have to run a windows app, I run it in a windows-VM.  If it's your hobby, of if you enjoy trying to solve a puzzle, then obviously you should. I would like to suggest you post your comments on the AppDB, which now lists a total of 8 tests for Visio 2007, the majority of which couldn't get it to work properly. I appreciate the testers' efforts and their willingness to share their results.

I see your point in the benefits of running a pure windows environment for "full compaitbility" over your windows apps.  However, the virtual solution requires a lot more space plus the need to install the full OS, not to mention the degradation in system performance.  For the sake of practicality, Wine seems to be the best (free) solution for those who have "completely" switched over. 

There's a difference between "solving puzzles" and putting in some extra elbow grease to get these apps to work.  It only gets better for everyone else from taking the time to test it and make it work with more applications.  How far would it be now if everyone adopted your attitude to not even bother?

It's also worth pointing out, THIS THREAD is for figuring out how to get Wine to work with Visio 2007! There are plenty of other threads to discuss the pros/cons of using Wine itself.

---

### Post by goltoof on 2010-07-14
> **beastrace91 said:**
> Have you tried Crossover as I suggested?

~Jeff

CrossOver does work.. but, much like Wine, it's not a one-step install.  It's missing fonts among other things. And some of the controls native to Visio get replaced by the environment (ie, zooming in/out).

Still, it's a well rounded emu and worth the funds if I can't get it working in Wine.

Thanks for the tip!

---

### Post by archenroot on 2011-01-12
Visio 2007 Professional works under Crossover 9 but life of application is still very buggy.

---

