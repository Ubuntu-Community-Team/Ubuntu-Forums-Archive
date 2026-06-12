---
title: "Firefox issue?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by adeyb on 2009-02-24
Hi 
I'm really new to this so be gentle with me please!
Im trying to play Dark Orbit in ff the login page and home pages all work ok but when i click on start to launch the star map nothing happens! all i get is javascript void in the status bar at the bottom of ff. 
ive installed the flash plug in and jre but this hasn't helped!
ive also dissabled the pop up blocker
can you advise me guys?  ):P

---

### Post by Ripose on 2009-02-25
Are you using Firefox 3.06?

---

### Post by adeyb on 2009-02-25
no its version 2.0.0.21pre

Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.8.1.21pre) Gecko/20090209 Ubuntu/7.10 (gutsy)

---

### Post by Ripose on 2009-02-25
Add the Linux Mint to your repositories, it contains Firefox 3.06, which has fixed a number of java issues.

Binary (deb)
URI: [http://packages.linuxmint.com/](http://packages.linuxmint.com/)
Distribution: Felicia
Section(s): main upstream support

---

### Post by adeyb on 2009-02-25
great! how? lol ;)

---

### Post by mkvnmtr on 2009-02-25
I don't think you need to add mint repositories. I have Firefox 3.0.6 on Ubuntu 8.10 and I believe you just have to uninstall your Firefox 2 and go to add and remove or the package Manager to install firefox 3. Athen it should upgrade to 3.0.6 if it is not that version that you down load it the first place.

---

### Post by redseventyseven on 2009-02-25
Hi adeyb,

I see from your profile that you're listed as using Ubuntu 7.10 Gutsy Gibbon - is that the case?

I would recommend that you upgrade to a newer version - it's not going to be long before Gutsy is no longer officially supported. [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)

---

### Post by cristian_b on 2009-08-27
I have the same problem while running firefox 3.0.13 and buntu/8.04 (hardy).
As far as I know, this is the highest version of firefox available for ubuntu.
Strange, the game works fine under windows and i don't have other problems whith flash in ubuntu.

---

### Post by epsolon77 on 2009-08-27
> **cristian_b said:**
> I have the same problem while running firefox 3.0.13 and buntu/8.04 (hardy).
As far as I know, this is the highest version of firefox available for ubuntu.
Strange, the game works fine under windows and i don't have other problems whith flash in ubuntu.

If I have read the rest of the thread correctly, it would not be a flash problem, it would be a java script or firefox interpretation of java problem.  You may want to test your JRE, or update your JRE to 6 and see if that helps.  However I do not know the requirements of this specific site.

---

### Post by cristian_b on 2009-08-30
I have tested JRE at this site:
[http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")
Currently i am running the highest version of JRE available. Also, found that others are having trouble at the same spot, under ubuntu. From what i see, the problem is not solved under ubuntu 9.04.
See this link:
[http://en.board.bigpoint.com/darkorbit/showthread.php?t=132645]("http://en.board.bigpoint.com/darkorbit/showthread.php?t=132645")

I also tend to think that the problem is the firefox interpretation of java...

---

### Post by epsolon77 on 2009-09-02
> **cristian_b said:**
> I have tested JRE at this site:
[http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")
Currently i am running the highest version of JRE available. Also, found that others are having trouble at the same spot, under ubuntu. From what i see, the problem is not solved under ubuntu 9.04.
See this link:
[http://en.board.bigpoint.com/darkorbit/showthread.php?t=132645]("http://en.board.bigpoint.com/darkorbit/showthread.php?t=132645")

I also tend to think that the problem is the firefox interpretation of java...

Sorry for the delay, have you tried killing java 6 and rolling back to 5?  I know that's not something you'd normally do, but hey, bugs happen.  You can also try reinstalling firefox and the java plugin for firefox.  I haven't played around with these issues in Ubuntu specifically since the release of JRE 6, but it worked for me under 5 once.  You are right that it could be a bigger issue with Ubuntu itself, or I guess more the compile of java for ubuntu.  Which brings me to one more option.  Don't use the repository version of java and try to compile it on your own, or use the DEB on sun's website, if there still is one.  Sorry for the unresearched response, don't have much time at work this week.

---

