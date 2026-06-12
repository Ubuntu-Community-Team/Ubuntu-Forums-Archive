---
title: "DeVeDe partially Crippled"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by gyozu on 2009-12-12
I have looked back through the DeVeDe related files, but so far, nothing looks similar. 

Sometime in the last few weeks, since I last used the program, DeVeDe has forgotten how to hold its settings. It also does not rememer the file to go looking in for .avi downloads.

When I click to add a new .avi for conversion to ISO it no longer fills in the current .avi info or the default video and audio rates. If I click from PAL to NTSC and back, the original rates will appear, but the default rates are 500 for frame rate and 0 for audio.

When I put in the subtitle file it does pickup the ISO-8859-1 selector, but the font size is zero.

I am not sure if any of the other defaults are odd, but If they are , they are not redily evident.

I can put in the wanted values for audio, frame and font. I can then make an ISO and "write to disk". This gives me a playable DVD with subtitles.

I am doing this on a 64 bit system. I am using DeveDe 3.15.2   
It is dual boot. I have all repositories that I know about enabled. DeVeDe was working. ???Some bug from a recent update or some setting changed?? About the only other peculiarity is that the speaker icon no longer shows the red "Muted" symbol when engaged.

so far, all I have done is use synaptic to completely remove and reinstall DeVeDe. No change in settings being remembered.

Any thoughts on where to start looking?

---

### Post by RedSingularity on 2009-12-13
Well first remove the whole thing......sudo apt-get remove devede

then delete all configuration files.  (I only see one).   Look in the /home/you directory and press ctl + h to show hidden folders.

Scroll to the bottom and you should see something called .devede

Delete that and then reinstall devede.

---

