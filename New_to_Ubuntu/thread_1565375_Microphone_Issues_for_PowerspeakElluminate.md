---
title: "Microphone Issues for Powerspeak/Elluminate"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by butterfly60680 on 2010-08-31
Hi, I am beyond a beginner, so please be gentle! My daughter has to use a microphone for her Spanish class and it won't recognize a recording.  I have recorded on audacity, so I know it is the microphones or sound card.  I have tried both the front and back plugs into 2 different desktops and a laptop.  We are using Kubuntu 10.04 and have spent 1.5 hours with the elluminate people trying everything, so it isn't just a muted mic.  Thank you so much to anyone who helps!

---

### Post by bergfly on 2010-09-03
Just to confirm you have done this.

Left click on the speaker in the system tray
Select Mixer at the bottom. It will bring up a window. Along the top of the window, select "settings"
Then under settings, choose "configure channels"

This brings up a list of channel. Depending on your sound devices depends on your list of channel, so can't help too much as to what you will see there. However, make sure that each and every possible channel that could do recording is dragged to the right. 

Now click ok on that and them make sure than any new sliders to do with recording are not muted and boosted up. There may well be mic boosters or the like that could help in there.

---

### Post by butterfly60680 on 2010-09-03
Yes, that has all been checked and moved and arranged.  New information from the Elluminate says that Kubuntu is not compatible with their program.  However Ubuntu 8.10 or less and Open suse 11 or higher are the only ones. However the guy I was talking to used Ubuntu 10.04 or 10.05 (whatever it is) and he had his working.

---

### Post by DarkSniper on 2010-09-15
I'm running Xubuntu 10.04, and Elluminate, with a bit of configuring, and some terminal commands works fine for me. The same procedure should work for other desktop environments as well. Powerspeak sadly I can't say the same about, still looking for a fix for that. 

Since you seem to have an analog mic, as opposed to a usb mic, I'm not sure how to get the microphone working, although, the fix that worked for my speakers, might allow you to use your analog mic as well. 

Here's what I've been doing to get elluminate working: 
Ensure that you have ALSA drivers installed by opening a terminal window and typing "sudo apt-get install libesd0-alsa0 alsa-base alsa-oss" without the quotes. Then once those are installed, create a shortcut/launcher somewhere with the command "aoss javaws /home/dark/Downloads/meeting.jnlp" [again without the quotes] Obviously substituting "dark" for your username, and "downloads" with where you plan to save your elluminate meeting file. Edit your browser's settings to not open jnlps by default, in edit>preferances>applications [This is using Firefox as an example] and setting the jnlp filetype to always ask. When the elluminate page requests to save the jnlp, save it in the same spot you told that launcher to open, overwriting the previous file you saved there [if any] 

Then once you have saved your elluminate file, run the launcher, and it should start elluminate, and it should have sound working properly now.

Hope this is helpful to you.

---

