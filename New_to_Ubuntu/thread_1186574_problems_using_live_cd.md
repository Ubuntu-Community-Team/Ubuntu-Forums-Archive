---
title: "problems using live cd"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by ranmaofborg on 2009-06-13
I am attempting to use the live cd of ubuntu but am having difficulties. I really would like to use linux since windows vista has been freezing up a lot (mostly when I view pictures). I want to try it before installing.   I have acquired 7.04 and and 8.1, I use dial up so I can't really download the newest version.   I've tried it on my new pc as well as my old pc. I have no problems on the old pc, it loads up and looks kind of like windows, fairly easy to use. On the new pc all I get is the command prompt: ubuntu@ubuntu~$:  and says something about root and sudo.  Old pc Hp 256mb ram, 733 mhz  New PC Medion 3 gigabytes ram, 2.10 ghz  How do I get the graphical interface similar to windows that shows up on the older computer, instead of the command line interface?

---

### Post by briguy47 on 2009-06-13
> **ranmaofborg said:**
> I am attempting to use the live cd of ubuntu but am having difficulties. I really would like to use linux since windows vista has been freezing up a lot (mostly when I view pictures). I want to try it before installing.   I have acquired 7.04 and and 8.1, I use dial up so I can't really download the newest version.   I've tried it on my new pc as well as my old pc. I have no problems on the old pc, it loads up and looks kind of like windows, fairly easy to use. On the new pc all I get is the command prompt: ubuntu@ubuntu~$:  and says something about root and sudo.  Old pc Hp 256mb ram, 733 mhz  New PC Medion 3 gigabytes ram, 2.10 ghz  How do I get the graphical interface similar to windows that shows up on the older computer, instead of the command line interface?


I've had a similar issue with the LiveCD.  It seems pretty sparse, but it happens. 

When the command prompt comes up, try typing:

```
startx
```Let me know if that helps! :D

---

### Post by ranmaofborg on 2009-06-14
I just tried that and it did not work.

---

### Post by s.fox on 2009-06-14
Hi and welcome to the forums,

> 
 On the new pc all I get is the command prompt: ubuntu@ubuntu~$:  and says something about root and sudo.  
Can you please post the exact error message.     That way we can establish exactly what the problem is :)

Thanks,

-Ash R

---

### Post by halitech on 2009-06-14
sounds to me like it doesn't like your video card. Do you know what you have for a video card? if not, post the output of ```
lshw -C video
``` after you log in with the username and password you setup during the install.

---

### Post by wpshooter on 2009-06-14
1) Try to run/install using "safe video mode" parameter.

2) If that does not work, then more likely than not, you need to somehow get a copy of the ALTERNATE (text based) CD verion of the Ubuntu ISO, to do the installation from.

But I sure would not want to try that on dial-up.  See if you can find a friend or perhaps you are not barred from doing it at work where you might have a high speed Internet connection (but ask before you attempt to download it at work - some of those more snootly IT types are stingy with their bandwidth).

---

### Post by ranmaofborg on 2009-06-15
I do not have a job involving computers, no computers at work.

I found the answer via an irc group elsewhere, but thanks for the replies. It was my video card. Now I just have to figure out how to get it to connect to the internet via dial up (already read about having to install a program that supposedly will work). I do not have cable TV (too expensive) and dsl not available where I live.

---

