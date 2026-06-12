---
title: "PC Speakers Not Compatible WIth Linux?"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by Deztruct on 2010-09-02
Ubuntu Community:

I never had a problem plugging in my personal computers speakers into my laptop to blast some music or videos!  But that was with Windows.  Now, since I have Linux, I am having a problem.  My laptop isn't picking up the speakers at all.

I was wondering if there was code or a way of being able to locate the speakers so i can play music through them!

Best,
Deztruct

---

### Post by bodhi.zazen on 2010-09-02
I doubt it is a problem with the speakers, what sound card do you have ?

See also : [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) 

for suggestions.

---

### Post by Deztruct on 2010-09-02
I want to make it clear that these speakers are NOT built-in speakers.  These are ones I took from my PC.  SO there's nothing wrong with my video card.  My laptop simply doesn't play music out of them where they;re plugged in. I tried the speakers in several other laptop's, and they've worked no problem!

---

### Post by kbless7 on 2010-09-02
Ok, that's fine, but that still doesn't mean your **sound card** doesn't have drivers installed. What laptop do you have?

---

### Post by Cypress421 on 2010-09-02
Open a Terminal from Applications -> Accessories -> Terminal, then type aplay -l and post the output.

---

### Post by Deztruct on 2010-09-02
The reason why I don't think it's the soundcard, is because sound does come out! Just not when I plug in the speakers :)

Here it is: 

[PHP]  
anthony@anthony-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
anthony@anthony-laptop:~$ ^C
anthony@anthony-laptop:~$ ^C
anthony@anthony-laptop:~$ 


[/PHP]

---

### Post by Cypress421 on 2010-09-02
Are you connecting the speakers to your monitor or the audio jack on your PC's back?

---

### Post by Jazzy_Jeff on 2010-09-03
I would assume he is plugging them into his headphone jack if it is a laptop. More than likely you need to adjust the volume for that. The easiest way is to plug the speakers in and turn on some music. Then open a terminal and type in alsamixer. Use your arrow keys to move to the different channels and start turning them up one at a time. I would start with the one that says Front. Make sure at the bottom of the level it says OO and not MM. If it is MM then hit the M key to change it. MM means it is muted. Let us know if this works or if you need further help.

---

### Post by forestG on 2010-09-03
There might be a possibility that Ubuntu recognises the jack as different output than the speakers. Same happens to me with the microphone. What you should check is the following:

Go here:
System->Preferences->Sound->Output. 
and check all possible options you may have. 
(Cannot be more than 2 or 3)

---

### Post by Deztruct on 2010-09-03
Well I go to sound, there are no options to check.  It just tells me what device I am using.  I can take screenshots to show you guys, but I don't know where to locate this pictures.  Can anyone help me with that?

And when I get back to my dorm, I'll definitely try plugging in the speakers and opening up the terminal like you guys told me to!  I will keep you updated.

---

### Post by migs73 on 2010-09-03
To take screen shots just press Ctrl & PrintScreen to get just the window currently in use or just PrintScreen to get the whole desktop. The system will then ask what to do with them. Save them to your Desktop.
To add to a thread, use 'New Reply' at the bottom of the thread not the quick reply box, and select the attachment symbol (paperclip), then click browse and click on desktop. Select the file(s) you wish to attach then click open(?) and then on 'upload'.

Done.

---

### Post by Jazzy_Jeff on 2010-09-03
> **Deztruct said:**
> Well I go to sound, there are no options to check.  It just tells me what device I am using.  I can take screenshots to show you guys, but I don't know where to locate this pictures.  Can anyone help me with that?

And when I get back to my dorm, I'll definitely try plugging in the speakers and opening up the terminal like you guys told me to!  I will keep you updated.

Did you open alsamixer in the terminal and do as I suggested in my previous post?

---

