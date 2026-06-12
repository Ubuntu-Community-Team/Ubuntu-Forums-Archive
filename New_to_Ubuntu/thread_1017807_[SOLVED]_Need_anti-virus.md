---
title: "[SOLVED] Need anti-virus"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-21
My sister has vista on her laptop, and it's horribly messed up. Can't install things, use certain programs, update certain programs, etc. I want to scan it via live-cd. What's a good AV for linux that would scan the computer thoroughly?

---

### Post by Dedoimedo on 2008-12-21
Here's a great forensics distro:
[http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)

It also has a Windows mode...

You may also want to try Ultimate Boot Cd for Windows:
[http://ubcd4win.com/](http://ubcd4win.com/)

Got a tutorial for it, if you want ...

Cheers,
Dedoimedo

---

### Post by Tom--d on 2008-12-21
AVG for Linux.

Install it on the LiveCD (Will only install to RAM) and run it as Root.

[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl) (download the .deb)

Edit:

Just double click the .deb and it will install for you. (Of course follow the on screen instructions, well, one :D)

---

### Post by adobrakic on 2008-12-21
> **Dedoimedo said:**
> Here's a great forensics distro:
[http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)

It also has a Windows mode...

You may also want to try Ultimate Boot Cd for Windows:
[http://ubcd4win.com/](http://ubcd4win.com/)

Got a tutorial for it, if you want ...

Cheers,
Dedoimedo

Thanks, but these seem way more complicated than just simply downloading a anti-virus. I'm not even sure what the first one is, other than another ubuntu mod.

---

### Post by Account1 on 2008-12-21
Yes AVG.

---

### Post by tiky on 2008-12-21
> **Tom--d said:**
> AVG for Linux.

Install it on the LiveCD (Will only install to RAM) and run it as Root.

[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl) (download the .deb)


yes, but how does one install this .deb file? just double click ?

edit: and how to install it in the LiveCD?

---

### Post by adobrakic on 2008-12-21
Yeah, your system will install it for you.

---

### Post by northern lights on 2008-12-21
> **tiky said:**
> yes, but how does one install this .deb file? just double click ?If the gdebi package installer is installed, yes. If not, install it first.

Alternatively you could used *dpkg* via the shell. Your choice.


P.S. You don't need an Antivirus. Your sister needs a Linux distro. Just my 2 cents.

---

### Post by ercferret18 on 2008-12-21
another option would be to boot in safe mode and run the online scanner at "housecall.trendmicro.com"

---

### Post by Gone fishing on 2008-12-21
You can clean Vista - but as the viruses will have added registry settings etc, I feel that even cleaned it will be messed. I'd reinstall Vista - dual boot with Ubuntu or Mint and encourage your sister to use Linux, maybe try Crossover office.

If she is going to continue with Vista I'd go for NOD32 as an AV

---

### Post by tiky on 2008-12-21
> **northern lights said:**
> If the gdebi package installer is installed, yes. If not, install it first.

Alternatively you could used *dpkg* via the shell. Your choice.


P.S. You don't need an Antivirus. Your sister needs a Linux distro. Just my 2 cents.

dpkg -i avg75fld-r51-a1243.i386.deb    

then how do i point it to the web page where the application is found?

---

### Post by adobrakic on 2008-12-21
> **northern lights said:**
> If the gdebi package installer is installed, yes. If not, install it first.

Alternatively you could used *dpkg* via the shell. Your choice.


P.S. You don't need an Antivirus. Your sister needs a Linux distro. Just my 2 cents.

I'm sorry, but this forum really has an elitism problem. Linux is not for everyone, and my sister is the case.

---

### Post by Gone fishing on 2008-12-21
> I'm sorry, but this forum really has an elitism problem. Linux is not for everyone, and my sister is the case. 

I don't think the first point is true this has to be one of the most supportive forums. 

On the second point I agree to a point, some people needed applications that are only found in Windows, however, if your sister is simply not very good with a PC, Linux might suit her well, a nice stable system with the apps she needs (this could include MS Office) that wont get viruses or be hijacked and she can do her online banking etc in full confidence. 

If she must use Vista (which I find counter intuitive) format and use NOD32.

---

### Post by northern lights on 2008-12-21
> **adobrakic said:**
> I'm sorry, but this forum really has an elitism problem. Linux is not for everyone, and my sister is the case.

I could not disagree more.

If there was a problem with elitism you're question would get answered by "just f*cking google". Countless redundant threads are meticulously answered on a daily basis even though a forum search or a google query would yield gazillion answers.

As for Linux not being for everyone:
Not all proprietary software vendors offer Linux versions. But that's it. If you know Linux averagely well, you can set up a machine for a monkey, give it a user account and it can't break the system.
I bought a new comp for my mom (HS teacher) about half a year ago. Vista pre-installed. Around every two weeks she'd call me cause something didn't work, make me "come over" (120 km!) and fix her system. 11 weeks ago to the day, I got too frustrated and installed Ubuntu on her system, gave her a user account with limited privileges and what do you know - no issues since. Now I come for tea once a month and not to fix some crap OS.

You see, your statement has been sent ad absurdum.

---

### Post by pdtpatrick on 2008-12-21
First off you will want to either use knoppix live cd or ubuntu live cd and then try to scan the entire drive ... though its never really safe to say that you have completely cleaned the system of malware .. because it still exists in registry or better yet it could be hidden and then eventually it will hit the computer again because the vulnerabilities have already been exposed.

You might want to reinstall vista as my guess is your sister is not going to have time or patience to learn linux nor will you want to troubleshoot it everytime she needs something installed or uninstall and more. 

I would recommend Clam AV or NOD32 and AVG Free version. I always install AVG on windows computers that i fix that arent part of corporate network.

---

### Post by handydan918 on 2008-12-21
> **adobrakic said:**
> I'm sorry, but this forum really has an elitism problem. Linux is not for everyone, and my sister is the case.

Sounds like the actual case may be that Vista is not for everyone, and you sister is the case....



:lolflag:

---

