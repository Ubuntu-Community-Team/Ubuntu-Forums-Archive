---
title: "Mic isn't working"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by Buuntu on 2009-08-23
I'm trying to get my mic to work so I can use skype.  I've looked for solutions in google, here, and have asked in IRC.

I have tried the following, none of which have worked for me:
-Checking everything in volume control under Preferences.
-Making sure nothing is muted and/or too low.
-Setting Input to Front Mic instead of Mic in Volume Control.
-Setting Input to Pulse in Skype.

Recording in Application > Sound & Video > Sound Recorder only return static, though it does seem to register something.
Also, I have no problem at all with sound, just the microphone.

I am using a headset attached directly to the motherboard ports (the green and purple ones).

Any ideas??

---

### Post by arochester on 2009-08-23
The sound settings for Skype are in Skype and not in the Computer sound settings.

Open Skype. Click the "S" button (bottom left)>Options>Sound devices.

To some extent you need to play around with Sound In and Sound Out. I use a headset and it did not work until I changed to the option with "hw" in it. Then make a Test Sound and a Test Call...

---

### Post by Buuntu on 2009-08-23
Well I think it's not skype, because or else stuff like sound recording would work.  
I think I should start with getting the sound recording to work somehow.

---

### Post by Buuntu on 2009-08-23
I got it fixed :D.

Sound recorder is a bad recorder and was basically playing back static while I talked.  Audacity is much better, and let me know when stuff was working or not.  

The setting that basically worked for me were:
Front mic in input tab under Volume Control.
Sound Out and Ringing set to Pulse in Skype.
Sound In set to HDA Nvidia (hw: Nvidia, 0) which I guess is my front panel port.
Unchecked "Allow Skype to automatically adjuct my mixer levels"

For poeople having similar problems, I recommend using audacity to test your sound recording, and the test call service in Skype to test Skype input.

---

