---
title: "Sound STILL not working"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by courtneynelson on 2010-04-25
I'm new but I have gone through the forums and tried the fixes posted. I did a clean install of Karmic 9.10 and the sound isn't working. I have made sure the sound was up on Windows 7 and the sound is not muted on Ubu. I have downloaded the driver from realtech but it hasn't helped either. I am using an HP TouchSmart tx2 tablet. My next fix will be NTrig and Pen. Can anyone please give me some assistance for sound? Thank you

---

### Post by nothingspecial on 2010-04-25
Posting your soundcard will help

aplay -l

---

### Post by flying_174 on 2010-04-25
I'm a new user as well. When i first installed Ubuntu i had no sound at all. I spent a lot of time on the forums reading and running suggested commands after nothing worked I started looking at thing my self this is what i found that worked for me. I hope it helps.

I found that Ubuntu has reading more than one sound device on my system. 
Go to system/preferences/sound/hardware.   check that there is only one device. If there is more than one device then run something in the background that has sound such as a youtube video and select between the devices till you have sound. I hope this helps. This is what my issue was and I didn't find it posted any where so I thought I would mention it.

---

### Post by lidex on 2010-04-25
> **courtneynelson said:**
> I'm new but I have gone through the forums and tried the fixes posted. I did a clean install of Karmic 9.10 and the sound isn't working. I have made sure the sound was up on Windows 7 and the sound is not muted on Ubu. I have downloaded the driver from realtech but it hasn't helped either. I am using an HP TouchSmart tx2 tablet. My next fix will be NTrig and Pen. Can anyone please give me some assistance for sound? Thank you

Did you go through this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Still no sound? As well as the info *nothingspecial* requests, Can you post the output of these terminal commands for me please:
```
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by courtneynelson on 2010-04-25
Thank you for your replies everyone. I don't know what I did but I was able to get it to work. I have restarted a couple times and it works so far so good. I appreciate everyone's replies

---

### Post by lidex on 2010-04-25
Oh well, as long as it works. Please mark the thread as solved using 'Thread Tools' up top.

---

