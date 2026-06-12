---
title: "audio and video"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by art_monu on 2011-05-06
I have recently removed my Windows XP completely and installed the latest Ubuntu 11.04 version. I have installed the gstreamer codecs that came up when I tried to play my mp3 files. But, the sound is not clear. I can hear "brrrr..." when playing music. My video playback is not smooth. I also installed the Ubuntu restricted extras but they also could not improve the performance of audio as well as video. I also installed vlc media player but with no difference. Also, there is no Rythmbox in 11.04 as was the case with 10.04. Please suggest me the best possible solution. Are there other media players that can solve the issue or better codecs? Please reply...!!!

Thanks in Advance.:KS

---

### Post by ExileAmongYou on 2011-05-06
Hmmm, the sound issue might be an analog vs. digital output problem. Click on the sound menu, go to Sound Preferences, Hardware, and test different profiles for your sound card to see if any of them work better.

Do you have the right drivers installed for your video card? Open up the Additional Drivers dialog and install them if not, that might fix your video.

Rhythmbox was replaced with Banshee as the default media player, but if you prefer Rhythmbox you can install it again from the Software Center.

---

### Post by art_monu on 2011-05-06
Ya, I have two sound cards one internal and one external. The internal sound card does not work so I have selected the external. I don't have graphics cards but I had updated my video drivers in XP. Please tell me how to install those latest drivers in Ubuntu.

---

### Post by art_monu on 2011-05-07
Someone please reply...

---

### Post by rx007 on 2011-05-07
> **art_monu said:**
> Ya, I have two sound cards one internal and one external. The internal sound card does not work so I have selected the external. I don't have graphics cards but I had updated my video drivers in XP. Please tell me how to install those latest drivers in Ubuntu.

there might be a conflict with your internal sound card. please disable it first in the bios. 
then in ubuntu you may want to check additional drivers for it. go to administration >> additional drivers.

---

### Post by art_monu on 2011-05-08
I have disabled the internal sound card and when I click on additional drivers, it says, no proprietary drivers are in use.

---

### Post by ExileAmongYou on 2011-05-08
OK, if there's no proprietary drivers in use, are there any available to install? You should install them if they're there.

Also, can you post a screenshot of what the "Hardware" tab looks like when you open up Sound Preferences?

---

### Post by 3rdalbum on 2011-05-08
If things sound fuzzy, then you might need to run 'alsamixer' in the terminal and turn down the "pcm" channel just a little.

---

### Post by art_monu on 2011-05-08
there are no available drivers to install.

---

### Post by art_monu on 2011-05-08
and what about the video quality? it does not run smooth. Please tell me how can I solve that???

---

