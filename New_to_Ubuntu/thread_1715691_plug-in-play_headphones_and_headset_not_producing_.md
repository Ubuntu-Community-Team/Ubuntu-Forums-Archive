---
title: "plug-in-play headphones and headset not producing sound"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by Mark Belcher on 2011-03-27
Any kind of headphones or headset will not produce sound. Instead the computer built in speakers are producing the sound. When I plug in external speakers the external speakers play sound, but the built in speakers still play sound which is not suppose to happen. If anyone has any kind of suggestion to help me fix this problem it would be greatly appreciated. (I have searched for additional drivers while the peripherals are plugged in and still nothing)

---

### Post by spikoley on 2011-04-08
Click on the volume indicator and go to sound preference.  Take a look around the settings.

---

### Post by rosencrantz on 2011-04-08
Install and start pavucontrol (sudo apt-get install pavucontrol).
Look at the Port dropdown list on the output tab. Change the setting to headphones if it's set to Analog Speakers

---

### Post by audreylorraine on 2011-04-19
Hi.. I am encountering the same problem. I already tried changing the Connector to Analog Headphones but what happens is that there is no sound completely.. Any more suggestions?

---

### Post by Locke_99GS on 2011-04-19
If you're certain that the Pulse setting are correct (in Sound Preferences and Pavucontrol) and you still get no sound, open a terminal and run *alsamixer* and make sure your USB device is unmuted and volume is at appropriate levels.

---

