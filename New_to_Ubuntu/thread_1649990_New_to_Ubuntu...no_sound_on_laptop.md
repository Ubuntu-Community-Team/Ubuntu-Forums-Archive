---
title: "New to Ubuntu...no sound on laptop"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by Laser835 on 2010-12-20
Hi to all. and thank you.  I am trying to stay the heck out of microsoft windows and all new to Ubuntu which seems so great.  I have loaded Ubuntu 10.10 on a usb stick and I'm trying it out on my laptop.  When I go to YOU TUBE I get video but NO sound.  The speaker on the laptop is on, because I get the startup beep and it works when I play YOU TUBE from Windows 7 on this laptop.   I have checked the Ubuntu sound preferences and it shows output volume at 100%.  I am missing something obvious, but I am a novice, trying to learn.  Can you help?  I am not sure...do I need to down load something like Adobe Flashplayer for Ubuntu?  Is there such a application?   Thanks for your patience and help.
Please be specific...I'm not a programmer, but I'm a fast learner.  Happy holidays.

---

### Post by CensoredBiscuit on 2010-12-20
Hey Laser835,

There is a flash player for ubuntu available in the software center in the applications menu, if installing that doesn't help...

Can you listen to local music or is it just youtube.

Otherwise I would do a search for restricted drivers.
system>administration>additional drivers

---

### Post by Laser835 on 2010-12-20
Thanks for your reply...I have a music cd inserted and the audio disc icon has appeared on the screen...it has opened the RHYTHM BOX MUSIC PLAYER from the Ubuntu applicationand I am trying to start the playback, but it has no audio...the track counter is counting up the time.  I suppose this is the best place to start to try to get sound from a cd...before I even try the internet...idea?
Thanks

---

### Post by garvinrick4 on 2010-12-20
Download this package so you get flash and all your gstreamer codec's for sound
and video, java and other in this package.
Open a terminal:
```
sudo apt-get install ubuntu-restricted-extras
```### Must open Software Sources and check the multiverse repository.
You need main,universe,multiverse and restricted. partners also.
# if you have problem getting to software sources go to System to Admin to Synaptics to Settings tab to repository:

---

### Post by Laser835 on 2010-12-20
Ok..making progress...thank you for your patience while I downloaded the restricted extras...the cd now reads on screen..tells me the names of the musical tracks, but still NO sound.  I have checked that the SOUND PREFERENCES shows that "Rhythmbox" is output volume of 100 percent...the darn cd is running, changing tracks, just no sound...something's not enabled yet...I guess?  Continuing to pick your brain please if you are still awake.  Thank you.

---

### Post by garvinrick4 on 2010-12-20
#Log out and back on or reboot first to see if that does it.
#Click on sound applet and choose  sound preferences, make sure
nothing is on mute.

---

### Post by Laser835 on 2010-12-21
Hi and thanks...it appears that even though I've rebooted, and checked my preferences, there is still NO audio with the Ubuntu OS.   The Windows 7 on this same laptop does have audio.  I'm at the point this evening that I'm wiped, so I will ask for help on this forum again this week.  I want to thank you for your advice so far.  I know that there's lots of experience out there and that ubuntu is a good OS.  I'm learning and tonite at least I was able to learn about the add'l downloads.   Have a really good evening, and happy holidays!

---

### Post by garvinrick4 on 2010-12-21
> **Laser835 said:**
> Hi and thanks...it appears that even though I've rebooted, and checked my preferences, there is still NO audio with the Ubuntu OS.   The Windows 7 on this same laptop does have audio.  I'm at the point this evening that I'm wiped, so I will ask for help on this forum again this week.  I want to thank you for your advice so far.  I know that there's lots of experience out there and that ubuntu is a good OS.  I'm learning and tonite at least I was able to learn about the add'l downloads.   Have a really good evening, and happy holidays! You have a Merry Christmas and a Happy New Year also.
There are a lot of Users with sound experience. It is nothing major so hit this thread
again when you have time and at every new reply it is bumped to front of forum so can
keep same thread. Here below is a web site from Ubuntu on Sound Trouble shooting!!
[https://wiki.ubuntu.com/DebuggingSoundProblems#Basic%20troubleshooting](https://wiki.ubuntu.com/DebuggingSoundProblems#Basic%20troubleshooting)

---

