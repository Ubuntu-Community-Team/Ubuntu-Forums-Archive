---
title: "gmail cell phone"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by Grumpywolfe on 2011-05-29
Hi all first off I like what has been done to xubuntu. Now my problem, it is very important to me to have the gmail cell phone to work for I use it to call my kids all the time.

the computer is a 
Acer Aspire one netbook 532h
xubuntu 11.4
Firefox 4.01

I do know this works on this computer for when I had puppylinux install used it all the time

---

### Post by LowSky on 2011-05-30
> **Grumpywolfe said:**
>  Now my problem, it is very important to me to have the gmail cell phone to work for I use it to call my kids all the time.... I do know this works on this computer for when I had puppylinux install used it all the time

Sorry can you explain what you need your phone to do?

I'm guessing your trying to use Google Voice from Gmail?

---

### Post by Grumpywolfe on 2011-05-30
Yes I am trying to use the voice and chat to call my kids cell phones but I did find out that the mic is not acceptable by the google plugin because it is not at the default level so well have to get and external one and try that.

I found the information at this link
[http://mail.google.com/support/bin/answer.py?hl=en&ctx=mail&answer=100173](http://mail.google.com/support/bin/answer.py?hl=en&ctx=mail&answer=100173)

in this comment.
> I know the reason why the microphone is not working, and I'd like to suggest Google a minor modification to get microphone audio for many Linux users.
I'm a Linux user (distribution here is irrelevant) and I can't get my microphone working with the Google voice plugin.


Technical stuff:
- ALSA based sound system, like most distributions
- the list of devices provided by "arecord -l" is the following:
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC889A Analog [ALC889A Analog]
Subdevices: 2/2
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1

The problem with Google plugin is that it offers for the mic input only most playback options, which are not talking to the correct audio device driver. From the device list above, only one configuration get the microphone audio: hw:0,2 (in other words, device 0, subdevice 2); Google Plugin only offers the "default" (hw:0,0) and some useless playback options.

Solution for better Linux compatibility:
Give the user more choices in the "Microphone" list, by also including all the subdevices available from the ALSA list.

---

### Post by Grumpywolfe on 2011-06-01
I count this as solved but the only way to salve it was to buy and external mic and use it. But now have clear chat with google chat and voice.

---

