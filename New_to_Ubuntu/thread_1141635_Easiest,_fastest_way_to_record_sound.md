---
title: "Easiest, fastest way to record sound"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Nutopia on 2009-04-28
Hello,

I had a bunch of problems with Audacity that I don't have time to fix right now. I need to be able to record some sort of sound from my mic hopefully right away. When I plug in the mic, I can hear it through the computer speakers, but every time I run any sound recorder I get some kind of error message. I've tried all sorts of different things and I think that may be what eventually screwed things up... 

Can anyone help me get some sort of rudimentary audio recorder working? Like I said, I've tried so many suggestions out there that I just feel like something is conflicting with something else - just not sure what.

Thanks - and I'm on 8.04

---

### Post by davidstri on 2009-04-28
Try ```
sudo apt-get install sox
```, and then ```
rec whatever.ogg
```

---

### Post by bgs100 on 2009-04-28
> **Nutopia said:**
> Hello,

I had a bunch of problems with Audacity that I don't have time to fix right now. I need to be able to record some sort of sound from my mic hopefully right away. When I plug in the mic, I can hear it through the computer speakers, but every time I run any sound recorder I get some kind of error message. I've tried all sorts of different things and I think that may be what eventually screwed things up... 

Can anyone help me get some sort of rudimentary audio recorder working? Like I said, I've tried so many suggestions out there that I just feel like something is conflicting with something else - just not sure what.

Thanks - and I'm on 8.04
Ubuntu comes with a small sound recorder
Applications -> Sound & Video -> Sound Recorder

---

### Post by Jazzy_Jeff on 2009-04-28
Here are some things to check. First double click on your sound icon in the upper right corner. On the Playback Tab make sure you can see the Microphone and the Mic Boost or the Front Mic and Front Mic boost depending on which one you are using. 

It is good that you can here sounds through your speaker with your mic. What you need to do is check the little speaker at the bottom of the mic and make sure it is muted. (It is only muted from being open, not from programs.)

Next click on the prefrences tab at the bottom. On the pop up Make sure the Microphone and Mic Boost is checked. (or Front Mic and boost, whichever one you are using.) Also check Input Source and Capture. Close the box when you are done.

You should have a tab now that says recording. Make sure the capture is up all the way. Then click on the Options tab and for Input source make sure Mic or Front mic is chosen. There is a bug some times where you have to change the option to something else and then back to mic. So do that. Make sure the mic volume is all the way up and the mic boost about half way and then adjust as needed.

Now go into Applications and sound and bring up your sound recorder. Make sure Record from input show Capture. Everything should now be working. Post back if it is not.

---

### Post by Nutopia on 2009-04-30
Jazzy Jeff - I did all that you said. When I went to Sound Recorder I hit 'Record.' I tested a little... then on playback I get the following error message:

"Internal GStreamer error: state change failed.  Please file a bug at http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer."



davidstri - I did what you said. After I execute the 'rec' command, I get the following error message:

"rec soxio: Failed reading `default': unknown file type `alsa'"


Thanks for the help thus far.... any further ideas?

---

