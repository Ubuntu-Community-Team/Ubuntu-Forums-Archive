---
title: "How to use usb tv tuner/input device"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by glennric on 2009-12-08
I have a Hauppauge usb tv tuner, and I am trying to figure out what applications there are that use it.  I know of mythtv, but what a pain in the *** to use.  All I want to do for starters is convert VHS to electronic format to later burn onto DVD.  I have hooked up the VCR to the USB tuner, and I have managed to see video with vlc.  However, I can't get vlc to play the sound for anything.  The sound device is /dev/dsp2, but I can't seem to get vlc to use it.  Perhaps a pulseaudio issue?

Anyway, I have searched all around for howtos and there seem to be a plethora of them, many of them out dated, and none seem to be specific to Karmic.  Any help?

---

### Post by LowSky on 2009-12-08
what model number is the tuner?

---

### Post by glennric on 2009-12-08
It is a WinTV-HVR-950Q which is supposed to be well supported under linux according to the linuxtv website.

---

### Post by LowSky on 2009-12-08
according to [this]("http://ubuntuforums.org/showthread.php?t=1067510") Kaffiene should work just fine
```

sudo apt-get install kaffeine
```

this might be need as well, not so sure
[http://ubuntuforums.org/showpost.php?p=7458651&postcount=32](http://ubuntuforums.org/showpost.php?p=7458651&postcount=32)

---

### Post by glennric on 2009-12-08
I will try that, but isn't there something non kde that will work?  Shouldn't vlc work?  Or mplayer?  Or even nicer is there a gnome frontend to mythtv?

Why is it so hard to find the right software for this in linux?  Every other device I have ever had I have managed to find nice software for without this much effort.

---

### Post by glennric on 2009-12-08
Ok, so Kaffeine is not working as it should.  I am able to scan for channels and several are found, but when I try to play one I get an error popup that says "Cannot find demultiplexer plugin for the given media data".

Another problem is that this isn't what I am trying to do anyway.  I am trying to capture output from the vcr.  Like I said earlier, I can do this with vlc (using video4linux not dvb), but can't get sound.

---

### Post by glennric on 2009-12-08
I got kaffeine to play digital broadcast tv channels, but now how do I get analog from the vcr?

---

### Post by glennric on 2009-12-08
Ok, so I have managed to get video from the vcr using video4linux but I can not seem to get audio.  I am trying to use the composite video input.  Any ideas?

---

### Post by jmore9 on 2009-12-08
Go to linuxtv.org This is the site that is tv on linux.

---

### Post by madsmaddad on 2010-01-16
I was trying to do exactly the same. Eventually my son-in-law, who gave me the TV card, told me that I had to take the output audio from the jack on the TV card and feed it in to the line in on my sound card. The sound was not being passed through the card to the computer directly. 

These little things that people forget to tell us do waste a lot of time. 

PS How did you get vlc to work?

---

