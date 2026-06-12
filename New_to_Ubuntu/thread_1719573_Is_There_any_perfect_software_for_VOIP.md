---
title: "Is There any perfect software for VOIP"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by desaivarun_104lts on 2011-04-02
Hi,

I tried ubuntu 10.04,10.10. now i am using natty.In these three distro's i am unable to use skype,empathy,ekiga to audio and video chat..

In 10.04 and 10.10 ,i am in worst scenario.My internal mic is unable to record my voice.Now in Natty,sound recorder is able to record my voice and i can hear my voice with little bit of disturbance.

But my problem is i cant use skype or any other voip to talk to my sister.I can hear the lady voice in the skype,when i talk,i cant hear my voice(Unchecked the automatically adjust the mixer levels also).Same problem with the empathy also.In empathy no video and audio.Tried Ekiga also,here also i am fail.

Is there any VOIP app,so that i can talk and see video.

I am a die hard fan of ubuntu,i am the only one who using ubuntu in my family.I motivated everyone to use ubuntu. Therotically i proved them.

But,in the case of voip i failed.Please can any one suggest me the best app to talk with my sister.Surely,i am in need of help.

Thanks in advance friends..

---

### Post by gradinaruvasile on 2011-04-02
This has been discusses thousands of times.
The problem is not any applications (Skype works perfectly BTW), it is simply your microphone not being used by the OS to capture. And this naturally applies to ALL programs.

Now the reasons can be:

PulseAudio applet checklist:
- The PulseAudio server output profile is set to "Analog Stereo Output" instead of "Duplex" (happens sometimes)
- Another input device is selected - line in/other microphone
- The microphone is muted somewhere - either in PulseAudio - that is easy to check

ALSA checklist:
- either in Alsa - this can be checked with alsamixer from the command line - press tab and see the capture devices.


- The sound hardware is not set up correctly by Alsa - now this is a pain to debug, there are cases when this can be solved by certain config options to the modprobe.conf file or updating ALSA or the kernel.

Most times the problem is in alsamixer or pulseaudio.

---

### Post by marl30 on 2011-04-02
This should work: [https://imo.im/](https://imo.im/). The Google Chrome App version works a lot better though.

---

### Post by desaivarun_104lts on 2011-04-02
@Gradin

I agree with you,it has been discussed thousand of times,they why ubuntu developers are unable to create a perfect interaction of sound card with  hardware and software.The programme cheese is perfect for webcam for every user of ubuntu(it detects almost all the webcams),they why there is no such type of software for sound.We can hear only the output,not our input(For maximum people,input mic is the problem)

You have to understand my problem,for this i changed from 10.04 to 10.10,now i am using 11.04.

---

### Post by gradinaruvasile on 2011-04-02
> **desaivarun_104lts said:**
> @Gradin

I agree with you,it has been discussed thousand of times,they why ubuntu developers are unable to create a perfect interaction of sound card with  hardware and software.The programme cheese is perfect for webcam for every user of ubuntu(it detects almost all the webcams),they why there is no such type of software for sound.We can hear only the output,not our input(For maximum people,input mic is the problem)

You have to understand my problem,for this i changed from 10.04 to 10.10,now i am using 11.04.

Webcams are simple things - they just transmit a stream of data with no complicated configuration implied. The driver has to know the encoding of it and maybe some adjustment options. They either work or dont - not half-half as some of the audio noards.
The issue is that the standard Linux webcam interface (v4l) was changed from version 1 to 2 and some programs such as Skype have to use a workaround (load a compatibility library with LD_PRELOAD) to be able to use them - if you see the camera in gstreamer-properties or cheese, that means that the camera is usable and if a particular program has issues with it, its that programs fault.

Audio hardware is more varied than webcams and the hardware compatibility depends on the ALSA (Advanced Linux Sound Architecture) implementation for that particular board. The issue sometimes is that the card is a modified version of a known card or the card's hw id is not in the ALSA database and ALSA has to guess configs.
Now because Linux is not a standard like Windows, vendors dont always make drivers available (although recently the situation begins to improve) for their hardware so the ALSA developers have to test on what they have or the users who sent bug reports have. This applies to webcams too.

None of the above cases can be solved directly every time by the distro maintainers because in case of major issues they have to talk upstream to the guys who maintain the code for the v4l/v4l2 and ALSA interface - and this can take time.
In any case the user should file a bug to the coresponding package/component in the Ubuntu bug tracker if he wants to be taken seriously. This is the way bugfixing works in Open Source.
There is no magic one-shot solution to audio issues because of the above situation. I personally had only minor issues with mics and i installed Ubuntu and Debian on about 10 computers. Most of the time the issue was a minor thing that could be solved from alsamixer. And sometimes PulseAudio was the culprit, removint it i had everything working.

---

