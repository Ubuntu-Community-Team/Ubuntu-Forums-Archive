---
title: "Sound Issues"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by jennkhutch on 2010-12-13
Apologies if this doesn't belong here but since I am new to ubuntu and linux, I figured this would be the place to get answers I can understand.

I am on 10.04 and I can't seem to get sound to work. I also can't get the sound preferences to recognize and let me select my Logitech Speakerdesk N700 as the output, that's if it even gets past the "waiting for sound system to respond" error.

I have googled my heart out for days on this issue c&p'ing all kinds of commands that have been suggested and I don't even know what I was even doing half the time and none of them seemed to help.

Suggestions?  (please speak to me as if I know nothing about ubuntu whatsoever)

---

### Post by karthick87 on 2010-12-13
Welcome to ubuntuforums :) 

Check this out,
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by jennkhutch on 2010-12-13
> **karthick87 said:**
> Welcome to ubuntuforums :) 

Check this out,
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)


Thank you for the welcome.  Unfortunately, I don't really understand those suggestions either. All I keep getting at this point is "waiting for sound system to respond"

---

### Post by karthick87 on 2010-12-13
Goto **System>>Preferences >>Startup Applications**
 

 1. Click on **Add **and give the following details.

 Name: Pulseaudio daemon
Command:/usr/bin/pulseaudio
Comment: 

 2. Now reboot your system.

---

### Post by jennkhutch on 2010-12-13
If this helps, here is what I am looking at.  I can get Alsamixer open and it shows both the internal sound card and the logitech speakers. When attempting to open up the sound settings, that warning appears. While trying to debug the issue, I am told to correct the output but it takes a while to get the sound settings to open and when it does, it doesn't show it as an option to choose from as the output.

[IMG]http://farm6.static.flickr.com/5004/5257982721_a21f3b46a0_b.jpg[/IMG]

---

### Post by jennkhutch on 2010-12-13
> **karthick87 said:**
> Goto **System>>Preferences >>Startup Applications**
 

 1. Click on **Add **and give the following details.

 Name: Pulseaudio daemon
Command:/usr/bin/pulseaudio
Comment: 

 2. Now reboot your system.

That got the sound to play from the laptop speakers, awesome!  

Hopefully when the sound system finally responds I can see if it will let me choose to have the sound go through the logitech ones.

Is there a way around the "waiting for sound system to respond" issue?


ETA: Settings opened up but it still isn't showing the Logitech speakers as an output option. 

[IMG]http://farm6.static.flickr.com/5122/5258029277_9b8aca9c8f_b.jpg[/IMG]

---

