---
title: "Skype Audio"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by AstroVision on 2010-06-12
Good morning,

I realize that there is a ton of threads about the microphone issue in Skype 2.1 Beta... but I'm relativity new to Ubuntu and after many days and weeks of getting nowhere, I'm hoping that someone might be able to help me if they knew my specific details.  I'm using an ACER ASPIRE 3810T. The specs are in the link below:

[http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire3810T/Aspire3810Tsp2.shtml]("http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire3810T/Aspire3810Tsp2.shtml")

I got the microphone working with Ubuntu itself (tested it with Sound Recorder).  The noise floor is a little high, but my voice still gets recorded (which is good).  When I go into Skype, it doesn't pick up the microphone.  If I go to the options within Skype, the only sound device available (microphone) is PulseAudio sever (local).  

I just can't get my head around what to do.  There are recommendation within the forums to install other audio software on the system, like ALSA.  But I'm afraid if I do that, I will loose all microphone capability completely.  

If someone could suggest a solution, that would be awesome! 

Cheers,
-AV

---

### Post by stoogiebuncho on 2010-06-12
This is the solution that worked for me and a few of my friends.

Go to the Skype options, and to the Sound Devices section.  There's a box there that says "Allow Skype to automatically adjust my mixer levels"  Make sure that box is NOT checked.

You may have to restart Skype after making this change.

---

### Post by AstroVision on 2010-06-16
Nope, didn't fix the problem.  Any other ideas you can suggest?

Cheers,
-AV

---

### Post by lidex on 2010-06-16
Try this. Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
Reboot.

---

### Post by AstroVision on 2010-06-19
Nope, didn't help. :( Still no audio recording in Skype.
Any other idea guys?

---

### Post by lidex on 2010-06-19
Have a look here:
[http://www.linlap.com/wiki/acer+aspire+timeline+3810t]("http://www.linlap.com/wiki/acer+aspire+timeline+3810t")
Scroll down to the comments section.

---

### Post by AstroVision on 2010-06-23
I spent a while looking through the link I found within "http://www.linlap.com/wiki/acer+aspire+timeline+3810t"
I tried some of the potential solutions without any luck.

---

### Post by AstroVision on 2010-07-03
Does anybody know if Skype is working on this audio problem?  Again, any other suggestions on what else I can do would be much appropriated.

---

### Post by oldsoundguy on 2010-07-03
I can't get either audio OR video to work with my Logitech 9000!  It works in Cheese, and the microphone tests fine outside of Skype.
Skype needs to get off the pot!  WAY  too many issues have shown up on this forum for it to be an isolated problem.  But, of course, they don't REALLY care about only 2% of the computer users.  Not their problem!

---

### Post by lidex on 2010-07-04
This may help?
[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/]("http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/")

---

