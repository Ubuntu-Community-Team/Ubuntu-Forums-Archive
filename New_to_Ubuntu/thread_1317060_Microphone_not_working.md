---
title: "Microphone not working"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by ubunt22rock on 2009-11-06
Hi

I have been using Karmic. And I installed skype. I found out that my mic is not working. I have a hp dv4 laptop. My webcam which never used to work with prev distros is working fine. in skype the sudio option list has only one entry : pulseaudio sound mixer.

I also tried the sound recoder app. Not working either. got a solution?

---

### Post by tacantara on 2009-11-06
Open up a terminal session, and enter the following:

```
alsamixer
```

This will bring up the Alsamixer slide controls.  Use the left & right arrows to navigate through the various controls.  Make sure that your microphone is enabled, and that the level is up.  You may want to play with the settings on the mic to ensure that you get sound picked up, without feedback, etc.  To increase/decrease any of the settings, use the up and down arrows.  When you're done, press the ESC key to exit Alsamixer.

---

### Post by jbrown96 on 2009-11-06
> **tacantara said:**
> Open up a terminal session, and enter the following:

```
alsamixer
```

This will bring up the Alsamixer slide controls.  Use the left & right arrows to navigate through the various controls.  Make sure that your microphone is enabled, and that the level is up.  You may want to play with the settings on the mic to ensure that you get sound picked up, without feedback, etc.  To increase/decrease any of the settings, use the up and down arrows.  When you're done, press the ESC key to exit Alsamixer.

You will need to switch to Alsa first. In System-->Preferences-->Sound switch all the options to alsa. Then reboot. Then do what tacantara said.

---

### Post by ubunt22rock on 2009-11-06
system-preferences-sound

There is no option to switch. I am in Karmic Koala. I have seen it in previous distros. But its not here in Karmic

---

### Post by jbrown96 on 2009-11-06
Uh-oh. I use Kubuntu, so I don't have the same menus. I don't know where to tell you to go, but there should be something about sound. 

Finally got burned giving support for Ubuntu. One of the perks for giving support on software that you don't use.

---

### Post by tacantara on 2009-11-06
> **ubunt22rock said:**
> system-preferences-sound

There is no option to switch. I am in Karmic Koala. I have seen it in previous distros. But its not here in Karmic

I'm also in Karmic, and I see what you're referring to.  When I ran Alsamixer in the terminal, I did not adjust any other settings previously.  I think Alsa is the default sound in this distro (though I could be wrong).  Try running the terminal command and see if you get the mixer.

---

### Post by ubunt22rock on 2009-11-06
I do get it. In fact I installed the GNOME alsa mixer and fiddled with it. but that doesnt change anything

---

### Post by jbrown96 on 2009-11-06
> **tacantara said:**
> I'm also in Karmic, and I see what you're referring to.  When I ran Alsamixer in the terminal, I did not adjust any other settings previously.  I think Alsa is the default sound in this distro (though I could be wrong).  Try running the terminal command and see if you get the mixer.

If there is just one pulseaudio channel, then alsa is not running. If alsa is working, there should be quite a few channels.

---

### Post by tahitiwibble on 2009-11-06
> **jbrown96 said:**
> If there is just one pulseaudio channel, then alsa is not running. If alsa is working, there should be quite a few channels.

This describes exactly my situation (I'm also having mike problems). How do I get alsa working?

---

### Post by Arla on 2009-11-06
Suggested in the thread to tahitiwibble, but I'll add it here.

Someone pointed me at linux-backports-modules-alsa-2.6.31-14-generic for my Lenovo laptop (mic totally didn't work), after installing this (I had to do a clean install of Karmic too, but I'd been messing with it for a while and probably had screwed up other things) it worked perfectly.

---

### Post by ubunt22rock on 2009-11-06
@Arla: tried it. doesnt work

---

### Post by Hilgo on 2009-11-06
I remember having the same problem when i first installed 9.04. I used the information on [this]("http://linuxtipstricks.wordpress.com/2009/04/04/how-to-permanently-fix-skype-audio-problem-in-ubuntu/") site. All though you have a different version it might just work for you as well.

---

### Post by ubunt22rock on 2009-11-06
dude. I tried it. and I couldn't get any audio controls. The sys-preferences-sound opens a blank window and there is no sound controls in the task bar. So I reinstalled pulseaudio. Anyone has a different solution?

---

### Post by ubunt22rock on 2009-11-08
bump

---

### Post by ubunt22rock on 2009-11-13
Bumpppppppppp

---

### Post by ojay on 2010-06-30
> **ubunt22rock said:**
> @Arla: tried it. doesnt work

Sure you must have settled this. Just for other 10.04 user, i also had same pro with my mic. then i went to system>preferences>sound>input. and then i realised that it was on mute!
That solves the pro.

---

