---
title: "Watch and record tv"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by tony.morse on 2009-09-21
Ok, so there are loads of linux based home theater solutions out there BUT...

I've been banging my head against MythTV for ever now, I just cannot get it to work properly, I'll say what I've done and the problems I've had in a moment, but first my question is what other linux based options are there other than MythTV ???

And by other than MythTV I mean ones that don't just wrap MythTV in behind the scenes such as LinuxMCE, or if they do wrap up MythTV that do so in a way that I can avoid the problems I'm having with Myth...

So first my hardware...
Processor: Athlon XP 2200+ (old I know but up the job apparently)
Audio: Audigy (the original, so that'll only work with alsa and not pulse-audio)
DVB card: Hauppauge Nova T-500

So this is what I've tried and following are the problems I've had...
(I should mention I'm no Linux guru, but not totally inept either)
1) Ubuntu 9.04 + MythTV
. get rid of pulse audio and go back to alsa to get sound in ubuntu
. get the correct driver for the DVB card
. disable compiz so Myth is full screen rather than a backdrop
. set up MythTV

2) Mythbuntu  (nice, no setup needed for sound or DVB card!!)


Problems... 
with 1) and 2)
. only one DVB channel available (the Nova-T-500 is a duel card)
. scheduled recordings not recorded
. recordings (from live TV) include adverts
. no remote

with 2)
. small linux partition fills up with log files till full then nothing works

So...
I can configure MythTV to use the duel cards, set them following all the info on the net any which way and still only one card available and no scheduled recordings actually being recorded

I've been at this for months and really am fed up with MythTV there must be an alternative either to MythTV altogether or a distro that might work such as knopmyth or even LinuxMCE.

All I want to do is record TV, have the adds removed and watch at my leisure.  Before I spend another month failing to get another Myth disto to work can someone please advise me here.

Thanks loads in advance...

---

### Post by LowSky on 2009-09-21
> **tony.morse said:**
> 


Problems... 
with 1) and 2)
. only one DVB channel available (the Nova-T-500 is a duel card)
. scheduled recordings not recorded
. recordings (from live TV) include adverts
. no remote

with 2)
. small linux partition fills up with log files till full then nothing works   


Here Goes...

1. you need to set up both tuners, sounds odd, I know, but one will be tuner 0, the second tuner 2

2.  Check to make sure MySQL is running correctly and that the database is fine

3. recoding will include ads. no way around that, That is why fast-forward was created.

4. Do you own a remote? If no they are cheap, get the M$ one it works fine.

5 use the MthTV wiki
[http://www.mythtv.org/wiki/Main_Page](http://www.mythtv.org/wiki/Main_Page)

6. have you even tried Linux MCE, or Windows 7's media center?

---

### Post by lovinglinux on 2009-09-21
If you don't need to stream to other machines and just need a simple and lightweight media center for a single computer, then you could try my media center extension for Firefox, called [FoxMediaCenter](http://fmc.isgreat.org/).

It probably sounds weird to use a browser as media center, but it makes sense to me, since there is a lot of media services on the web and a lot of multimedia extensions for Firefox. Anyway, my extension allows you to schedule recordings, setup reminders, manage playlists, track watched programme, import xmltv data and more.

I'm not sure if it will work with your card, but I have improved the recording features recently to use mencoder, so I guess it is possible. I would appreciate a lot if you could test it and report if it works with your card.

[IMG]http://fmc.isgreat.org/images/stories/screenshots/FoxMediaCenter_3.0.3-001.jpg[/IMG]

---

### Post by tony.morse on 2009-09-22
Hi there, I'm not sure I understand all comments so here goes, one at a time....

> 1. you need to set up both tuners, sounds odd, I know, but one will be tuner 0, the second tuner 2
Ok so in Myth I've set up both tuners as DVB0 and DVB1, then one tv listings called freeview, and then 2 connections, DVB0->freeview & DVB1->freeview.  The connections use 'generic' in the input 1 and input 2 fields, both scan and find channels.  I've also tried 2 separate tv listings and seperate connections i.e. DVB0->freeview0 and DVB1->freeview1, then I get duplicates of every channel in the channels list but still ultimately only one tuner I can use for watching and recording TV.

So what do you mean tuner 0 and tuner 2 ??? is this the number I should use in setting up the cards (rather than 0 and 1) ???

> 2. Check to make sure MySQL is running correctly and that the database is fine
I've done this... ```
sudo dpkg-reconfigure mythtv-database
```
which seemed to fix recording while the frontend is on but not while the backend is on but the frontend off?

> 3. recoding will include ads. no way around that, That is why fast-forward was created.
Yes but Myth is supposed to be able to mark the adverts post-recording and then there should be a setting to automatically skip commercials.  If there is I can't find it

> 4. Do you own a remote? If no they are cheap, get the M$ one it works fine.
Yes, the Hauppage Nova-T-500 comes with a remote and it works fine in windows.  I'm guessing I need to set up LIRC or something and I remember getting it to work in linux when I got the card a couple of years back but I've followed the steps described online and it's not recognized at all, or rather it is recognized but no input from it is seen.

> 5 use the MthTV wiki
[http://www.mythtv.org/wiki/Main_Page](http://www.mythtv.org/wiki/Main_Page)
yup have been, there, here, and everywhere else

> 6. have you even tried Linux MCE, or Windows 7's media center?
Ok so windows is not an option for me.  I tried to install Linux MCE last night from the DVD image, but it throws errors saying: ERROR Partition expected, non found. and just stops after warning me that the disk will be scanned every 28 mounts or something.  The hard drive is fine, I can format it from my Mythbuntu install on the other harddrive and it seems ok.

I'm up for trying different things out but it seems everything is failing to work properly... any idea what might be the problem with linuxMCE? might try knopmyth tonight (though I like ubuntu and would prefer to be using that)

I'll check out foxmediacenter.

Thanks

---

### Post by tony.morse on 2009-09-22
bump

---

### Post by anaconda on 2009-09-22
I use kaffeine, and it just works

Then only thing I needed to do was to get the correct firmware file and copy it to /lib/firmware

and then after starting kaffeine I just scanned the channels and everything just works. (it is better to manually select the town/city you are in, because the "auto" setting had problems atleast in ubuntu 7.04..)

PS: I dont think you can skip commercials when recording with kaffeine.

PSS: I have a hauppauge usb tuner (dont remember the model but it is propably older wintv nova)

---

### Post by OffAxis on 2009-09-22
> Yes but Myth is supposed to be able to mark the adverts post-recording and then there should be a setting to automatically skip commercials. If there is I can't find it

While you're watching a recording the default button for commercial-skip is 'Z' or 'End'.

The menu for selecting commercial Auto-Skip can be brought up with the 'O' button.

The full listing of commands can be viewed here:
[http://www.mythtv.org/docs/mythtv-HOWTO-11.html](http://www.mythtv.org/docs/mythtv-HOWTO-11.html)

pay attention to the different sections; a key can have different meaning depending on what operation you're currently doing (i.e. watching live TV versus watching a recording).

Even if you don't install the mythbuntu version of myth, you should install the mythbuntu control center. There are a number of tools in there that make system management easier, like the lirc remote control configuration selector, or the mysql database optimizer.

```
sudo apt-get install mythbuntu-control-centre
```

I forget if that installs the lirc generator automatically. It's name is 
mythbuntu-lirc-generator

---

### Post by tony.morse on 2009-09-23
I have the myth control center in both my ubuntu and mythbuntu installs.  In both cases the lirc remote section lists my remote but fails to make it work.

I'll try the 'o' button, thanks for that! but still not so useful if I can't record anything but live tv

---

### Post by ranch hand on 2009-09-23
There is a dedicated Mythbuntu sub-forum here;

[http://ubuntuforums.org/forumdisplay.php?f=301](http://ubuntuforums.org/forumdisplay.php?f=301)

I have no idea how to help other wise, I intend to do Mythbuntu one of these days but I don't have the cards I need and I think I may just build a box for it.

---

### Post by OffAxis on 2009-09-23
> but still not so useful if I can't record anything but live tv 
So it's your scheduling that's pooched?
Does the program guide list programs correctly?

Is Schedules Direct an option ([http://schedulesdirect.org](http://schedulesdirect.org) )?They've got a free trial period of 1 week. $20 for the year is more than reasonable if it works.

setup for the guide data is done in the mythtv backend setup (and then run mythfilldatabase)


> In both cases the lirc remote section lists my remote but fails to make it work.

How exactly does it fail?
and what are you using as your IR receiver?

from a command prompt try typing

```
lircd -H ?
```

and make sure that your remote is listed as a possibility.
If it's not you can run

```
sudo dpkg-reconfigure lirc
```

and try selecting your remote. You should see the lirc service shut down before the reconfiguration tool launches. If it wasn't working at all it should list [fail] when it tries to shut down and (after the reconfig) again when it tries to start back up.

If the service starts up okay, then check your config files for lirc.
These two:
/etc/lirc/hardware.conf
/etc/lirc/lircd.conf

1. Try running 
```
irsend LIST "" ""
```

The name of your remote should be displayed (as it's defined in /etc/lirc/lircd.conf)

2.
/etc/lirc/hardware.conf
lists a path to the IR receiver somewhere in the /dev/ folder. Check and make sure that the reference is valid (sometimes receivers are brought up as as 0, sometimes as a 1). I've got one currently at /dev/iguanaIR/0.

3. If that all checks out then try running
```
irw
```
and see if your remote's keypresses are mapped correctly to what you think they are (as they are defined in /etc/lirc/lircd.conf)
(Ctrl-C will get you out of that)

4. If all of that checks out then the problem lies in your lircrc file. The old single massive lircrc file has been broken into pieces for the various multimedia programs and they live in your home directory in the .lircrc/ folder. If you've never mapped one out before it's pretty straightforward.

---

