---
title: "logitech v10 laptop speakers not working"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by gertrude58 on 2009-03-07
I have dual boot with vista and ubuntu.When I first tried the speakers with ubuntu they didnt work so I discovered how to select them in sound preferences for playback and devices.This worked for a few days then suddenly didnt any more.I checked and they are still selected in sounds.Rhythmbox will play but ignores the speakers,and songbird completely seizes up if the speakers are plugged in and refuses to play at all.I get'media playback error'but as soon as I unplug speakers it will play.
I would be very grateful for any help being a total novice.thanks
:(

---

### Post by kostkon on 2009-03-07
> **gertrude58 said:**
> I have dual boot with vista and ubuntu.When I first tried the speakers with ubuntu they didnt work so I discovered how to select them in sound preferences for playback and devices.This worked for a few days then suddenly didnt any more.I checked and they are still selected in sounds.Rhythmbox will play but ignores the speakers,and songbird completely seizes up if the speakers are plugged in and refuses to play at all.I get'media playback error'but as soon as I unplug speakers it will play.
I would be very grateful for any help being a total novice.thanks
:(
No, you need to go to your sound preferences again (i.e. *System &#8594; Preferences &#8594; Sound*) and set all your playbacks back to *Autodetect*.

Then, the thing you need to do is to install the *PulseAudio Device Chooser* utility (using *Synaptic*. It will create a menu entry in *Applications &#8594; Sound & Video*). Run it, left-click on its icon in your system tray and select *Volume Control*.

In the *Input Devices* and *Output Devices* tabs you can set the default input and output device to be used by your applications. Right-click on the device you want and enable the *Default* option. Thus, I assume you'll want to set here your Logitech USB speakers as the default output device. Afterwards, all your applications will send their audio to your speakers by default.

Also, from there, if you want, you will be able to send the audio stream of one application from one device to another in real time (if in the future you will have more than one audio device, or if you have already and you want to use it instead of your USB speakers, for example. Also, maybe in some rare cases, you will need to manually send the sound of some apps to your USB speakers). In the *Playback* tab you should see the audio streams of your running applications (the ones that produce audio only, of course). Right-click on one and select *Move Stream...* to move its audio to the device you want.

You can set *PulseAudio Device Chooser* to start every time you login from its preferences.

Hope that helps...

---

### Post by gertrude58 on 2009-03-07
Thanks ill give it a try.:):o

---

### Post by gertrude58 on 2009-03-07
It works a treat,thanks again:D

---

### Post by gertrude58 on 2009-03-08
Another question![sorry to be so dim].Is there an easy way to swop between sound with speakers and sound without them? They work well but if they arent plugged in I have no sound at all.Thanks.Hope you see what I mean.

---

### Post by kostkon on 2009-03-08
> **gertrude58 said:**
> Another question![sorry to be so dim].Is there an easy way to swop between sound with speakers and sound without them? They work well but if they arent plugged in I have no sound at all.Thanks.Hope you see what I mean.
In theory, when your speakers aren't plugged in, your sounds must go to the next available audio device.

What happens exactly in your case if, for example, you put something playing in *Rhythmbox* and then suddenly unplug the USB speakers.

Also, what is your 2nd audio device, if you have one?

---

### Post by gertrude58 on 2009-03-08
I really am as dim as I thought! There's nothing wrong withthe sound at all,but when I was using the speakers I turned down the sound at the volume control on the top panel as speakers made sound much louder,then promptly forgotI'd done it.Thanks again for all your help.

---

### Post by arkmundi on 2009-04-10
Thanks for the tip on PulseAudio Device Chooser, which I installed via the Add/Remove application.  I bought the jlabsaudio.com B-Flex USB speakers.  This doesn't show up in the Output Devices tab.  My Dell Inspiron 1525n Ubuntu 8.04 machine is somehow not finding the USB device.  Any clue?

---

