---
title: "Installing SPSS 18 for Linux in Ubuntu 10.04"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by Kurtber on 2010-07-16
Hello,

I have searched the forum and can't find this problem mentioned anywhere. I assume there is a simple solution to it, but I'm stuck. 

I have just installed the statistical software SPSS 18 for Linux on my Ubuntu 10.04 (netbook), following a guide from the SPSS support pages. The installation folder on my computer is /opt/SPSSInc/PASWStatistic18/. 

According to the installation manual I am supposed to be able to start the program by "brows[ing] to the *bin* subdirectory in the installation directory" and "run[ing] the *spss* file". But there is no SPSS file, and none of the executable files there seem to work whether I try to open them in Terminal or outside.

Does anyone else have experience with installing (and running) SPSS 18 on Ubuntu? 

Thank you in advance for your assistance.

---

### Post by silentrebel on 2010-07-16
If the installation showed any signs of anything going wrong at any point, I would suggest you start from scratch (uninstall and reinstall).

If not...  Any executable in any of the bin directories accessible to you should not require you to navigate to that bin to run that executable.   They should be accessible with their name only, from the command line...  That's the whole point of these bin directories...  So try this, from anywhere on your computer, in the terminal:

```
spss
```

If that doesn't work, the bozos either did not put the spss executable in a bin directory or did not make it an executable.  You could try looking around for this file in likely places like this:

```
find /opt spss 
```
or 
```
find / spss | grep -i bin 
```

Sifting and sorting through the results yielded by these commands could take a while, but that's all I can think of for now.  

When you have found a likely suspect, try running it (simply specifying it from the command line with it's entire directory path).  If that fails, try 
```
chmod +x /path/to/file 
```
before trying to run it. 

If that doesn't work, your suspect is not the one you are looking for...

Perhaps other people in the spss community have had this problem and can suggest a more specific solution?

Good luck,
Nuagerebelle

---

### Post by Kurtber on 2010-07-17
Thank you for your helpful reply!

I had no luck searching for spss, sadly. I will keep searching for a solution, though. Maybe I've failed to notice an error occurring, and a complete reinstallation would be the way to go.

---

### Post by k3lt01 on 2010-07-17
Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1531916")

---

### Post by Kurtber on 2010-07-21
Thank you for your help! 

I have now completely reinstalled the program, and I've found the executable (/opt/SPSSInc/PASWStatistics18/bin/STATISTICS), after interpreting [COLOR=RoyalBlue][a German walk through (http://wiki.ubuntuusers.de/SPSS)]("http://wiki.ubuntuusers.de/SPSS")[/COLOR].

It still doesn't work, though. When I try to start the program, I get a small (seemingly Java run) splash window that suddenly disappears with no further action. When I try to start STATISTICS through Terminal, I get no error messages, so I have nothing to work at.

Following the German walk through I've installed *libstdc++5* and made sure *bc* is installed, so dependencies should theoretically not be the problem. According to [the link k3lt01 tipped me about (http://bas-r.nl/?p=10)]("http://bas-r.nl/?p=10"), I should disable desktop effects/compiz. But as far as I can see, there are no special desktop effects available on my system (I'm running 10.04 Netbook Edition), and compiz is not installed.

---

### Post by k3lt01 on 2010-07-21
Can you use PSPP instead of SPSS? PSPP is Linux native, so you don't need WINE, and it is in the repositories.

---

### Post by bodhi.zazen on 2010-07-21
> **Kurtber said:**
> Thank you for your help! 

I have now completely reinstalled the program, and I've found the executable (/opt/SPSSInc/PASWStatistics18/bin/STATISTICS), after interpreting [COLOR=RoyalBlue][a German walk through (http://wiki.ubuntuusers.de/SPSS)]("http://wiki.ubuntuusers.de/SPSS")[/COLOR].

It still doesn't work, though. When I try to start the program, I get a small (seemingly Java run) splash window that suddenly disappears with no further action. When I try to start STATISTICS through Terminal, I get no error messages, so I have nothing to work at.

Following the German walk through I've installed *libstdc++5* and made sure *bc* is installed, so dependencies should theoretically not be the problem. According to [the link k3lt01 tipped me about (http://bas-r.nl/?p=10)]("http://bas-r.nl/?p=10"), I should disable desktop effects/compiz. But as far as I can see, there are no special desktop effects available on my system (I'm running 10.04 Netbook Edition), and compiz is not installed.

If you are running the netbook edition, try running a standard gnome session instead.

---

### Post by k3lt01 on 2010-07-21
> **Kurtber said:**
> According to [the link k3lt01 tipped me about (http://bas-r.nl/?p=10)]("http://bas-r.nl/?p=10"), I should disable desktop effects/compiz. But as far as I can see, there are no special desktop effects available on my system (I'm running 10.04 Netbook Edition), and compiz is not installed.Ummmm. I never gave that link.

---

### Post by Kurtber on 2010-07-22
After getting in touch with the IT support at my university, I managed to start the program by a simple tcsh wrapper script they wrote. According to them, it seems the program just won't start in bash (this goes a bit beyond my competence). 

My new problem now is the interface, which seems not to work. The toolbar is completely missing. I can edit which icons are supposed to be there, but the toolbar does not show. In addition the program does not open SPSS files (.sav) that even PSPP easily opens. Once again I get no error messages and have nothing to work at.

Thank you for helping me with this! It is a bit frustrating, as I would have thought that Debian tested software should work fine in Ubuntu, but I might be a bit optimistic? The SPSS people only guarantee that the software works in Red Hat and Debian 4.0.


**Replies**
> **bodhi.zazen]If you are running the netbook edition, try running a standard gnome  session instead.[/quote]

I tried all possible sessions. No effect, but thank you for the tip!

[quote=k3lt01]Can you use PSPP instead of SPSS? PSPP is Linux native, so  you don't  need WINE, and it is in the repositories.[/quote]

SPSS is used in the courses that I am taking, and to make my life as  simple as possible I'd prefer having the same software as my lecturers.  SPSS/PASW Statistics is also Linux native (as of v16 and forwards), and  I'm not (as far as I understand) using WINE. But I do have PSPP  installed, and principally I would really prefer it - but until I've finished my courses and know what I'm doing I'll have to stick to what is safe  said:**
> Ummmm. I never gave that link.

Oops! No, that was a link from the thread that you tipped me about... :D

---

### Post by Kurtber on 2010-07-25
:KSSuccess!:KS 

I was using the wrong executable. When I start the program with "paswstat" in stead of "STATISTICS", everything works as it is supposed to - except that I can't show the program window maximized. That's a minor problem though, and probably can't be easily fixed? 

Thank you for helping me out!:D

---

### Post by bodhi.zazen on 2010-07-25
> **Kurtber said:**
> :KSSuccess!:KS 

I was using the wrong executable. When I start the program with "paswstat" in stead of "STATISTICS", everything works as it is supposed to - except that I can't show the program window maximized. That's a minor problem though, and probably can't be easily fixed? 

Thank you for helping me out!:D

Fantastic =)

---

### Post by beew on 2010-07-31
I know this is an old thread but just came upon it and would like to offer my 2 cents.

First, SPSS does have a native Linux version so there is no need to run it out of wine.

Secondly

> **k3lt01 said:**
> Can you use PSPP instead of SPSS? PSPP is Linux native, so you don't need WINE, and it is in the repositories.

But it is also garbage. 

Take a look at their menu and compare that to SPSS's and you will know why it is in no way a replacement for SPSS.  If I were the developers I wouldn't make that claim, it only makes them look like a bunch of fools.  Maybe in a few years it can close up the gap, but not now, not even close. (Aside: SPSS is hardly the best stat software out there)

It can do some descriptive statistics, two sample t test (not even ANOVA) and its most advanced feature is multiple regression (but no logistic regression)

If may be sufficient for someone taking a first year stat course and just wants a glorify spreadsheet to play with, but it is not up to the task for any advanced course, let alone real statistical analysis. Speaking of spreadsheet gnumeric (also in the repo) has more statistical features than PSPP.

R is definitely the best statistical software package out there (much better than SPSS, I mean SPSS, not PSPP) and it is FOSS. But don't get it from the offical repo as you don't get the updates. Download from their repo, here is the instruction

[http://cran.r-project.org/bin/linux/ubuntu/README](http://cran.r-project.org/bin/linux/ubuntu/README)

More about R
[URL="http://cran.r-project.org/"]
http://cran.r-project.org/[/URL]

There are quite a few good introductory stats books using R. Just have to google them.

---

### Post by leng2 on 2011-08-02
**Hai,my toolbar also does not show. May I know how you solve this problem?**



> **Kurtber said:**
> After getting in touch with the IT support at my university, I managed to start the program by a simple tcsh wrapper script they wrote. According to them, it seems the program just won't start in bash (this goes a bit beyond my competence). 

My new problem now is the interface, which seems not to work. The toolbar is completely missing. I can edit which icons are supposed to be there, but the toolbar does not show. In addition the program does not open SPSS files (.sav) that even PSPP easily opens. Once again I get no error messages and have nothing to work at.

Thank you for helping me with this! It is a bit frustrating, as I would have thought that Debian tested software should work fine in Ubuntu, but I might be a bit optimistic? The SPSS people only guarantee that the software works in Red Hat and Debian 4.0.


**Replies**


I tried all possible sessions. No effect, but thank you for the tip!



SPSS is used in the courses that I am taking, and to make my life as  simple as possible I'd prefer having the same software as my lecturers.  SPSS/PASW Statistics is also Linux native (as of v16 and forwards), and  I'm not (as far as I understand) using WINE. But I do have PSPP  installed, and principally I would really prefer it - but until I've finished my courses and know what I'm doing I'll have to stick to what is safe ;)



Oops! No, that was a link from the thread that you tipped me about... :D

---

### Post by Kurtber on 2011-08-03
> **leng2 said:**
> **Hai,my toolbar also does not show. May I know how you solve this problem?**

If you can't see the toolbar, try starting the program using the "paswstat" executable, rather than "STATISTICS". Ref. this earlier post in the thread:

> **Kurtber said:**
> :KSSuccess!:KS 

I was using the wrong executable. When I start the program with  "paswstat" in stead of "STATISTICS", everything works as it is supposed  to - except that I can't show the program window maximized. That's a  minor problem though, and probably can't be easily fixed? 

Thank you for helping me out!:grin:

This is a Norwegian language help page that might be of help - if you understand Norwegian, that is..: [https://it.uib.no/SPSS_i_Linux_Ubuntu_10.04](https://it.uib.no/SPSS_i_Linux_Ubuntu_10.04)

---

