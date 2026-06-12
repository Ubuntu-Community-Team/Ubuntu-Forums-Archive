---
title: "What is the best way to record audio into my desktop?"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by keithgroben on 2011-03-06
I have since tried to use Audacity, but couldn't get it to work. I am new to this, so I am hoping someone may know a fairly simple way to set up a recording program, and configure it to record line-in.

---

### Post by maqtanim on 2011-03-06
Applications > Sound & Video > Sound Recorder
Did you use that?

[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

---

### Post by keithgroben on 2011-03-06
Yes, I tried using that, but cannot get audio to record into it, or any other application for that matter.

---

### Post by MrRichard on 2011-05-06
I'm also having the same problem. Does anybody know of a solution?

---

### Post by Thecoolguru on 2011-05-06
Do you have a microphone either plugged in or built in to your computer? I know it sounds like a silly question, but it's easy to forget things like that. Another thing that could be the problem is not having the program using the correct input. I'm not sure what it would be if it were actually part of Ubuntu.

If you're using Audacity, press ctrl+P (or go to Edit-> Preferences) and open up the Audio I/O tab. Go to the drop-down menu next to "Device", and try out different options. You could also try looking at the audio settings for Ubuntu. I'm not totally sure where that is, as my computer running Ubuntu is in a state of disrepair right now.:frown: I hope that helped some!

---

### Post by BertN45 on 2011-05-06
Load "pulse audio volume control" from the Ubuntu Software Center.
Check the settings on the configuration tab, the main type of choice is there analog or digital. Check the settings of the device tabs (input and output). Check the volume settings and check that the microphone is selected and not e.g. line in.

Start the recording program and go to the recording tab of pulse audio volume control and select the right input device for the recording.

I hope and expect it helps.

---

