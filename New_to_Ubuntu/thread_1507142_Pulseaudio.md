---
title: "Pulseaudio"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Fifthmarch on 2010-06-11
I'm using Karmic Koala now - thinking of uploading to Lucid Lynx. I had to remove pulseaudio and install a mixer for ALSA before my mic worked with Karmic. Will I have to do the same with Lucid, or is it less dependent on pulseaudio?

Also, are there problems with displaying 3D - Blender, for instance in Lucid? It was there in Jaunty, but Karmic works fine. 

Thanks

---

### Post by tarps87 on 2010-06-11
It would help if you could post the sepcs of your machine, specifically the sound card

---

### Post by cb951303 on 2010-06-11
it's not less dependent on pulseaudio. but pulseaudio maybe less buggy.

---

### Post by eriktheblu on 2010-06-11
I'm finding Pulseaudio in Lucid to work a lot better than it did in Karmic.

---

### Post by Fifthmarch on 2010-06-11
> **tarps87 said:**
> It would help if you could post the sepcs of your machine, specifically the sound card
This is the sound card: 

Intel 82801l (ICH9 Family)

---

### Post by sandyd on 2010-06-11
> **Fifthmarch said:**
> This is the sound card: 

Intel 82801l (ICH9 Family)
oh that card!

I have it...

and it isn't a bug in karmic.

If you install the pavucontrol package and start up the app, you will find that pulseaudio has a seperate place to enable and disable the mic O_o.

not sure why they did that, but it made me waste 30 minutes before I decided to install everything with the name "pulseaudio" in it...

and yea... I still had to do that in Lucid.

p.s. If you have any media keys on your keyboard, DO NOT, I repeat DO NOT press the mute key if you have a HDMI port. It will mute the normal speakers and use HDMI out instead.

To get around this, click on "configuration", and make sure EVERYTHING other than "Internal Audio" is set to Off

Under the input devices, you can unmute the mic (which is muted by default, and unmuting it in gnome/kde volume manager doesn't have any effect....)

---

### Post by Fifthmarch on 2010-06-15
If I open up pavucontrol, I get a pop up saying "Connection Refused." Can you tell me what that means?

---

### Post by Bucky Ball on 2010-06-15
You might find this of interest:

[http://ubuntuforums.org/showthread.php?t=1478754](http://ubuntuforums.org/showthread.php?t=1478754)

Follow the steps in post #8. 

Once you get Pulse Audio Device Chooser->Volume Control working, start an audio stream (play some music). The stream will appear in the 'Playback Stream' window. Right click it, 'Move Stream ...' and move it to the device you want. You can move the playback stream for individual apps to whatever device you choose: Skype to the USB headphones, Firefox to the computer speakers ... whatever.

---

### Post by Fifthmarch on 2010-08-10
I think I will have to do the same steps in Lucid that I did in Karmic. Thanks for the tips, everyone!

---

