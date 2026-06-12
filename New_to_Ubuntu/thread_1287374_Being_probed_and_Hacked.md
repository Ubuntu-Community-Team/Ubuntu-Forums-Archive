---
title: "Being probed and Hacked"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by Hamma Hedd on 2009-10-10
Being probed and Hacked......

I engage in "civil standings of great import" (huge internet fights) against some pretty corrupt organisations....

AND they don't like it.

AND I have been using the Firestarter Firewall, and of late a few bad things have happened.

(several days and nights of crazy day night sleeping and programming)

One of my websites needed a HUGE backup and that got stored away in a certain folder through a specific pathway.

And after some "severely leaking firefox" type activities and a forced shutdown and reboot,  there appeared a FULLY opened and full sized folder containing all the website pages - immediately after starting and then the PC started to bog down and become unuseable..... (it may have had something to do with 400 items on the desk top - the slowness not the hacking that is)

Anyway I moved all the excess off the desk top and then rerouted the folder to a different location so that the script searching for it, wouldn't be able to find it.

Now immediately after booting I am getting a pop-up saying, "Could not find "/home/username/folder/folder/Backup Website". Please check the spelling and try again.

And I am thinking there is a script searching for this folder and to open it, running on my system and I didn't organise it.

I have tried some searching - with the Dolphin and the regular searcher - with two terms - seperately "Could not find" and "/Backup Website".... including binaries; and I found some linking files... nothing installed, created or modified in the last few days tho.

Not having much luck; Found a few files like "net" and "qmake" but I was unable to open them to read their contents - because in Windoze speak, the usual idea of using a good text editor to open and read almost anything - doesn't seem to be a forte of Linux.

Yeah so any ideas on how to "drill into" my own system to find the file executing the script and how to stop it, AND how to track it back to it's source - IF it has been planted?

---

### Post by theozzlives on 2009-10-10
vi should be able to open any file, it's a command line program and hard to use.

---

### Post by ibuclaw on 2009-10-10
```
ps -elf
```
Will tell you all running processes on your system.

If you suspect that your system has been compromised, probably won't work though, and you'll have to write your own ps app.

---

### Post by 3rdalbum on 2009-10-10
This sounds like one of the classic paranoia thread. "They" are "hacking" you through a firewall and causing odd behaviour?

See:

[http://www.linuxquestions.org/questions/linux-newbie-8/help-me-shutdown-localhost-please-606409/](http://www.linuxquestions.org/questions/linux-newbie-8/help-me-shutdown-localhost-please-606409/)

[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-machine-has-malware-and-spyware....need-help-692261/page2.html#post3384587](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-machine-has-malware-and-spyware....need-help-692261/page2.html#post3384587)

---

