---
title: "Virtualbox hanging up on shutdown in ubuntu?"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-08-30
idk if i can get  any help, on this issue i am not sure if it in VB or Ubuntu.
when ever i try to shutdown VB go's to 70% then freezes and i cant get rid of it unless i shut down my computer manualy by holding in the power button, nothing else wiill shut down ubuntu. thanks for any thoughts!

---

### Post by pedro3005 on 2009-08-30
CTRL ALT F1 then kill it via terminal (killall virtualbox i guess). If even that won't work, hold ALT, hold Sys Rq (Screenshot) and type REISUB. It'll restart, so you won't have to manually shutdown. Now, about fixing that problem, i don't know.

---

### Post by R3fr4cti0n on 2009-08-30
lol well thax sorta

---

### Post by pedro3005 on 2009-08-31
If the process is not virtualbox, 'ps aux | grep box'. If it doesn't find, just run 'top'.

---

### Post by miki147 on 2009-09-02
> **R3fr4cti0n said:**
> idk if i can get  any help, on this issue i am not sure if it in VB or Ubuntu.
when ever i try to shutdown VB go's to 70% then freezes and i cant get rid of it unless i shut down my computer manualy by holding in the power button, nothing else wiill shut down ubuntu. thanks for any thoughts!

I have the same problem so I'm going to 'bump' the forum hoping someone knows what to do.   

In my case it started after I upgraded to Karmic Koala (Alpha 4) and then the latest VB update for linux i386, so it could be either the buggy OS or the new VB.  Anyway does someone have a temporary fix?

FYI:  you can also add an icon to one of your panels (right click on a panel and click "add" near the top; then look down the list to the icon that says it will force misbehaving programs to quit.  Once it's on the panel, I use it instead of rebooting.  :popcorn:

---

### Post by diablo75 on 2009-09-02
I was having the same problem.  Here's what I've figured out so far:

The problem is somehow related to the use of sound devices by the system.  If you use Virtualbox at the same time as another program that is producing sound, it seems to cause a lock up while shutting down the VM.  The VM I have is currently set to use PulseAudio for output.  During some experimenting, I found that if you set it to ALSA, the entire VM would crash before it could even boot.  I also found that if you disabled sound on the VM completely, the system would never crash or lock up.  It also seems that often times if I use a program to make sound prior to starting my VM up (even if the first program has been closed), the VM will boot WITHOUT SOUND, even though it's set to use PulseAudio.  If that happens, it would certainly lockup during shut down.

I have resorted to running the VM first thing after logging into Ubuntu if I intend to use it for any sound related purposes (in my case, I need Windows Media Player for certain videos that VLC cannot play, despite using the w32codecs and ubuntu-restricted-extras packages).  In the event the VM locks up, I just hit Alt-F2 and type "xkill", then use my mouse pointer to click on the VM and it will kill virtualbox.

This bug seems to have cropped up recently and I don't think it's related to the version of VB I'm running.  I first started having it while running VB version 2.x, and upgraded to 3.0, but the problem remains.

---

### Post by miki147 on 2009-09-02
> **diablo75 said:**
> I was having the same problem.  Here's what I've figured out so far:

The problem is somehow related to the use of sound devices by the system.....


That's very interesting.  I happen to have a lot of crash reports regarding the PulseAudio on my system.  I'll start there and see what happens.  If I run across anything I'll give a shout.

THANKS for the reference!  :D

---

### Post by miki147 on 2009-09-02
> **miki147 said:**
> That's very interesting.  I happen to have a lot of crash reports regarding the PulseAudio on my system.  I'll start there and see what happens.  If I run across anything I'll give a shout.

THANKS for the reference!  :D


DUDE!!  That works for me.  I switched the audio setting in VB's Host Audio Driver to "OSS Audio Driver" and kept the Audio Controller to ICH AC97.  (I also have ubuntu hardware set to CA016 Analog Surround 5.0 output, which I did NOT change).

VB Win sound works great, and it turned off without a hitch.  That worked for me, Thanks again!

---

