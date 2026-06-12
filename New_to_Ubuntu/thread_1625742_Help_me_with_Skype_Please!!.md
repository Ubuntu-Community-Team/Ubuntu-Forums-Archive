---
title: "Help me with Skype Please!!"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by damienxx22 on 2010-11-19
hello all...

have no clue about ubuntu but i installed the 10.10 version and i cant get skype to work properly...

i can make calls to landlines and i can hear the other person talking to me but they cannot hear me at all...all they hear is a lil robotic sound...i have tested my skype with the sound test service and i could hear myself clearly so i dont think its a problem with the mic...

anyone know what the hek to do??

thanks

---

### Post by Aster-Phoenix on 2010-11-19
Where did you download skype?
I know that if you downloaded it from synaptic it had problems
if you did try uninstalling it and downloading it from the skype website

---

### Post by ivanovnegro on 2010-11-19
Hello and welcome.
Im not sure about it as you said the mic works, you activated the mic really?
In sound preferences enable the input for sound but seems that you already did that because you can hear you.

---

### Post by L Campbell on 2010-11-19
> **damienxx22 said:**
> hello all...

have no clue about ubuntu but i installed the 10.10 version and i cant get skype to work properly...

i can make calls to landlines and i can hear the other person talking to me but they cannot hear me at all...all they hear is a lil robotic sound...i have tested my skype with the sound test service and i could hear myself clearly so i dont think its a problem with the mic...

anyone know what the hek to do??

thanks


What type of microphone, headset, or whatever are you using?

Do you have a laptop or a PC?

---

### Post by Tangible on 2011-01-20
I am also finding that I can make skype to skype calls fine but landlines cannot hear me.
I've spent a lot of time looking at forums and there are some comments that this is an issue with pulse audio but am unable to debug the problem.  In the interim I have to go to windows to use skype to a landline.  If anyone has found a fix to this I would really appreciate some input.

Ubuntu: 10.10

---

### Post by lotus@terminal on 2011-01-20
I also recently installed Linux Ubuntu 10.10 and the Skype Linux guide on the Skype website worked very well for me. :)

---

### Post by Tangible on 2011-01-20
lotus@terminal: I have had skype installed for some time and thought it was working perfectly until I started making calls to landlines and found out that I cannot call landlines.  Have you tried calling landlines to see if it works?

---

### Post by Tangible on 2011-01-20
lotus@terminal: I have had skype installed for some time and thought it was working perfectly until I started making calls to landlines and found out that I cannot call landlines.  Have you tried calling landlines to see if it works?

---

### Post by Tangible on 2011-01-20
lotus@terminal: I have had skype installed for some time and thought it was working perfectly until I started making calls to landlines and found out that I cannot call landlines.  Have you tried calling landlines to see if it works?

---

### Post by lotus@terminal on 2011-01-20
Yes, I have tested it and I can make outgoing calls fine. Have you tried uninstalling it and rebuilding it via the terminal?

---

### Post by alexandra84 on 2011-01-20
I have sometimes also problems with Skype, one way audio.
Alternatively I am using another app to call landline of mobile pnone. 
Good sound. You can try it if you want.

---

### Post by ptrinder64 on 2011-01-20
Hi,

Not had a chance to test this out yet, but Skype recommends that as it is built natively for OSS you need to install the alsa-oss package either from synaptic or by opening the terminal and typing:

```
sudo apt-get install alsa-oss
```

The website suggests that this is because alsa is not natively supported and therefore needs to have an OSS wrapper.

Let me know if this works.

---

### Post by Tangible on 2011-01-20
Thanksfor your reply lotus@-  I recently re-installed it from the canonical partners repo (taking care to remove the .Skype folder, but not from a terminal though there shouldn't be any difference.  My installation works great unless I connect to a landline number and then my voice is not recognizable. 

Could you please let me know what your /etc/pulse/demon.conf parameters are for default fragments and default frag size are?  I've read that they may have direct bearing on my problem but cannot prove it.  Mine are set at default-fragments = 8 and default-fragment-size-msec = 10  Not sure if this is the problem but would appreciate being able to check this out against an install that is working.

Thanks....

---

### Post by rajeev1204 on 2011-01-20
> **damienxx22 said:**
> hello all...

have no clue about ubuntu but i installed the 10.10 version and i cant get skype to work properly...

i can make calls to landlines and i can hear the other person talking to me but they cannot hear me at all...all they hear is a lil robotic sound...i have tested my skype with the sound test service and i could hear myself clearly so i dont think its a problem with the mic...

anyone know what the hek to do??

thanks


Could you enable technical call info from skype options and see if there is some difference .It should display info when you move the mouse over the call window.You could compare this to a skype to skype call and see.

Also,even though webcam should not work for landline calls, try to disable video when attempting a landline call.

---

### Post by ptrinder64 on 2011-01-20
D'oh! My last post wasn't helpful at all...

However I just tried the following and it works for me:

Install pavucontrol from synaptic or from the terminal

```
sudo apt-get install pavucontrol
```

Run it, and click on the input devices tab. Bizarrely my mic turned up as muted on this whereas on other (e.g. alsa-mixer) the mic wasn't muted. I unmuted and this seemed to work.

If this doesn't solve the problem one solution in the Skype for Linux forum suggests doing the following:

> Found the answer, make sure that you turn off "Allow Skype to automatically adjust my mixer levels" in the Skype audio options.

Install pavucontrol "Pulse Audio Volume Control" via Synaptic Package Manager.

Using Pulse Audio Volume Control, select Input Tab and slide Front Left to 0%

Use Front Right slider to adjust mic volume, 100% works well enough.

You will need to unlock the channels. Don't use the normal sound config from the top panel to change volume, as it will re-lock the two channels back together and mic will mute again.

My Acer Aspire ZG5 (AOA150) has a bit of background hiss/noise, but voice is clear enough to understand.


--- taken from [http://forum.skype.com/index.php?showtopic=463251&](http://forum.skype.com/index.php?showtopic=463251&)

---

### Post by rajeev1204 on 2011-01-20
> **damienxx22 said:**
> hello all...

have no clue about ubuntu but i installed the 10.10 version and i cant get skype to work properly...

i can make calls to landlines and i can hear the other person talking to me but they cannot hear me at all...all they hear is a lil robotic sound...i have tested my skype with the sound test service and i could hear myself clearly so i dont think its a problem with the mic...

anyone know what the hek to do??

thanks


Could you enable technical call info from skype options and see if there is some difference .It should display info when you move the mouse over the call window.You could compare this to a skype to skype call and see.

Also,even though webcam should not work for landline calls, try to disable video when attempting a landline call.
Have you tried cfalling a landline of a different phone service? Maybe its a problem with how skpye connects to a network.

---

### Post by Tangible on 2011-01-20
> **rajeev1204 said:**
> Could you enable technical call info from skype options and see if there is some difference .It should display info when you move the mouse over the call window.You could compare this to a skype to skype call and see.

Also,even though webcam should not work for landline calls, try to disable video when attempting a landline call.
Have you tried cfalling a landline of a different phone service? Maybe its a problem with how skpye connects to a network.

This problem is being experienced by many people including myself.  It doesn't matter where the landline called is, if I call a landline they get garbled noise.  All I can find on this with regard to a fix is a re-adjustment of the mic- which didn't work, a change in the pulse audio server parameters and an instruction to create a "loop-back" device in pulse which I don't completely understand.  From what I've read so far it would appear that this is an problem related to pulse audio but how to fix it in Ubuntu evades me.

---

### Post by Jechem on 2011-01-20
I've totally removed pulse from ubuntu so that skype will work properly on my laptop.

[http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html](http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html)

maybe that will be helpful. I'm not sure of landline calls but maybe you can try it out.

---

### Post by Tangible on 2011-01-20
> **Jechem said:**
> I've totally removed pulse from ubuntu so that skype will work properly on my laptop.

[http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html](http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html)

maybe that will be helpful. I'm not sure of landline calls but maybe you can try it out.

Thanks Jechem for your comment.  I am 90% certain that the problem of bad output audio is caused by the pulse sound server but since I would prefer to retain the functionality of pulse for other applications I am looking for a fix that would give me Skype and preserve pulse on my system.  I'm sure that the answer is out there somewhere.

---

### Post by Jechem on 2011-01-20
I've tried installing alsa along with pulse before but Skype will not let you choose which one to use. It defaults to pulse as its sound server. Hopefully Skype would give the user controls to it because its a hit and miss with pulse and Skype.

---

### Post by Tangible on 2011-01-22
Hello all and thanks for your inputs.  I have spent another 10 hours or so looking for solutions and have tried a great many things.  Firstly, there are two main problems Ubuntu users are experiencing with Skype audio.  The first one has to do with getting Skype to play correctly with their systems through pulse audio... I don't have that problem.  Pulse seems to work fine in all respects and seems to be correctly configured to the Skype application.    The problem I am having is that landlines only cannot hear me.  They get a garbled, wavering distortion of the transmitted sound. I turned on "display technical details" and noticed that on skype->skype calls, i.e. the sound test service, that the codec invoked was SILK_V3 with a 24k sampling rate.  The audio through the pulseaudio server is crystal clear both sending and receiving.  When I place a call to a landline however the codec used is G729 at an 8k sample rate.  It is only when the G729 codec is invoked that the called party cannot hear me.    After many hours of messing with settings for pulse and changes in config files I have little reason to suspect that the pulse audio server is the culprit here (though I may be wrong).    I then went to windows and cranked up skype 5.something and tried to turn on the "display technical details{" however it failed to display the data for some reason so I cannot make a direct comparison on what codec is selected and it's sample rate but from windows skype works perfectly to landlines.  Given this problem I would ask that someone tell me what codec and what sample rate they see when they use skype to a landline.  The truth is out there somewhere..... I hope to find the root cause of this issue and get skype fully functional on Ubuntu as it is and has been my only phone for years now.

---

### Post by rajeev1204 on 2011-01-26
> **Tangible said:**
> Hello all and thanks for your inputs.  I have spent another 10 hours or so looking for solutions and have tried a great many things.  Firstly, there are two main problems Ubuntu users are experiencing with Skype audio.  The first one has to do with getting Skype to play correctly with their systems through pulse audio... I don't have that problem.  Pulse seems to work fine in all respects and seems to be correctly configured to the Skype application.    The problem I am having is that landlines only cannot hear me.  They get a garbled, wavering distortion of the transmitted sound. I turned on "display technical details" and noticed that on skype->skype calls, i.e. the sound test service, that the codec invoked was SILK_V3 with a 24k sampling rate.  The audio through the pulseaudio server is crystal clear both sending and receiving.  When I place a call to a landline however the codec used is G729 at an 8k sample rate.  It is only when the G729 codec is invoked that the called party cannot hear me.    After many hours of messing with settings for pulse and changes in config files I have little reason to suspect that the pulse audio server is the culprit here (though I may be wrong).    I then went to windows and cranked up skype 5.something and tried to turn on the "display technical details{" however it failed to display the data for some reason so I cannot make a direct comparison on what codec is selected and it's sample rate but from windows skype works perfectly to landlines.  Given this problem I would ask that someone tell me what codec and what sample rate they see when they use skype to a landline.  The truth is out there somewhere..... I hope to find the root cause of this issue and get skype fully functional on Ubuntu as it is and has been my only phone for years now.

Hi, i cant be of much help here but iam sure you cannot change which codec skype selects to connect to a call.

I also advice to follow the skype forums for any help on this.And try seeing again what codec gets used in windows.

---

### Post by Tangible on 2011-02-01
Thanks Rajeev1204.  The codec used for skype to landlines by V5x in Windows is G729, the same as the Linux version.  Having spent considerable time looking over why this does not work and considering that many Ubuntu users do not experience a problem I started to investigate what Pulse Audio had to say about it and what Skype is saying about the garbled voice problem.  Both claim that the fault is not their software and they both may be right.  

It appears that those who achieved a fix by changing their hardware configuration may have revealed that the problem is indeed a hardware incompatibility issue.  Many users report that they fixed the problem by adding a USB sound card.  I just installed a USB headset which Ubuntu see's as a second sound card and now I can call land lines all day long.  It does appear that the sound card in this Toshiba L300D laptop doesn't play well with the native sound card with regards to Skype.  While this problem is fixed on my computer using this "work-around" I doubt that any software fixes are going to be forthcoming either from Skype or PulseAudio because apparently this is a standards issue with the hardware.

---

