---
title: "Low Mic Volume"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by HackerOfDoom on 2010-03-20
Hi everyone, I'm sorry I am making a new post as there is probably one out there already, but, here goes:
I have installed the newest skype beta and called my friend, who reported (after a little tweaking) that he could barely hear me.  I don't know why this is, I use skype on my (boooo) Windows partition and it works fine, other than a little crackling.  Any help would be great!  Thanks in advance.

---

### Post by _h_ on 2010-03-20
Have you tried playing around with the Skype input settings (if it has such) or the ubuntu sound preferences for Input?

System -> Preferences -> Sound -> Input tab

---

### Post by sebastianabate on 2010-03-20
And uncheck the option "Allow Skype to automatically adjust my mixer levels" in Sound Devices option in Skype

---

### Post by florin-ganea on 2010-03-26
I have the same problem - low level on microphone.
Input volume is set to max.
Skype is not allowed to automatically adjust mixer levels.
In karmic I had similar problem, but solved by increasing the input volume level towards the max; the drawback was background noise.

---

### Post by florin-ganea on 2010-03-26
Same issue in sound recorder; so it is not related to skype.

---

### Post by gradinaruvasile on 2010-03-26
Launch alsamixer in a terminal. Then press tab (this will take you to the recording view). Post a screenshot.

PS: The Skype level adjusting thingie will leave the bad settings behind even it is disabled...

---

### Post by florin-ganea on 2010-03-26
Here it is. 
I am aware of what you said.
Thanks.

---

### Post by gradinaruvasile on 2010-03-26
Turn up the volume on "Line" with up/down keys.

But i see you have a USB card? Or this is the internal card? Something isnt right if it is.

Also, have you tried the options in sound preferences (right-click from the tray volume icon)?

---

### Post by florin-ganea on 2010-03-26
Changing "Line" level has no impact. It is correct that I have an USB soundcard.

Problem solved:
- alsamixer: Line - 0%, Mic - 100%, PCM Capture Source - "Mic"
- set Input volume from Input tab, Sound preferences, to max
- restart the system
Without restarting the system there was no real improvement.

Thanks for ideas.

---

### Post by gradinaruvasile on 2010-03-26
You are welcome.

---

### Post by kit1980 on 2010-04-29
I have the same problem. 

Mic worked perfectly in Karmic, but in 10.04 I have only very-very low volume distorted sound in Skype. 

Mic still works for playback (I can clearly hear my own voice from speakers in real-time, and if I raise the volume I got audio feedback) but not for capture.

I tried to adjust various settings in alsamixer with no success. Also I no longer have "capture source" switch in mixer - maybe this is a cause...

---

### Post by florin-ganea on 2010-05-03
Hello,

For me it worked like this: System->Preferences->Sound->Input.
Moved the slider to the max and restart the computer.
After that, I have moved the slider to 100% and restarted again.
No problem after this.

Well, almost no problem...
I am with 10.04 since beta1. Each time the kernel was updated, I had to restart the computer once more than required (1 for the kernel and 1 for the sound input stream to work).

Best regards,
Florin

---

### Post by mantorpcity on 2010-06-08
> **florin-ganea said:**
> Hello,

For me it worked like this: System->Preferences->Sound->Input.
Moved the slider to the max and restart the computer.
After that, I have moved the slider to 100% and restarted again.
No problem after this.

...

Best regards,
Florin

You're a star, this worked for me. No restart required even.

Thanks

---

### Post by flying_174 on 2010-06-09
This is what solved the issue for me.

From Ubuntu Software Center 
Install Default Sound Card and Pulse Audio Volume Control 
Then, open Pulse Audio Volume Control. Select Input Devices. There  should be 2 sliders, and a input tester at the bottom. Speak into the  mic. you will know if it is working. If it is not, slide the slider that  says Front Left, to 0%. Now speak. If the mic works here your good to  go. 

Hope this helps.

---

### Post by randomAccess on 2011-04-10
> **flying_174 said:**
> This is what solved the issue for me.

From Ubuntu Software Center 
Install Default Sound Card and Pulse Audio Volume Control 
Then, open Pulse Audio Volume Control. Select Input Devices. There  should be 2 sliders, and a input tester at the bottom. Speak into the  mic. you will know if it is working. If it is not, slide the slider that  says Front Left, to 0%. Now speak. If the mic works here your good to  go. 

Hope this helps.

THANKS!!!! This solved my problem with Ubuntu 10.10 and Skype.

---

