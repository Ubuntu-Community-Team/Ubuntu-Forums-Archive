---
title: "Accessing C$ folders"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by xtremesupremacy3 on 2008-04-21
Ok I know usually the accessing of Windows folders is easy as pie and never had a problem with it, however this is different and also kind of new to me.

My uncle, at who's house I currently stay, runs Windows XP and myself run Ubuntu Hardy on my laptop both on same network. 
Now heres the problem, some dumb@ss did whatever it was to XP and now when you log in, it logs straight out, almost as if 30 day trial has expired, which it can't have since it was registered. So I thought I'd take a look using good old Ubuntu. This is how theyre layout of the network on their pc is: "Admin$; C$; D$; D; and SharedDocs" And as you probably guessed I can access all without the $ symbol. so thats D and SharedDocs.

Now my question is this; When I try to connect to the other files and it asks me for username, domain and password and then doesnt accept it. Is there any way or tool I can use to gain access for means of checking whats killing their XP?

Thanks
Arthur

---

### Post by thevoidreturns on 2008-04-21
Quick question, have you tried safe mode in WinXP yet?

If you can, open up msconfig and check under the Startup tab what programs are starting. First, try deselecting them all and then restart windows. Then turn things back on one at a time.

It sounds to me its one of the following:

1. Misconfigured driver
2. Spyware/Malware
3. Program crashing causing an explorer exception

If all else fails have you thought about using a live cd on the problematic machine?

Hope this helps
Adam

---

### Post by xtremesupremacy3 on 2008-04-21
I kinda thought the same, 

I tried the usual, safe mode (same story), then I tried to go back to last settings that worked (same problem), sign in as Administrator (Same story). So I though I'll do a live CD, but then it gets worse...their cd drive doesnt seem to want to pick it up, i tried Ubuntu 6.04, 7.04, 7.10...nothing, even Utimate Boot CD...but doesnt really read it. So it wont do much if I was to format it because then I couldnt put XP back on

---

### Post by thevoidreturns on 2008-04-21
What have you done to try to access your admin shares?

Have you thought about removing the hdd and put it into your other machine and copy everything over?

Can you access any normal shares without problem?

---

### Post by xtremesupremacy3 on 2008-04-21
All normal shares are easy to access and work great.

See problem is that I run on a laptop and they run on a PC, and I dont have the tools to connect their HD to my laptop

---

### Post by thevoidreturns on 2008-04-21
Do you have a Windows XP disk by any chance?

---

### Post by xtremesupremacy3 on 2008-04-21
Yeah I have that one too, but their CD drive doesnt boot it from bootup. I checked BIOS but seems that its a cd drive hardware issue

---

### Post by thevoidreturns on 2008-04-21
Ok basically found some info that could be causing your problem. Not sure if it is or not but it sounds like it.

[http://www.allpostnews.co.uk/i12/Userinit%20problems%20windows%20xp%20logs%20off%20immediately%20after%20log%20on.php](http://www.allpostnews.co.uk/i12/Userinit%20problems%20windows%20xp%20logs%20off%20immediately%20after%20log%20on.php)

Scroll down to Num 5.

If you can't boot off the CD can you boot of floppy's? You can download windows xp boot disks and you could access the recovery console then.

---

