---
title: "Advice for a begginner"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by psy-moon on 2009-04-29
Greetings All,
 First I would like to thank the ubuntu team very much, I am very impressed with the development, and strongly relate to the ethos.

Now I wonder could any one give me some advice on how to deal with a number of problems I am having?

I will give some details on my situation.

First off I am a linux novice.

Over the last few years I have tried and failed to install both RedHat and Suzi on vacant machines.

I am pretty familiar with the various Windows up to XP I can cope with working in DOS and also have an of old Apple with Mac OS8.6.

Now Ive been longing to escape the tyranny of microsoft how ever I am rather fond of a few windows apps and seem stuck with some others.

My interest in computers stems from three main fields.

1. I work as an electrician and use a PC to keep track of all the documentation and certification involved. Most of this is just database stuff I use Office Access at the moment so I dont see why I shouldn't be able to migrate to open office. But I do use a tester that uploads test results via a USB virtual rs232 link. The software that communicates with the tester is windows specific.

2. Playing music is what I like to do and recording helps me practice. So I have the old free version of Protools5 running on the Mac and an old windows98 PC.
 I also use a newer XP box with a yamaha XG1000 soundcard/midi device to handle midi stuff. ( Ive got one of those ION drum kit things and a wind controler)

3. My other thing is flight simulators. Not only flying them but modding (3d modeling with GMax) I have various flavours from microsoft flight sim.

Now I have installed ubuntu to try it out. First using the wubi install on my main PC
(AMD Athlon 2.02GHz 1.5GB RAM NVIDIA GeForce FX5200 Via Mboard) its old I know but its also my newest machine. ( I dont buy new stuff because I think its way over priced here in the UK))

It works well, I installed Intrepid Ibex and up graded to Jaunty Jackalope. I have the NVIDIA driver installed and it seems to work ok. (I have a problem setting the resolution on one of my CRTs but I think it might be because the lead is missing a pin and  the PnP function isn't connecting. So I just get 800x640.

So feeling confident I moved on to do a clean install on an older machine I have.
(AMD Athlon 1GHz 512MB RAM ATI Radeon Via Mboard).
I want to set the machine up so my children can use it to surf and learn. 
I installed Intrepid Ibex and loaded the GCompris package. Fine.
I installed the upgrade to Jaunty Jackalope fine. 
Then I Itried to add a driver for the ATI grahic card to get 3d acceleration and heres were I ran into difficulties.

The driver did not work and locked the machine up. 
So I tried to boot from the CD but I could not figure out how to remove the driver.
 Ok thinks I,  well I havent any data on this machine to lose I'll just start again.
 And did a fresh install of Jaunty. Then installed GCompris. Now when I try and start the program. I see a notification in the status bar  "Starting GCompris" but then it just seems to give up.
Well I think "maybe its because I didnt install it into intrepid and then upgrade as I did before".
 So I load Intrepid into a separate partition and install GCompris on that, still wont start and further more Firefox seems to do the same thing.
Now I have not reported these events as bugs because I strongly suspect they are user induced. i.e my ****up.
So would any one offer any advice on any of the above?

---

### Post by muteXe on 2009-04-29
Hiya,
For number 1 (and 3 maybe?), have you looked at virtual machines? Google "Virtualbox" or "vmware".  I have ubuntu 8.04 on my laptop, but need to code c# in dev studio.  I've created a virtual xp within my ubuntu OS and installed dev studio for coding.  There's nothing to stop you doing the same and installing ms office, your software that communicates with your spreadsheet, or even your flight simulator (specs permitting).

mute

---

### Post by Moop on 2009-04-29
I think your older pc is a little under powered to run straight Ubuntu. Try installing Xubuntu or Qimo. I installed Qimo on a old dell for my 6 yr old and think it's great for kids. [http://www.qimo4kids.com/](http://www.qimo4kids.com/)

---

### Post by y_garti on 2009-04-29
if you have an application that you must run and only run on Linux can you do two things
1 install a virtual windows (vmware and etc..)
2 you can install wine (u can even run office 2007 on ubuntu with wine (but i prefer open office))

---

### Post by psy-moon on 2009-04-29
Thanks all, I shall digest...

---

### Post by Saghaulor on 2009-04-29
Using google with Ubuntu as part of your search term and the other part being what you're interested in doing always helps.

Also, try using the keyword search feature in Synaptic, the package manager in Ubuntu.

That's how I find all kinds of Windows replacements.

---

### Post by Mortus Pryde on 2009-04-29
> **psy-moon said:**
> So feeling confident I moved on to do a clean install on an older machine I have.
(AMD Athlon 1GHz 512MB RAM ATI Radeon Via Mboard).
I want to set the machine up so my children can use it to surf and learn. 
I installed Intrepid Ibex and loaded the GCompris package. Fine.
I installed the upgrade to Jaunty Jackalope fine. 
Then I Itried to add a driver for the ATI grahic card to get 3d acceleration and heres were I ran into difficulties.

The driver did not work and locked the machine up. 
So I tried to boot from the CD but I could not figure out how to remove the driver.
 Ok thinks I,  well I havent any data on this machine to lose I'll just start again.
 And did a fresh install of Jaunty. Then installed GCompris. Now when I try and start the program. I see a notification in the status bar  "Starting GCompris" but then it just seems to give up.
Well I think "maybe its because I didnt install it into intrepid and then upgrade as I did before".
 So I load Intrepid into a separate partition and install GCompris on that, still wont start and further more Firefox seems to do the same thing.
Now I have not reported these events as bugs because I strongly suspect they are user induced. i.e my ****up.
So would any one offer any advice on any of the above?

Still a novice myself and have Ubuntu on an IBM Thinkpad with an ATI video subsystem. I am running Intrepid with the 9.3 Catalyst till the open sourse drivers fully support my Radeon Mobility 9600 that is no longer supported under Catalyst 9.4 and so not currently supported properly for 3D in Jaunty.

One thing I would ask is have your tried just running with your origional configuration? Intrepid, proprietery driver and GCompris? Second it do you need 3D exceleration on the machine?

If you don't need 3D Exceleration and GCompris works fine with the open source drivers your can stick with Jaunty that way. If you absolutely need 3D Exceleration on that machine however sticking with Intrepid is your best bet for now.

The problem is Jaunty only works with the new 9.4 Catalyst driver and this driver dropped support for a good chunk if not all mid range cards not currently supported under open sourse drivers. I am sure the open sourse drivers will catch up eventually, but as of right now there is a gap in 3D support for Jaunty.

---

### Post by psy-moon on 2009-05-02
Ok I've found out what I did wrong with the old box. The ATI driver is for a modern card not the one I have so thats is why I messed that up.
All I needed to load was the synaptic packages python-opengl and python-gtkglext1 

When I reloaded intreped I did not pay attention to the size of partitions, the swap file was very small. Once I resized it GCompris and FireFox work fine.

So these aspects are solved.

I do not think my boxes are up to running virtual machines, Well the newest one may be but I understand that running Ubuntu through wubi is not very efficient so I will have to set up a dedicated drive for Ubuntu to run from. Thanks for the input. I shall no doubt return...

---

