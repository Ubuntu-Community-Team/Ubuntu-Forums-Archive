---
title: "virtual soundboard app?"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-08-26
Hi, Y'all! I was wondering is there is a sort of virtual soundboard program that will take audio in from a USB microphone DIRECTLY to the speakers, amplifying my voice? Any recommendations would be greatly appreciated!

DG

---

### Post by sandyd on 2011-08-26
> **doppel.ganger said:**
> Hi, Y'all! I was wondering is there is a sort of virtual soundboard program that will take audio in from a USB microphone DIRECTLY to the speakers, amplifying my voice? Any recommendations would be greatly appreciated!

DG
Use Jack. Add in jack RACK or an equalizer. Send the microphone output to jack Rack/equalizer. Then send the application output back to the speakers.

Oh, and you don't need to garbage pulseaudio for this.

Just install jack, and use

```

load-module module-jack-sink channels=2 channel_map=front-left,front-right
#load-module module-jack-source channels=2 channel_map=front-left,front-right
load-module module-native-protocol-unix
## The following is not mandatory
load-module module-volume-restore
load-module module-default-device-restore
load-module module-rescue-streams
.nofail
.ifexists /usr/lib/pulse-0.9/modules/module-x11-publish.so
load-module module-x11-publish
.endif
## The following can conflict with this config.
#.ifexists /usr/lib/pulse-0.9/modules/module-gconf.so
#load-module module-gconf
#.endif
set-default-sink jack_out
#set-default-source jack_in

```
as ~/.pulse/default.pa .

Be sure to back it up first.

Oh, and QjackCTL is a nice gui for JACK.

---

### Post by doppel.ganger on 2011-08-26
What? Sorry, I'm not THAT tech-literate ;)

---

### Post by sandyd on 2011-08-26
> **doppel.ganger said:**
> What? Sorry, I'm not THAT tech-literate ;)
Jack is a professional audio system. Designed for low latency audio production. It allows for routing audio streams from one output/input to another.

The instructions in this thread -> [http://ubuntuforums.org/showthread.php?t=806730](http://ubuntuforums.org/showthread.php?t=806730)

are enough to help you finish installing JACK & qjackctl.

Afterwords, you won't be able to start JACK because pulseaudio is in the way.

Run this:

```

rm -rf ~/.pulse
nano ~/.pulse/default.pa

```Copy and paste the stuff I had in my previous post, and press ctrl+x to save

You might also find it handy to set QJackCTL (click the setup button, misc tab)
to 
-"Start Jack Audio on application startup"
-"start minimized to system tray"

For more info, see
[https://help.ubuntu.com/community/What%20is%20JACK]("https://help.ubuntu.com/community/What%20is%20JACK")
and [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

If you use Ubuntu Studio, you might find that everything is already setup. You would only need to install qjackctl if it isn't installed.

---

### Post by doppel.ganger on 2011-08-27
OK, got it installed. Now how do I set it up to take input from a USB Mic and out put it through my external speakers?

---

### Post by doppel.ganger on 2011-08-27
I don't see any settings that would allow me to do this.

---

### Post by sandyd on 2011-08-29
In the readable clients box (click connect in qjackctl), select system -> capture 1.

In the writable clients box , select both the outputs under system, and click connect.

p.s. if your not getting output, check if you selected the right input in the qjackctl config.

---

### Post by doppel.ganger on 2011-09-03
Yay! it works with my internal mic but i can't get it to work with my usb mic!!

---

### Post by doppel.ganger on 2011-09-03
I've posted a video on YouTube that might make it a little easier to help me. [http://www.youtube.com/watch?v=AkqquJLFLso]("http://www.youtube.com/watch?v=AkqquJLFLso")

---

