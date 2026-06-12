---
title: "Logitech C250 webcam microphone"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by dndrich on 2009-11-21
Ubuntupals:

OK, just purchased a Logitech C250 webcam. Works just great in Karmic 64 bit. Now, the device plugs into a USB port with a single plug. It also has a microphone built into it. How do I get that mic to work?

---

### Post by laidback on 2009-11-22
I had this issue with a Logitec 3000 using USB, whereas my previous mic had used the mic port on the sound card.

Try this, top right of screen in task bar press the loudspeaker icon. Now you'll see "Volume Control..." press that too. Now a new window will appear which is called "Volume Control xxxx". 

At the top of the window is a drop down, select "CAPTURE USB device..." now adjust the slider as required. If you can't see the slider you need goto preferences and select it as required. 

You'll notice that you can adjust/select many devices/options here as if it were Alsa Mixer. I've used both but for the mic issue found the above worked fine for me. I hope it does for you too.

---

### Post by anders_c_ on 2009-11-22
@laidback
He says hes using Karmic...I'm pretty sure the instructions you gave are for an older version.

What program are you using with your webcam? I think it might be different solutions for different programs, Cheese usually works fine but if you're trying to use it in empathy i have no idea.

---

### Post by laidback on 2009-11-22
Quite right, I'm still on Jaunty so probably different. I've used Skype, Sound Recorder and Cheese but not Empathy. Sorry if I misled anyone. Alsa Mixer or Gnome Alsa Mixer (GUI version) may still help.

---

### Post by dndrich on 2009-11-22
Yup, using Karmic, and I don't see anywhere where the USB mic is detected in sound. I want to use it for Skype, but that is another matter. I would think that it has to be seen by pulse audio somewhere, but I don't know where.

---

### Post by laidback on 2009-11-23
You can choose Options in Skype and then select the devices/options via Sound devices. You should see a USB for sound in, I found Pulse works for Sound out and Ringing. But you may need to play a little. Use the Test buttons just below the drop downs used in above selections.

Is Karmic really that different to Jaunty that you don't have the loudspeaker icon in the task bar? and sound is handled in a different way?, not looking forward to that if it is.

---

### Post by dndrich on 2009-11-24
Unfortunately there is no such choice in Skype. The only choice is pulseaudio server. There is a volume control in Karmic on the panel. When right clicking you can bring up the sound options. But USB mic does not appear.

---

### Post by laidback on 2009-11-25
In that case I suspect that it's not being recognised as a device at all. I Have a feeling this means trying to load the driver you got with it using ndsiwrapper..with which I have never had any assured success but I know others have. Someone in the forum will have posted the instructions I'm sure.

---

### Post by Novacainekidd on 2009-12-25
So i just recently got this webcam and i do not know which drivers to download. where do i even begin 0.0 help is appreciated

---

### Post by stardustdk on 2009-12-25
Hey.

It may sounds strange, but Skype forced me back to 9.04 (Jaunty).

A fresh install of 9.04 and the Mic did work on my LG K2 Express Dual Laptop with front mic (no internal mic).

Are trying to find a Webcam with mic that does work with 9.04, have abandoned 9.10 total because of sound problems in many PC's (both mine and people, I help).

(If there still will be sound problems in 10.04, I abandon Ubuntu totally).

---

### Post by gsimpson on 2009-12-25
SOLVED for me getting USB logitech camera going. The video but not sound worked.

Ubuntu 9.10
Skype 2.1.0.47

HOWTO
System>Preferences>Sound
Select Input
Select Device to use (in my case, quickcam rather than internal mic)
Adjust input volume

I did a test call to Skype and it worked fine.:popcorn:

---

### Post by Lambertus on 2010-01-09
UBUNTU 9.10
Logitech 3000 webcam USB sound
Skype 2.1.0.47

Same solution worked for me, after setting the alsamixer for sound device 1 capture to high volume. Volume default was off for the device. (in terminal window:  alsamixer -c 1 -V all)

System>Preferences>Sound>
Set mic to webcam

---

### Post by Hieronymus Josch on 2010-02-27
Yeah,

I'm running 9.1 and have the same webcam, the C250 and webcam isn't an input option under sound preferences.  Anybody have any idea what's going on here?  I don't have ALSA but am damn tired of pulseaudio.  Is there a good walkthrough on getting rid of pulse?

---

### Post by Hieronymus Josch on 2010-02-27
Never mind,

For whatever reason, my mic isn't listed as "webcam" but as "analog device" something or other.  Which makes no sense as USB, is in no way analog.  It's also pretty stupid that the ALSA mixer isn't accessible through the sound options and that it's automatically muted.  I love ubuntu but sometimes it's bass akwards.

---

