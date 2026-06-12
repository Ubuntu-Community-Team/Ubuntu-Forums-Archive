---
title: "Problem with greeter application using Netbook Remix"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by stape on 2009-04-26
Hi, I am posting here as well as launchpad in case anyone with a similar problem finds their way here first. The launchpad question is at:

[https://answers.edge.launchpad.net/netbook-remix/+question/68727](https://answers.edge.launchpad.net/netbook-remix/+question/68727) 

**************************

I have had some problems since installing updates to a Toshiba NB100 running 8.04 I bought last week:

There was no sound after the update and as a result of a bit of searching I found a guide, I tinkered around and did something that resulted in the loss of Gnome desktop: (see extract from guide below), from:

 [http://ubuntuforums.org/showthread.php?t=205449&highlight=gstreamer](http://ubuntuforums.org/showthread.php?t=205449&highlight=gstreamer)

-----------------------------
Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop

(3) Reboot

-----------------------------

I had to reinstall this. Once I had done this the way the netbook started up was different with a log in screen that I never had before. That is OK but now I get this message:

"The greeter application appears to be crashing, attempting to use another one." and some type of 'hang'.

I have now the sound working but need to sort this greeter problem.

The thread with the initial problem is here:

[http://ubuntuforums.org/showthread.php?t=1129937](http://ubuntuforums.org/showthread.php?t=1129937)

I would really appreciate some help, I don't mind how the system starts, I just need it to do it 1st time, rather than hanging and me having to press the power button to switch off then back on again.

---

### Post by stape on 2009-04-26
...Fixed but not sure how exactly:

After six or so goes of "The greeter application appears to be crashing" and clicking OK I had a new screen telling that "Something bad is happening" and something about "waiting two minutes".

I ended up with a new picture of a Hardy Heron and the screen seemed to revert to the day I bought the netbook with a request to input my name,
 create a password and choose which city I am in etc.. 

After this the whole thing is working great and boots up OK (have tried it three times now)...

I think the answer was to go to the startup manager panel and select something to do with starting with the last used version of software.

...at least that is what I think happened.

Maybe someone can shed a little more light on this.

---

### Post by alcCapone on 2009-05-16
I'm using a normal ubuntu (no netbook remix) and after the last update and reboot I'm facing a similar "**The greeter application seems to be crashing**" problem. 

When that message window appears I can klick **OK**. After klicking **OK** the screen turns black and has some blue stripes on the right of my screen and the message window returns. After I klicked **OK** several times *gdm* started anyway. ;)

Things that got updated yesterday were:


[LIST]
[*]foomatic-db-engine (4.0.0-0ubuntu6.1)
[*]libmysqlclient15off (5.1.30really5.0.75-0ubuntu10.2)
[*]mysql-client-5.0 (5.1.30really5.0.75-0ubuntu10.2)
[*]mysql-server-core-5.0 (5.1.30really5.0.75-0ubuntu10.2)
[*]mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2)
[*]udev (141-1.2)
[*]metacity-common (1:2.25.144-0ubuntu2.1)
[*]libmetacity0 (1:2.25.144-0ubuntu2.1)
[*]libudev0 (141-1.2)
[*]metacity 1:2.25.144-0ubuntu2.1()
[*]pm-utils (1.2.2.4-0ubuntu5)
[/LIST]

---

