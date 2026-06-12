---
title: "Can't install anything, using Software Center or Terminal"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by thewasteland on 2011-01-11
Running 10.10 (Maverick Meerkat), first time running Ubuntu and only installed it on Sunday.

Yesterday I tried to install Google Chrome from the website, but for some reason, once it got to installing in the Software Centre, it froze when the bar was at about 90% so I had to cancel it. Now, whenever I try installing something from the software centre, I click install and absolutely nothing happens. When I try in the Terminal, I get the same message every time:
""Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package google-chrome-stable needs to be reinstalled, but I can't find an archive for it."
This happens no matter what I try to install, even when I try to reinstall Google Chrome through Terminal.

Can anyone please help? It's rendered me completely unable to tweak my laptop.

---

### Post by TeoBigusGeekus on 2011-01-11
Have you tried purging it?
```
sudo apt-get purge google-chrome-stable
```

---

### Post by davidmohammed on 2011-01-11
try

sudo dpkg --remove --force-remove-reinstreq google-chrome-stable

in a terminal

---

### Post by thewasteland on 2011-01-11
> **davidmohammed said:**
> try

sudo dpkg --remove --force-remove-reinstreq google-chrome-stable

in a terminal
 
That did the trick, thanks a lot.

---

### Post by juliantchan on 2011-04-30
I think I have more or less the same problem as in above but with printer driver (mfc665cwlpr-1.0.1-1-i386.deb) installation the first time under Ubuntu v11.04. 
Below is the session log of rerunning the dpkg commands:
sudo dpkg -i --force-all mfc665cwlpr-1.0.1-1.i386.deb
[sudo] password for julian: 
Selecting previously deselected package mfc665cwlpr.
(Reading database ... 144459 files and directories currently installed.)
Preparing to replace mfc665cwlpr 1.0.1-1 (using mfc665cwlpr-1.0.1-1.i386.deb) ...
Unpacking replacement mfc665cwlpr ...
start: Unknown job: lpd
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
start: Unknown job: lpd
dpkg: error processing mfc665cwlpr-1.0.1-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
start: Unknown job: lpd
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 mfc665cwlpr-1.0.1-1.i386.deb
julian@julian-ThinkPad-T42:~/Downloads/Brother_Linux$

Try cleaning up the partially installed package with synaptic package manager, it always pops up the following:
E: The package mfc665cwlpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I am new to Linux, pls suggest what could be done at command level to fix the problem to let update manger continue.
Further, is there any procedure error I have committed for this installation?

---

