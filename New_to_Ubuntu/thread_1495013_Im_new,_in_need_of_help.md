---
title: "Im new, in need of help"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by LabRat85 on 2010-05-27
Ok, first off as the title says, im new, not brilliant on a computer but obviously wanting to learn, i wanted to learn some security and stuff so i bought a book called HACKING: The art of exploitation 2nd ed, which comes with a live cd, however when i try to start it up it comes up with an error message saying
 
/bin/sh: can't access tty; job control turned off
(initramfs)
 
 
Any way i can fix this?
You will have to explain exactly what i need to do step by step because i wont understand technical terms
Thanks

---

### Post by libssd on 2010-05-27
Here's a better starting point (no CD required):  *Ubuntu Pocket Guide and Reference*, by Keir Thomas. It's available as a free PDF download at: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Re your question, google for bin/sh: "can't access tty; job control turned off"

Long discussion of this problem here: [http://www.linuxquestions.org/questions/ubuntu-63/bin-sh-cant-access-tty;-job-control-turned-off-474493/](http://www.linuxquestions.org/questions/ubuntu-63/bin-sh-cant-access-tty;-job-control-turned-off-474493/)

---

### Post by LabRat85 on 2010-05-27
Would i be able to keep windows if i get another OS?

---

### Post by wojox on 2010-05-27
Sure, you can either install Wubi or dual boot. If you want to learn about Linux find a good book on Linux not Hacking.

---

### Post by ibuclaw on 2010-05-27
> **LabRat85 said:**
> Ok, first off as the title says, im new, not brilliant on a computer but obviously wanting to learn, i wanted to learn some security and stuff so i bought a book called HACKING: The art of exploitation 2nd ed, which comes with a live cd, however when i try to start it up it comes up with an error message saying
 
/bin/sh: can't access tty; job control turned off
(initramfs)
 
 
Any way i can fix this?
You will have to explain exactly what i need to do step by step because i wont understand technical terms
Thanks

Hello and welcome to Ubuntu forums.

Judging from the error message you've given. Try the following:

[LIST=1]
[*]When at the initial loading screen for the LiveCD, press **F6** to access more options.
[*]Add the following line to the options list:
```
break=top
```
[*]Press enter to start booting.
[*]Ubuntu should start booting, but will stop at a command prompt. At this prompt type in these two commands:
```

modprobe piix
exit

```
[/LIST]

Report back if the LiveCD continues to boot properly after performing this procedure.

Regards

---

### Post by LabRat85 on 2010-05-27
Wubi or dual boot means nothing to me, dont understand
i understand "sure" though haha

---

### Post by ibuclaw on 2010-05-27
> **LabRat85 said:**
> Wubi or dual boot means nothing to me, dont understand
i understand "sure" though haha

Wubi is an Ubuntu installer for Windows users that allows you to install and uninstall Ubuntu like a Windows application, in a simple and safe way. See [http://wubi-installer.org/support.php](http://wubi-installer.org/support.php) and [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) for troubleshooting.


Dual boot instructions:
x86/AMD64: [https://help.ubuntu.com/community/WindowsDualBootHowTo](https://help.ubuntu.com/community/WindowsDualBootHowTo)
MACs: [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) [https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot)


Regards

---

### Post by LabRat85 on 2010-05-27
> **ibuclaw said:**
> Hello and welcome to Ubuntu forums.
 
Judging from the error message you've given. Try the following:

[LIST=1]
[*]When at the initial loading screen for the LiveCD, press **F6** to access more options.
[*]Add the following line to the options list:
```
break=top
```
[*]Press enter to start booting.
[*]Ubuntu should start booting, but will stop at a command prompt. At this prompt type in these two commands:
```

modprobe piix
exit

```
[/LIST]
Report back if the LiveCD continues to boot properly after performing this procedure.
 
Regards
 
 
This worked a treat, thanks loads, been trying for ages and asking around but to no solution, now im off to read the guide to see what i can do :)

---

### Post by ibuclaw on 2010-05-27
> **LabRat85 said:**
> This worked a treat, thanks loads, been trying for ages and asking around but to no solution, now im off to read the guide to see what i can do :)

No probs. Do you mind if I mark this thread as 'SOLVED'?

You can do it yourself by going to "Thread Tools" and "Mark this thread as Solved".

Regards
Iain

---

### Post by LabRat85 on 2010-05-27
done

---

### Post by rewyllys on 2010-05-27
> **LabRat85 said:**
> Ok, first off as the title says, im new, not brilliant on a computer but obviously wanting to learn, i wanted to learn some security and stuff so i bought a book called HACKING: The art of exploitation 2nd ed, which comes with a live cd, however when i try to start it up it comes up with an error message saying
 
/bin/sh: can't access tty; job control turned off
(initramfs)
 
 
Any way i can fix this?
You will have to explain exactly what i need to do step by step because i wont understand technical terms
Thanks
I'm glad to see that you got an answer to your immediate problem.

I'd like to respond to your more general desire to learn about Linux in general and Ubuntu in particular.  Here are three books that I've found really useful for me as a newbie since I started in earnest with Ubuntu last summer:

1. "Ubuntu for Non-Geeks: A Pain-Free, Project-Based, Get-Things-Done Guidebook", Third Edition (2008 ), by Rickford Grant. This is an extremely readable book that takes you in easy steps from the very beginning till you will feel quite comfortable using Ubuntu Linux. Many of the projects that the author describes are things that you will want to add to your Ubuntu installation; some you may not want to bother keeping; but ALL of the projects will illustrate ways to accomplish a variety of things involved in using Linux. The book truly merits the word "Guidebook" in its title, and its 336 pages cover Ubuntu up through version 8.04. (The fourth edition, based on v. 10.04, is to be published in June 2010.)

2. "Beginning Ubuntu Linux", Fourth Edition (2009), by Keir Thomas and Andy Channelle with Jaime Sicam. Another very readable book, this goes into more detail than does the Grant book. Using this (before I discovered Grant's book), I found that it covered every problem I had encountered in my first trial installation of Ubuntu--the trial in which, I need to confess, I made a number of stupid mistakes. Had I read Chapters 4-6 of Thomas-Channelle-Sicam prior to that trial installation, it would have been smooth sailing. The 764 pages in "Beginning Ubuntu Linux" explain just about everything I can imagine wanting to know about Ubuntu 9.04. (The fifth edition, based on v. 10.04, is to be published in July 2010. Keir Thomas has also written "Ubuntu Pocket Guide and Reference", which is available as a handy paperback book and also as a downloadable file: [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html) ).

3. "Linux in a Nutshell: A Desktop Quick Reference", Sixth Edition (2009), by Ellen Siever, et al. This is a fine reference book on Linux in general, including, for example, the most readable presentation of Linux commands of which I am aware. I find myself looking through its 944 pages (which include a detailed index) whenever the previous two books happen not to cover a topic to the depth that I would like.

---

