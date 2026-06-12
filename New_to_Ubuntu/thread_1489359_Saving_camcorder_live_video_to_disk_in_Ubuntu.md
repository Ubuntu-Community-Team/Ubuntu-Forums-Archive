---
title: "Saving camcorder live video to disk in Ubuntu?"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by brucewagner on 2010-05-21
I've always used Flash Media Encoder to receive video from a camcorder, encode it, and save it to disk. How can I do this in Ubuntu instead?

---

### Post by diablo75 on 2010-05-21
What kind of connection are you using to connect your camera?  Firewire?

---

### Post by brucewagner on 2010-05-21
Yes, FireWire from the camcorder to the PC. 
With Windows and using Adobe Flash Media Encoder, I just turn the camera On - without ever recording to DV tape - and the live video and audio are fed via the FireWire directly into Flash Media Encoder.  FME then encodes it into Flash, and saves it to disk... (much like a web cam sends video to Skype.)
Is there an app that I can use in Ubuntu to just capture the live video and audio and save it to disk?

---

### Post by bumanie on 2010-05-21
Kino (although it is getting a bit old, it still works well) is probably the best thing at present to get the video off the camera via firewire. It has basic video editing. I have used devede to convert the video to a.iso for burning, but there are other dedicated authoring programs to use that have better editing capability. I guess if you are using 10.04, why not try pitivi as it is included by default and once on the hard drive, it will do authoring and editing etc. as far as I know.

---

### Post by brucewagner on 2010-05-21
I can't get anything to even "see" the camcorder on firewire.

It appears that Kino, PiTiVi, etc are designed to capture PLAYBACK of recorded video from a camcorder...  But not to capture LIVE video coming in...

Either that, or...   Linux is not seeing the firewire video in at all.

On Windows, even Skype saw my Camcorder... as if it were another web cam.

On Ubuntu, nothing sees the camcorder.

I don't want to have to tape the video onto DV tapes first, then capture them into a video editor.  ( I mean, I could, but I'd rather go live to disk. )

---

### Post by bumanie on 2010-05-21
Oh...Yeah...i have always had to run kino via root for it to work. I forgot to mention that. To start kino go to terminal and type > sudo kino then it should 'see' the camera. Was never happy running it with root privileges, but it was the only way to get it to work. Editing is possible as a normal user, but to get video off a camera. running as root seems to be the only answer.

---

### Post by Paddy Landau on 2010-05-21
> **bumanie said:**
> sudo kino
Should be
```
gksudo kino
```Always use gksudo (or gksu) instead of sudo for graphical programs.

You can also start it with Alt-F2 then type the command.

---

### Post by brucewagner on 2010-05-21
Cool. Running it as root ( sudo kino ) does now allow it to see the camera's video.

Kino does not seem to allow live capture though...  Only the "capture" of a pre-recorded video... as the camera plays it back.

Is that correct?

I am looking for a way to capture it live, without the extra step of recording it on the camera first.

Also, which is the best, most stable, functional, easy to use, video editor?   Kino, PiTiVi, OpenShot, Lives, Kdenlive, OpenMovie, other...?

---

### Post by hfw on 2010-11-25
Did you ever figure this out.  I plugged my camera in via firewire, and launched kino and had live video in kino.  Looks great.  But then when I click capture, it only captures a single frame. I can't seem to get it to capture video.

Thanks,
Hal

---

### Post by no2498 on 2010-11-25
you may try typing webcam in the package manager and see what all uses fire wire/1394

? does the cam show up if you type 
lsusb in a terminal
if yes try xawtv, cheese, or wxcam

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

hope 1 of them help you

---

### Post by marcia on 2010-12-05
Hello. 

Did you get this resolved? I have captured live via firewire on my sony minidv camcorder many times. I have used dvgrab, kino, and gstreamer-properties. It can be done beautifully! 

This link may help for starters:[http://ubuntuforums.org/showthread.php?t=645826&highlight=dvgrab](http://ubuntuforums.org/showthread.php?t=645826&highlight=dvgrab)

You will need all of the firewire apps installed.

I will be doing this again in kxstudio lucid hopefully this week. I will let you know how I am doing it if you need the assistance.

Good luck,

Marcia

---

