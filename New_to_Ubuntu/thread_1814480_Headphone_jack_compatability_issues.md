---
title: "Headphone jack compatability issues?"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by Sunfire0258 on 2011-07-29
I've tried Banshee and Rhythmbox, and neither of them will play my library on my headphones. I've checked to make sure it was plugged in correctly and in the right jack, I've went through the Ubuntu System Testing, and I've checked with YouTube videos as well and it still plays it through my laptop's speakers instead of my headphones when my headphones are plugged in. I know my headphones work because I've been using them with my iPod and smartphone.

---

### Post by scorchgeek on 2011-07-30
Have you tried looking in the Sound Preferences? In GNOME it's at System->Preferences->Sound. If you're using Unity I'm not entirely sure where it is, but the same thing should apply.

The problem is probably that Ubuntu isn't recognizing that you plugged something in and changing the device--if you select the Output tab of the Sound Preferences box you should be able to change where you want the sound to be played. (If that doesn't work, your headphone jack is probably broken.)

---

### Post by Sunfire0258 on 2011-07-30
The only option it gives me is Internal Auto Analog Stereo. I tried plugging in my headphones and going back to Sound Preferences and it was still the same. My laptop is only a year old, and my headphones worked fine when I has Windows 7 installed. My laptop has been having other problems with Ubuntu too so it could just be my laptop brand.

---

### Post by Redblade20XX on 2011-07-30
Try and install pulse audio volume control from the software center. After installing, run the program and look under the output devices there should be an option for what device to use like analogue speakers, headphones, etc. Test out which ever works.

---

