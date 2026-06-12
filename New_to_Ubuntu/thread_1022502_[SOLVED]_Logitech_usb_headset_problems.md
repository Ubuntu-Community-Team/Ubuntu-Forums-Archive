---
title: "[SOLVED] Logitech usb headset problems"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by WASHAD on 2008-12-26
I have logitech's usb headset that I'd like to use with skype, but skype gives me a 'problem with audio playback' error. I have my sound preferences set (attached) but it doesn't seem to help. Any suggestions?

Thanks, 

SteveJ

---

### Post by kostkon on 2008-12-27
> **WASHAD said:**
> I have logitech's usb headset that I'd like to use with skype, but skype gives me a 'problem with audio playback' error. I have my sound preferences set (attached) but it doesn't seem to help. Any suggestions?

Thanks, 

SteveJ
What version of Ubuntu do you have?

---

### Post by WASHAD on 2008-12-27
8.10 --- Wubi

---

### Post by kostkon on 2008-12-28
OK. I think you could try the following:

In your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) set all of your sound playbacks to *Autodetect*. It is better to set your sound capture device to *PulseAudio*.

Install the *PulseAudio Device Chooser* utility from *Synaptic*. This utility will allow to easily reroute the audio produced from your applications from one device to another and have individual volumes per application and some other things.

Run it (it will create a menu entry in *Applications &#8594; Sound & Video*) and it will its icon in your taskbar.  

Then open *Skype*, go to its sound preferences and set the *Sound Out* and *Ringing* to *pulse* and your *Sound In* to your USB headset (alternatively, you can also set this to *pulse*, but I don't know if it works well. But for this to work, you need to set your headset as the default input device in the *PulseAudio Device Chooser*. More on this below).

Left-click on *PulseAudio Device Chooser*'s icon and select *Volume Control...* There, your sould see *Skype* listed in the *Playback* tab. Right-click on it and select *Move Stream to...* and in the list that will appear select your headset (obviously). Thus, from now on the sound from *Skype* will go to your headset.

You can do the same for any other application running that produces audio. *PulseAudio* will remember your choice the next time you run the application again. Thus, in other words you can easily and in real-time reroute the sound of applications from one device to another (e.g. from your sound-card/speakers to your headset or the opposite). Very nice and useful.

Also, select the *Output Devices* tab to set the default output device. You should see your headset and your sound card(s) listed there. For example, you may want by default your applications to use the speakers to output their sound. Thus, right-click on your sound-card and enabled the *Default* option. 

Do the same in the *Input Devices*.

Hope that helps.

For any questions or problems regarding the above, don't hesitate to ask here.

---

### Post by WASHAD on 2008-12-28
Awesome, I'll give that a try and post back if it solves it. 

SteveJ

---

### Post by girark on 2008-12-28
I am having a similar, if not the same, problem. I'm using a Logitech USB headset, Ubuntu 8.10 and Skype 2.0.0.72 on a ThinkPad R61. I attempted the fix in #4 (using the Pulse settings) but I continue getting "Problem with Audio Playback". In the sound preference menu, I can get both the headset playback and audio in to test fine. However, in Skype, I don't see any options for Logitech devices, only:
[LIST]
[*]Default
[*]HDA Intel (hw:intel,0)
[*]HDA Intel (plughw:intel,0)
[*]HDA Intel (hw:intel,0)
[*]HDA Intel (plughw:intel,0
[*]hdmi
[*]headset
[*]pulse
[/LIST]

When I set the Skype Sound Out to "pulse" I managed to get sound out of my speakers, but nothing out of my headset. Thanks for any help you can offer!

---

### Post by wmoore on 2008-12-29
> **girark said:**
> I am having a similar, if not the same, problem. I'm using a Logitech USB headset, Ubuntu 8.10 and Skype 2.0.0.72 on a ThinkPad R61. I attempted the fix in #4 (using the Pulse settings) but I continue getting "Problem with Audio Playback". In the sound preference menu, I can get both the headset playback and audio in to test fine. However, in Skype, I don't see any options for Logitech devices, only:
[LIST]
[*]Default
[*]HDA Intel (hw:intel,0)
[*]HDA Intel (plughw:intel,0)
[*]HDA Intel (hw:intel,0)
[*]HDA Intel (plughw:intel,0
[*]hdmi
[*]headset
[*]pulse
[/LIST]

When I set the Skype Sound Out to "pulse" I managed to get sound out of my speakers, but nothing out of my headset. Thanks for any help you can offer!
You just got me thinking .... I use Skype a fair bit and have just converted from Fedora to Ubuntu (and been very happy so far :)) but hadn't got around to testing Skype. I have Skype running at startup and after plugging in my Logitech dongle, Skype doesn't show it, though 'aplay -l' does. I played around with a few settings to no effect before having a brainwave. I killed Skype, then plugged in the dongle, then restarted Skype and voila! Logitech headset options in audio devices :D

---

### Post by girark on 2008-12-29
Awesome! That did the trick. Thanks!

---

### Post by WASHAD on 2008-12-29
> **kostkon said:**
> 
Left-click on *PulseAudio Device Chooser*'s icon and select *Volume Control...* There, your sould see *Skype* listed in the *Playback* tab. Right-click on it and select *Move Stream to...* and in the list that will appear select your headset (obviously). Thus, from now on the sound from *Skype* will go to your headset.


Thanks again for this. With your help I was able to get it to work. The only think that I had to do differently than your instructions was to have Skype make a test call while I had the playback tab open. Only then did it show me an application (Skype). 

That was just a small detail, though. Everything else worked awesome. 

'preciate the help. 

SteveJ

---

### Post by kostkon on 2008-12-30
> **WASHAD said:**
> Thanks again for this. With your help I was able to get it to work.
:):):):)
> **WASHAD said:**
> The only think that I had to do differently than your instructions was to have Skype make a test call while I had the playback tab open. Only then did it show me an application (Skype). 

That was just a small detail, though. Everything else worked awesome. 

'preciate the help. 

SteveJ
Yes, indeed, apps are shown in *Playback* only while they produce audio. Sorry for forgetting to give this (rather important) detail!  ](*,)

---

