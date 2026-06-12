---
title: "Install from CD problems"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by Ericpode on 2010-04-26
Hi
First time I have tried to install Ubuntu so bear with me.
I had an install disk for 9.10 from a magazine. After several goes got no further than disk partitioning before install hung. Downloaded ISO image from Ubuntu site burnt disc and tried again, it still hangs up at some point in the process. This is regardless of which cd drive I use.
Currently run Windows XP, 4Gb of RAM, Intel Quad core CPU. I have an empty 80Gb disc for Linux.
Any suggestions would be appreciated.
Eric

---

### Post by Gone fishing on 2010-04-26
The obvious problem would be fault with the CD so that fails to copy file. I'd start by burning the iso again you can then on install select "check disk for defects" before completing the  installation.

---

### Post by P4man on 2010-04-26
The OP already made a new CD, so thats almost certainly not the cause.
Try running disk utility (palimpsest) from system > administation and see if it reports any problems with the harddisk. Im guessing the harddisk is the problem.

---

### Post by Ericpode on 2010-04-26
Thanks for the suggestions. Gave it one last go and it worked fine. Law of Sod strikes again.
Now Ubuntu is loaded and system can boot into Ubuntu it then asks about encryption and hangs up.

---

### Post by P4man on 2010-04-26
I still think its a bad drive. Run disk utility from the live CD and report the SMART status (assuming the drive supports smart)

---

### Post by Ericpode on 2010-04-26
Thank you
Persistence won the day in the end. Finally installed.
No internet connection yet.
Eric

---

### Post by P4man on 2010-04-26
Installing an OS, whether it is linux based or any other, is not something you have to try a few times until it finally works. If it doesnt work the first time, then something is really wrong and despite having it installed, you will not have solved anything. It will freeze again or lock up or not boot. Chances that you encountered some weird problem twice and now you will never encounter it again seem... small :)

IOW, check your harddrive. If its a 80GB drive, its probably old, and possibly dying.  its just 2 clicks to find out, and you wont be doing anyone (not in the least yourself) any favors to keep trying and posting questions about all sorts of problems if the root cause is a faulty disk (although its equally unlikely the hdd problem is related to a lack of network connectivity).

---

### Post by peterj on 2010-04-26
> **P4man said:**
> Installing an OS, whether it is linux based or any other, is not something you have to try a few times until it finally works. If it doesnt work the first time, then something is really wrong and despite having it installed, you will not have solved anything. It will freeze again or lock up or not boot. Chances that you encountered some weird problem twice and now you will never encounter it again seem... small :)

IOW, check your harddrive. If its a 80GB drive, its probably old, and possibly dying.  its just 2 clicks to find out, and you wont be doing anyone (not in the least yourself) any favors to keep trying and posting questions about all sorts of problems if the root cause is a faulty disk (although its equally unlikely the hdd problem is related to a lack of network connectivity).

I had a tonne of fails on my last installation. Standard ISO just failed the whole time. Alternative got caught up in copying.. 

Eventually I decided to download 10.4 and it worked a treat. 

Now you have me wondering!

---

### Post by P4man on 2010-04-26
> **peterj said:**
> I had a tonne of fails on my last installation. Standard ISO just failed the whole time. Alternative got caught up in copying.. 

Eventually I decided to download 10.4 and it worked a treat. 

Now you have me wondering!

Its entirely possible there was a problem with the 9.10 kernel and your hardware (acpi, sata, whatever), something solved in 10.04. Its only if you try installing the same OS several times and freezes a few times but eventually stays up long enough to finish the install, that you should expect more trouble and its certainly worth clicking a few icons to check common causes (like a bad hdd). 

I have no reason to believe *your* hdd is bad (but dont let that stop you from checking :) )

---

