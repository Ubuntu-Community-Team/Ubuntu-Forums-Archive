---
title: "The trials and tribulations of the 790GX."
date: 2009-01-30
forum: New to Ubuntu
---

### Post by thechansen on 2009-01-30
This motherboard (Biostar TForce 790GX set to run with 128 sideport and 512 shared) has been a giant headache for me with 8.10 64 bit.  It seems as soon as I *think* I solved all of my video/audio problems, they just rear their ugly heads in different ways.  HDMI has been a giant pain in the rear.

I'm thinking of just giving up all hope with pulse audio.  I went through the pulse audio guide and have my audio working system wide, which is great.  The Last.fm application works just fine and I've tested it to work for hours, as does DVD play back and h.264 hi def file in VLC.  Flash/Boxee on the other hand....  Now in Windows 7, I can full screen any content on youtube or hulu and it runs fine.  No video stutter, and the audio sounds great coming over HDMI.  In Ubuntu however, if I have a video playing at full screen (or even half of full)  I get choppy playback.  

Ok, fine I say,  I will watch it at the default size.  So I was just watching the last episode of Fringe and after about 10 minutes, the audio goes dead.  Video is still running fine, just no audio.  Ok, I killall pulseaudio and restart it.  I try watching it again.  I make it about 5 minutes into the episode before it cuts out again.  I restart pulse audio, and this time I load up Boxee (32bit app forced onto a 64 bit 8.10 install) and I have a little more luck watching up to 30 minutes in before the audio craps out on me.     At this point i purge pulse, reinstall go through the guide again, purge ati drivers, reinstall ati drivers, muck around in sound/video settings, purge everything again, then install flash 10 alpha/beta, ati 9.1, and pulse audio.  Still can't figure it out.  When firefox and flash decide to kill the audio, it's not just in FF and flash, it's system wide, which is leading me to believe it's pulse audio. 

Pros and cons of ditching pulse audio?  Anyone have any suggestion on how to get around these little issues, or should I just hold out for better support in jaunty?

---

### Post by nortexoid on 2009-04-06
Sorry, I have nothing helpful to say, except thanks for the feedback. I am considering a 790GX but only if everything works properly under Ubuntu. If you can, a follow up with your experiences in Jaunty once it's released would be most welcome. Most welcome!

---

### Post by markbuntu on 2009-04-06
I have a biostar TA790GX A2+ and I don't have any of those problems. The problem is not with pulse or alsa but with flash so you would be better off without a beta version.

ALso, change the System/Preferences/Multimedia Systems Selector/video to X Window System (No Xv) to get rid of choppy full screen playback or turn off the dektop effects but the 9.3 driver should take care of all that.

---

### Post by slakur on 2009-09-06
I have the TA790GX XE and have had nothing but troubles getting my jaunty install up and running properly.  I can say the same with regard to just when I think I have everything working something goes wrong.  I can't get the proprietary video drivers to work at all, the open source driver seems to work most of the time but I just had a lock-up a few minutes ago (browsing the web).  All-in-all a major disappointment.  I had an ATI video board years ago under linux (running fedora core then) and had nothing but problems which forced me to install Windows XP.  I was hoping things had changed.

---

### Post by slakur on 2010-11-18
This is an old thread but I figured I might update it despite its age. I am still running Ubuntu on the same board and am happy to report things work much better now. I am on Maverick and my experience is fairly stable. From time to time though my system will just "freeze". I don't know how to diagnose the problem though, the only symptom that I am aware of is the freezing. When the system does freeze, I reboot it by holding the power button for 5 seconds. I have the latest bios for the board.

---

