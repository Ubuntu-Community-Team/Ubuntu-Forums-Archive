---
title: "Does Linux require periodic maintenance?"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-04-09
When I was in college, the Unix system always went down once a week or so for "scheduled maintenance".  I never understood what that meant.

Being essentially "Unix for the PC",  does Linux require something like that?  Are there things that need to be "cleaned" periodically?  Or would a simple reboot do it?

What about a web server (or file or print, etc) for example that would be on all the time?  Is that different?

---

### Post by djyoung4 on 2011-04-09
the only thing that is needed to my knowledge now is the updates which update manager takes care of.  The only time usually that a reboot is required is when you update kernels.  Other then that you should be good.  my htpc that has mythtv running has an uptime of 103 days right now.  I need to update the kernel soon though

---

### Post by NightwishFan on 2011-04-09
Not really. In some circumstances, such as after a version upgrade of a debian/ubuntu system you might want to autoclean the downloaded packages. They might take up a few gigs over time, and that is killer on a netbook.

As for common stuff on Windows such as defragging? No, the OS takes care of most of that for you.

---

### Post by jtarin on 2011-04-09
Scheduled maintenance could also mean the weekly backup.

---

### Post by rvchari on 2011-04-09
> **NightwishFan said:**
> Not really. In some circumstances, such as after a version upgrade of a debian/ubuntu system you might want to autoclean the downloaded packages. They might take up a few gigs over time, and that is killer on a netbook.

As for common stuff on Windows such as defragging? No, the OS takes care of most of that for you.

ailurus is a package that will be of help to you. ubuntu has lots of terminal commands whcih you can issue periodically to clear apt cache etc... but ailurus is one gui based software that will guide you thru all what you wish to do...

it also has some nice features like changing the start menu icon etc...

---

### Post by HermanAB on 2011-04-10
Linux maintenance is mostly automated by logrotate and other cron jobs, so you can leave it running for years on end with no down time.

---

### Post by Old *ix Geek on 2011-04-10
> **Learning Linux 2011 said:**
> When I was in college, the Unix system always went down once a week or so for "scheduled maintenance".  I never understood what that meant.There's no way to know exactly what that meant, without asking, that is. The sysadmins may have been doing backups (which wouldn't necessarily require downtime, unless they wanted to be sure nothing was being changed as the backups were happening), or various kernel/system updates, but the latter seems pretty unlikely on a weekly-ish basis. So I don't know. The *nix systems I ran were basically up all the time, except when I was installing new hardware or doing some kernel-related change. 
> Being essentially "Unix for the PC",  does Linux require something like that?  Are there things that need to be "cleaned" periodically?  Or would a simple reboot do it?

What about a web server (or file or print, etc) for example that would be on all the time?  Is that different?Linux is intended to run 24/7 and does not need the silly, time-wasting "care" windows does, such as defragging or rebooting to clear its...garbage. Once you have a Linux box running the way you want, you should be able to leave it running all the time, only shutting down to install hardware (if you're like me and don't want to get electrocuted! :)) and/or upgrading the kernel. There are rare occasions when you install something and it'll say the system needs a reboot, but again that's generally kernel related.

---

### Post by Learning Linux 2011 on 2011-04-10
Coming from Windows, that's hard to fathom, lol

We had to reboot our Windows servers at least twice a month and could never figure out why.

Maybe the weekly maintenance was for backups. Good point.

---

### Post by earthpigg on 2011-04-10
lots of exaggerating going on in this thread. for home desktop use, the thread is mostly on track.

your professor was probably not talking about unix/linux on the home desktop, though.

if you are managing a large database on linux, you will have some actual maintenance to do from time to time. *including defrag*, as i understand it: commonly done by backing up the entire system, putting the database parts into a tarball, copying it to another location, verifying integrity of the copy, deleting it from the original location, and copying it back, and verifying integrity again. there. database is 0% fragmented.

if you have a filesystem over 85% full, a few ultra-huge files, a zillion small files, and all of them being constantly modified (think: amazon.com)... ya, you are going to have fragmentation.

how often do you keep up on the mailing lists of the open source projects that are mission critical to your firm? has some new vulnerability come out that poses and immediate dire threat to your entire operation? may be a good thing to check up on from time to time, beyond waiting for a fix to get pushed downstream to you. if it is a critical enough vulnerability, maybe you need to take two of your mirrors systems off-line immediately (just in case) and start working on your own patch. checking mailing lists can be regular preventative maintenance.

and, software aside: all computer hardware requires regular maintenance. dusting, etc. if it's a huge cluster, verify that all fans are actually working. is the air conditioner in the room working good? what is the ambient temperature in the room? and in the center of that mass of technology?

---

### Post by earthpigg on 2011-04-10
the reason we have so little maintenance on our home ubuntu installs is because *we really don't do much with them*. we check facebook, we word process, we look at porn, we bicker on ubuntuforums.org, we compile gentoo from source, we play some vidya games, we play with python, we read the news... but really, nothing ***demanding*** - like processing millions of google searches per hour, keeping track of them, seeking patterns and correlations between them, maybe plotting the orbits of heavenly bodies or modeling a nuclear explosion or two...

even coordinating a playstation cluster to monitor the entire new york stock exchange and make dynamic predictions is more complex than what most of us ***do*** with ubuntu.

yes, that stuff above is demanding on hardware, but it is ***also*** demanding on software. how many of the top 500 supercomputers in the world use Windows or OS X? Exactly.

When most of us use Ubuntu, we're essentially using the Starship Enterprise to pick up groceries from the corner store. it'll be a while before we're due for our 5,000,000 lightyear tune-up and oil change, wont it?

---

### Post by HermanAB on 2011-04-10
Here is one of my web servers:
-bash-3.2$ uptime
 18:54:16 up 530 days,  6:00

So, depending on what the machine is doing, a Linux machine can run for multiple years with little/no manual maintenance or restarts.

Some systems execute incredibly long running jobs, for example seismic data processing, which can take several months.  So if you would reboot a server after 4 months in a 5 month process, you will be rather unpopular and would probably need to collect your pink slip. Don't try that with Windows though.

---

