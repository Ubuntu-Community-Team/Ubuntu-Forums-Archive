---
title: "Sound Recorder"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by worksofcraft on 2009-06-07
I want to record from microphone.

Have set up System, Preferences, Sound so all Sound playback devices are Autodetect and the Sound capture is ALSA, ande default mixer is HDA ATI SB (Alsa mixer) and the volume controls on speakers and microphone all work as expected.

Run Sound Recorder from Applications, Sound&Video and I can hear my voice from the microphone in headset and speakers. Click on Record and the recorded .wav file contains only silence :(

With recorder I can open a sample .wav file and it plays that sound back no problem. However having selected recording again, the sample. wav file just plays back as before.

Having spent best part of today trying all the various options and upgrades I need some suggestion what to try next. It seems to me sound is going into the system, through the mixer controls and coming out the speakers but applications don't seem to know how to get at it.

Sound Recorder presents a "Record from input" menu and of course I tried every single option to no avail. The options are: Front Mic Boost, Front Mic, IEC958, Capture, Capture 1, Digital.. sigh this is just so frustrating :/

---

### Post by Don1500 on 2009-06-07
Go here, do what the man says. You will have music, and record it, too.


I have done this many times, and every time, it works. 

[URL="http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html"]
Click here for link[/URL]

---

### Post by Jazzy_Jeff on 2009-06-07
Go to this [link]("http://ubuntuforums.org/showthread.php?p=7171519#post7171519") and go to my post. That should help.

---

### Post by worksofcraft on 2009-06-07
Hum tried both of those... recording silence :(

I think I must have completely messed up some of the config file edits that were suggested so I'll see if I can install Ubuntu 9.04 over the top of my 8.04 without loosing all my data... then try again.

Just for the record I also plugged in a USB head set then selected all the USB audio devices but Recorder just complais my Multimedia setup is wrong.

---

### Post by worksofcraft on 2009-06-07
> **worksofcraft said:**
> Hum tried both of those... recording silence :(

I think I must have completely messed up some of the config file edits that were suggested so I'll see if I can install Ubuntu 9.04 over the top of my 8.04 without loosing all my data... then try again.

Just for the record I also plugged in a USB head set then selected all the USB audio devices but Recorder just complais my Multimedia setup is wrong.


OK :)

Jaunty Jackalope (9.04) works just fine staight out of the box :)
Either Hardy Heron (8.04) has serious audio problems, or I messed up somewhere at some stage with installations and configurations...

Thanks for the input it helped to know what I was meant to be  doing too :)

---

### Post by Jazzy_Jeff on 2009-06-07
> **worksofcraft said:**
> OK :)

Jaunty Jackalope (9.04) works just fine staight out of the box :)
Either Hardy Heron (8.04) has serious audio problems, or I messed up somewhere at some stage with installations and configurations...

Thanks for the input it helped to know what I was meant to be  doing too :)

Ok, I am sorry, I assumed you were using 9.04. I also had problems with 8.04 and 8.10. It was pulse audio that was messing me up. I uninstalled that and then I could get the recording to work.

I am glad you have everything working now.

---

### Post by worksofcraft on 2009-06-07
> **Jazzy_Jeff said:**
> Ok, I am sorry, I assumed you were using 9.04. I also had problems with 8.04 and 8.10. It was pulse audio that was messing me up. I uninstalled that and then I could get the recording to work.

I am glad you have everything working now.

Lol thanks... if only. Sound may be working but installing the new UBUNTU seems to have trashed all the applications I had set up and not only that but it's also lost my dual boot Windows option from /boot/grub/menu.lst

Thus I had many "fun" hours trying grub-install and grub-update and wondering why the partitions are not what they used to be. In fact replacing the hard drives with ones that used to boot fine it doesn't even recognize them now... so it's just the usual sort of computer frustrations.
):P

---

