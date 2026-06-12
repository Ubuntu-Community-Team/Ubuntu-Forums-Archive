---
title: "Linux!"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-20
Hi!.
I just came across a blog.. it was some review of Mandriva .. and the guy says that"Due to the strength of Linux, a typical Mandriva Linux system can run for months without a reboot.".. what does this mean.. what in linux makes this possible.. hope my question is clear...(and yes as you rightly guessed I am a newbie).. well I have never tried running windows for months without a reboot ...

---

### Post by SlickRick on 2010-04-20
You could run Ubuntu for about a week and you would gety a kernel update which requires a reboot. You can ofcourse choose not to and keep using the old one. There are several tools that allow you to install a kernel without a reboot, so it is technically possible to run a linux system untill the computer gives out.
The thing that makes this possible is that something would rarely crash and if it does, there are ways to recover form it without rebooting.

---

### Post by iponeverything on 2010-04-20
> **vivek40 said:**
> Hi!.
I just came across a blog.. it was some review of Mandriva .. and the guy says that"Due to the strength of Linux, a typical Mandriva Linux system can run for months without a reboot.".. what does this mean.. what in linux makes this possible.. hope my question is clear...(and yes as you rightly guessed I am a newbie).. well I have never tried running windows for months without a reboot ...

I have had systems up for more that a year. This one is not mine.. just one that I have an account on.

mayhem1 > uptime
  5:02am  up 460 days, 17:26,  1 user,  load average: 1.08, 1.02, 1.00

---

### Post by kwacka on 2010-04-20
One of the great strengths of Linux is its stability.

As your quote says, a computer can run for months without a need to restart. 

I did find this on 'Linux Today', dated February 1999 "The timer wraps in 497 days, 2 hours, 27 minutes, 52.96 seconds so this machine had been up 559 days, 21 hours and 28 minutes at the time of posting. That's about a year and a half. Add in the prior 440 hours and you get over 33 months with only 1 reboot due to external factors."

---

### Post by P4man on 2010-04-20
What makes it possible is a stable OS. The question would be what makes it impossible on other OS's to run for months without reboot, and that would be bugs or memory leaks or whatever (although as the poster above mentioned, if you run for months without reboot you will not have an up to date patched system).

In fairness though, back in the XP days perhaps this was a considerable difference between linux and windows, but recent windows releases will run just fine for extended periods of times just as well, provided you can keep them virus/malware free.

---

### Post by HermanAB on 2010-04-20
Hmm, I had a  web and mail server that ran for over 4 years without a reboot, until the power supply broke.

The best I ever managed with Microsoft was a 2003 server that ran for just over a year, before it broke.

So, how long you can run a system mostly depends on how well you configure it to begin with.

---

### Post by Fxy on 2010-04-20
I would assume that with windows if you kept it in order & skipped updates, you would be able to successfully run it for a long period of time...  Though without installing updates you system is more prone to infection etc etc...  There was a program back in the day for windows 98 that would allow updates to install without requesting the user to reboot, though it didn't seem to work very well haha...  To me with ubuntu, you can run it for long periods, but at times it can get a bit sluggish until you reboot the system...  Though with ubuntu you can always open terminal and use the stop commands to stop certain things and then restart them...

---

### Post by DrMelon on 2010-04-20
At my workplace, we have a machine that has been up for 6 years without rebooting. It's a marvel.

---

### Post by d3v1150m471c on 2010-04-20
> **DrMelon said:**
> At my workplace, we have a machine that has been up for 6 years without rebooting. It's a marvel.

I find it difficult to believe. You're saying a machine was left on and had no upgrades that required a reboot and that the power never went out, or Billy Lumpkin never spilled starbucks on it?

---

### Post by 3rdalbum on 2010-04-20
Every layer of Linux is fairly well isolated against the other layers. In Windows, if the GUI stops working then the problem will usually leak into the kernel and bring the system down. In Linux, the display server is just another program running on top of the kernel, with no direct links into kernel internals, so one program crashing should not bring the rest of the system down.

---

### Post by Fxy on 2010-04-20
> **3rdalbum said:**
> Every layer of Linux is fairly well isolated against the other layers. In Windows, if the GUI stops working then the problem will usually leak into the kernel and bring the system down. In Linux, the display server is just another program running on top of the kernel, with no direct links into kernel internals, so one program crashing should not bring the rest of the system down.

Thats what i like about linux compared to windows...  Whenever i used to run windows vista on my laptop, once one thing crashed the whole system then followed...  But now with linux once one thing crashes, one thing crashed not the whole system...  Thats the beauty of linux :)  I would also have to say the same with mac os x, its on a similar bases to linux...

---

### Post by Doug11 on 2010-04-20
It's great. I leave mine on for weeks at a time. Very rarely do you have to force quit a program.

---

### Post by Grenage on 2010-04-20
We have Linux installs that have been running for years without a restart, and we've also had Windows servers last years without a restart (2000-current).

---

### Post by Calash on 2010-04-20
I usually get 2-3 weeks from my work Ubuntu system.  My home system is nightly shutdown due to wanting to keep my power bill as low as possible.

I had a Gentoo server that went 2 1/2 years before a power outage took it down.  Simple Samba file share with no internet access so I kept it in a static state and never ran upgrades.

I know they have some where I work that are at least a year+.


We also have a few Windows systems that, barring power outages, will sit idle for a year or so before anybody thinks to reboot them.  Then they ask me what is wrong......REBOOT!!!  :)

---

### Post by ubunterooster on 2010-04-20
Our computer has been on for about six months now becase the dying motherboard usually makes USB devices invisible.> **d3v1150m471c said:**
> I find it difficult to believe. You're saying a machine was left on and had no upgrades that required a reboot and that the power never went out, or Billy Lumpkin never spilled starbucks on it?

A program like kexec was used for kernel updates and Billy was kept out of the room.
[The six years ended when somebody left the door unlocked and Billy walked in.] :lol:

---

### Post by Linuxforall on 2010-04-20
As long as one can keep the cacheset and memory clean on XP, it can also be run for a while but still Linux is far more stable.

---

### Post by dwarfolo on 2010-04-20
My backup server running Red Hat Enterprise
```
    ~ ---> uptime
 16:27:43  up 426 days,  1:00,  1 user,  load average: 0.00, 0.00, 0.00

```
My e-mail server running Slackware 9.1
```
    ~ ---> uptime
 16:26:56  up 276 days, 23:46,  42 users,  load average: 0.00, 0.00, 0.00
```
My samba file server running Slackware 9.1
```
    ~ ---> uptime
 16:22:43  up 183 days, 13:12,  123 users,  load average: 0.00, 0.00, 0.00

```
My Oracle database server running HP-UX B.11.11 
```
# uptime
  4:20pm  up 326 days,  1:14,  1 user,  load average: 0.05, 0.04, 0.03
```

*nix power!

---

### Post by uRock on 2010-04-20
> **vivek40 said:**
> Hi!.
I just came across a blog.. it was some review of Mandriva .. and the guy says that"Due to the strength of Linux, a typical Mandriva Linux system can run for months without a reboot.".. what does this mean.. what in linux makes this possible.. hope my question is clear...(and yes as you rightly guessed I am a newbie).. well I have never tried running windows for months without a reboot ...
If you are running Jaunty or Karmic, you could go months without a restart also. The only release getting weekly updates requiring restarts is Lucid, because of development. Windows itself may actually make it a long time without a restart, but the constant updates to AV and such will require an update. Hell, Between Adobe and AVG I have to restart after updates run almost every time I boot Windows. A real motivator to not boot it. Nothing like booting up and getting started on something just for the system to want a restart.

---

### Post by vivek40 on 2010-04-20
I had posted the same topic in Kubuntu forums too and there is somebody named GreyGeek who posted this and believe me it is worth reading:-
(posted by GreyGeek on Kubuntu Forums)
"An historical side note:

In the early 90s distros like SuSE, for example, introduced "repository" management applications like YAST, for example, but these were primarily for installing applications that were on the CD that one purchased from various sources.   Most folks used dialups and did not have the connection speed (bandwidth) to download 700MB or 4GB of an iso file in order to burn an installation CD.  BTW, these CDs were installation CDs,  not LiveCDs, which hadn't been invented yet.   Also, kernel and application upgrades did not appear as frequently as they do today.  New applications were individually downloaded from the Internet from sites like RPMBone and installed one at a time.  IF a dependency was encountered it was downloaded and installed, repeat, wash, spin, until one could finally install the desired application.  Sometimes, trying to install one dependency would conflict with dependencies required by other applications, thus preventing one from installing the new application without doing a major overhaul of one's system.  For this conflict the term "Dependency Hell" was created.

It was not uncommon for one to install Linux from a purchased CD onto their PC and never do another reinstall for months or even years.   At work I installed SuSE 6.4 as a PostgreSQL server and it ran non-stop for 465 (IIRC) days before I had to bring it down in order to plug in an errant Unix drive from a Kodak Image maintenance system.  We created 50kb jpg images of all incoming paper documents and stored them on the Kodak Unix system.   When the Kodak system experienced problems the clerks would just reboot it without unmounting it.  After a  few weeks (months?) the system experienced an abend from which it could not recover.  The IT guys tried several of their tricks trying to pull the images off of the HD, but they couldn't get DOS to see the indexes or the images.  They knew I knew Linux so they brought the HD by and asked if I could mount it on my Linux server and pull the info off.  Fortunately, Linux includes the ability to mount Unix systems.   I used the dd command to pull the HD image off in one big 1GB text file.  Then I used PFE (a lightening fast text editor which could scan the entire 1GB file in a few seconds) to capture and correlate the indexes with the jpg image files.  I succeeded in recovering over 95% of the images.   Some of the images were 15 years old (that's how long the Kodak system had been running) but even then, because of lawsuits and legal issues, access to any particular image could be required at any time.

After that task I removed the Kodak HD and rebooted.  The SuSE system continued to run for another 135 or so days before I installed RH 3.0 on it and set it to doing other purposes.

During that period of time there was an ongoing debate in the newsgroups about which system had the longest uptimes, Linux or Windows?   Linux users were reporting up times in excess of 400 days.   Windows users were reporting similar up times in those flame wars.   Then, Microsoft announced the 49.7 day clock bug, a bug which automatically REBOOTED the Windows OS when its clock  counter reached 32767, which took 49.7 days.   All those Windows users claiming months of uptime had egg on their face, and their claims were revealed as obvious lies.  That was the end of the uptimes flamewars."

---

### Post by Calash on 2010-04-20
> 
Then, Microsoft announced the 49.7 day clock bug, a bug which automatically REBOOTED the Windows OS when its clock counter reached 32767, which took 49.7 days. All those Windows users claiming months of uptime had egg on their face, and their claims were revealed as obvious lies. That was the end of the uptimes flamewars."


I would argue this on both Win2000 and WinXP.  Despite our best efforts we have many systems that are ether never touvhed until they are needed or used so often the clients feel the need never to reboot them.  Though our efforts have helped alot I have personally run into many systems with up time far exceeding the 49 day quote.

Most of the systems were in bad shape.  Even small memory leaks in applications turn into huge issues after that amount of time.  Pending patch reboots do not make things much easier.


Side note:  Looking for more information on this 49.7 day reboot and all I can find are some bugs from Windows 95, 98, and NT.  That probably explains why I have never seen it in 2K or XP.

---

### Post by P4man on 2010-04-20
I cant even find a reference of this bug in NT. Only 95 and 98 (and I would consider it small miracle to have a windows 95 machine run more than a few days without reboot anyhow).

Nice story, but dont believe everything you read on the web ;)

---

### Post by spillin_dylan on 2010-04-20
> **vivek40 said:**
> I had posted the same topic in Kubuntu forums too and there is somebody named GreyGeek who posted this and believe me it is worth reading:-
(posted by GreyGeek on Kubuntu Forums)
"An historical side note:

In the early 90s distros like SuSE, for example, introduced "repository" management applications ...  <snip>

To be fair, he definitely said early 90's, and even with a few years' of uptime on his Linux machine, I'm sure that wouldn't be any later than Windows 98.  I'd even bet this was probably more during the Windows for Workgroups 3.11 and eventually Windows 95 era....

---

### Post by vivek40 on 2010-04-20
Again by GreyGeek on Kubuntu forums:-(hate this copy paste activity , but after reading his post, I felt it was really worth sharing)...

""At work I used to leave my Linux PostgreSQL server on 24/7/365 and my Windows workstation on 24/7.  I soon gave up on leaving the Windows box on because it would either lock up or crash during the night (even though it was unused) and I had to reboot it in the morning.  I also noticed that the greater the number of days it was up the slower it got and the more likely I'd have a crash, especially when I was running several apps or using large amounts of memory.    When 9/11 hit and energy became a concern I started shutting my Windows workstation off at quitting time.  Rebooting every day my XP OS rarely locked up or crashed, and it was alway much quicker than when it had been running for several days.

Two things changed department policy during the last five years of my employment:  1)  we replaced desktops with laptops, and the IT support crew noticed that when folks shut down their Windows workstations every night they gave fewer problems, and 2) workstations that were off didn't have locks on applications and databases which would  prevent automatic backup systems that ran every night from making backups of our applications and data.

At home, before 2005 I used desktops and left them on 24/7 for convenience.  Running Linux there never was a problem with lockups, crashing or slowdowns.   One day, while looking around at my three computers, three CRT monitors (one a 27 inch), one laser printer and one bubble jet printer, a scanner, cable modem and passive router, I wondered how much power they were consuming.    IIRC, it was around 3 Kw.  Even at 7 cents/hr the monthly bill was over $150.  I checked with my wife and she said our electric bill was almost $250/month.       I replaced my desktops with 100 watt laptops and the printer with an ML-1210 laser printer, which I turned on only when I needed to print.   I replaced the scanner with a 3-in-one HP all-in-one and turn it on only when I need to.  I turn off the laptop every night and rarely have it on more than 12 hours a day.  My wife uses her laptop  only an hour or so a day.  Now, our the portion of our electric bill due to our computers is less than $3/month, and my electric bill rarely goes over $76/month.""

---

### Post by Dayofswords on 2010-04-21
> **Calash said:**
> 

Side note:  Looking for more information on this 49.7 day reboot and all I can find are some bugs from Windows 95, 98, and NT.  That probably explains why I have never seen it in 2K or XP.
[http://support.microsoft.com/kb/216641](http://support.microsoft.com/kb/216641)

i dont run a server, so i shut down everyday
uptime right now -0 days, 0 hours, 0 minutes, 0 seconds

i'm current on my windows part =p

---

### Post by Calash on 2010-04-22
> **Dayofswords said:**
> [http://support.microsoft.com/kb/216641](http://support.microsoft.com/kb/216641)

i dont run a server, so i shut down everyday
uptime right now -0 days, 0 hours, 0 minutes, 0 seconds

i'm current on my windows part =p


That KB is only for 95 and 98.  The 2007 time was probably to reflect the EOL of 98 by providing a final patch for the issue.

---

