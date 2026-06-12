---
title: "I screwed up ubuntu tweak, how do I start over"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by geebob on 2009-04-22
I was following instructions on installing ubuntu tweak and I misunderstood a step.  Instead of adding to the source list the lines that were supposed to go there, I put those codes into the terminal.  So when I finished going through the instructions, nothing happened.  I tried to do it all again accept correctly but nothing happened.  I assume to start from the beginning, I need to undo everything I've done but I don't know how to do that.

---

### Post by PukingPenguin on 2009-04-22
It's a lot of fun to try to guess what you may have done, but I can tell you this:
If you put a url in as a command it won't do anything. 
No idea what else you did, since you don't say much about it.

---

### Post by geebob on 2009-04-22
Here's what I did.

I followed these instructions imperfectly:

> How to add the source of Ubuntu Tweak

open your terminal, first import the key:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FE85409EEAB40ECCB65740816AF0E1940624A220

type the command to run gedit(or other editor in your opinion) to modify the sources.list:

sudo gedit /etc/apt/sources.list

And put the two line into it(If you are using Ubuntu 8.04 Hardy or early) :

deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main

Or Ubuntu 8.10 Intrepid:

deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main

Or Ubuntu 9.04 Jaunty:

deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main

Then update the source and install or upgrade Ubuntu Tweak:

sudo apt-get update
sudo apt-get install ubuntu-tweak

if you have installed, just type:

sudo apt-get dist-upgrade

They come from this link:   [http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)



I'm very sure that what I did was that at the point where the instructions say "And put the two line into it," I understood "it" to be the terminal.  I was wrong.  I was supposed to put that code into the source list which pops up.

While there may be a simpler way to fix this, I assume that a sure way to fix this is just to undo everything that I've done and start over from scratch.  I've already started over from scratch and nothing happened.  I can't find any evidence that Ubuntu tweak is on my computer thus I assume that I need to undo what was done.

---

### Post by PukingPenguin on 2009-04-22
Yes, it appears that you are correct. There shouldn't be anything to undo because you've done nothing....

):P

---

### Post by geebob on 2009-04-22
For that matter, what didn't I do?  Why isn't this program on my computer as I did follow the instructions correctly a second time around.

After entering the last two commands, the terminal just sat there and did nothing.

If this program is on my computer, where is it?  I didn't see it in any drop down menu.

---

### Post by lhb1142 on 2009-04-22
> **geebob said:**
> I was following instructions on installing ubuntu tweak and I misunderstood a step.  Instead of adding to the source list the lines that were supposed to go there, I put those codes into the terminal.  So when I finished going through the instructions, nothing happened.  I tried to do it all again accept correctly but nothing happened.  I assume to start from the beginning, I need to undo everything I've done but I don't know how to do that.

:KS If you already have Ubuntu Tweak installed onto your computer, skip step 1 and proceed to step 2. (Ubuntu Tweak is found in "Applications->System Tools.") 

1) If you do not have Ubuntu Tweak actually installed do this: In the Ubuntu Tweak "Downloads" section, click, in "Deb package for all," < ubuntu-tweak_0.4.7-1~intrepid3_all.deb > and select the "Open with [your default archiver]" choice. This will install Ubuntu Tweak onto your computer.

2) Open Ubuntu Tweak and Click on "Applications;" this will open four sub-menus. Highlight "Third-Party Sources" and unlock it with your password (the same password you use to log into Ubuntu). Scroll down until you see "Ubuntu Tweak" [NOT - repeat NOT - "Ubuntu Tweak (Unstable Version")] and place a check mark in the selection box. This will add Ubuntu Tweak to your third-party software sources (you can check, if you wish, by going to System->Administration->Software Sources->[the tab] Third-Party Sources. In that you will see "Ubuntu Tweak" as one of the software sources (make sure it is checked).

You can add any of the Third-Party sources within Ubuntu Tweak to your computer's sources but I recommend that you tread carefully here. Add a selection only if you absolutely MUST have something listed there. I myself have only Canonical, Debian Multimedia, Medibuntu, Ubuntu Tweak, and Winff as third-party sources; I found that, when I had too many third-party sources, sooner or later I ran into incompatibilities and this caused unnecessary problems for which, on a couple of occasions, the only remedy was a complete reinstall of Ubuntu. (The sources I have installed have, thus far, caused no problems and allow me to have any program I could possibly desire.)

Please be careful. But you will find that Ubuntu Tweak is a VERY useful addition to your Ubuntu armamentarium. One of its most useful capabilities is in cleaning your computer of unnecessary programs after every update with "Update Manager" or the "Synaptics Package Manager;" to accomplish that cleaning, you go into Ubuntu Tweak, and then, under "Applications," go into "Package Cleaner." Unlock it with your password and, selecting each of the four options one at a time, clear them all. You need not be afraid of doing this; it works perfectly and frees up space on your computer.

I hope this is of some use to you. ):P

---

### Post by geebob on 2009-04-24
I tried the first step and I got this messeage:

"/tmp/ubuntu-tweak_0.4.7-1~intrepid3_all.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences."

The only option I had for a helper was "GDebi package installer (default)"

---

### Post by fooman on 2009-04-24
i followed the instructions you posted and it installed just fine on my fresh installation of jaunty 9.04.  :P

just remember that when you run the command "sudo apt-get update"...you are updating your ubuntu repositories.  if you are using jaunty,  that means it will be a slooow process as you wait for the repos to update.  ...there is quite a load on the servers atm, since jaunty was just released yesterday.

so after you run "sudo apt-get update"....give it a few minutes (took mine about 5-7 minutes) to finish updating before running the next command to install ubuntu-tweak.  after that,  it installed with ease and was in the menu under applications > system tools > ubuntu tweak.  if you do not find it there after the installations completes....just open a terminal and type:

```
ubuntu-tweak
```then post back with any errors that pop up (if any).

---

### Post by geebob on 2009-04-24
Thanks for the advice fooman and lhb1142.  I now have ubuntu tweak.

---

### Post by lhb1142 on 2009-04-24
> **geebob said:**
> I tried the first step and I got this messeage:

"/tmp/ubuntu-tweak_0.4.7-1~intrepid3_all.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences."

The only option I had for a helper was "GDebi package installer (default)"

:KS I'm glad you were able to get Ubuntu Tweak, a very useful program. For what it's worth, I suggest you go into your Synaptics Package Manager and, in the Quick Search box, type Gdebi. Make sure that all three choices are installed. ):P

---

