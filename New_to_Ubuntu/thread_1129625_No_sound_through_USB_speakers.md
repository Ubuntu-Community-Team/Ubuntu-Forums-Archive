---
title: "No sound through USB speakers"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Shintrick on 2009-04-18
I've followed advice given on a bunch of forum posts relating to this but can't seem to figure it out. 

I can't get any sound out of my USB speakers. When I had Windows on this machine they worked fine, so I'm not sure what the issue is. My sound card works - I can get sound when I plug headphones directly into it. In Settings Manager -> Sound, there are three options on the drop-down: default, #0: C-Media CMI8738, #1: USB Audio DAC. Even if I select the latter...no sound.

I downloaded what I think are the right alsa module drivers. Don't know where to take it from here.

Any help would be great.

---

### Post by freeman2000 on 2009-04-20
[bump]

---

### Post by gackt on 2009-04-21
unplug the speaker and type lsusb in the terminal, plug it and type lsusb again. Is there new usb detected on the lsusb result?

---

### Post by Shintrick on 2009-04-22
Yup.

Before:
```

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

After:
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 08bb:2704 Texas Instruments Japan 
Bus 001 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by Shintrick on 2009-04-26
Can anyone tell me what to do next? It's apparently recognizing my speakers as 'Texas Instruments' (even though they are made by Creative...) - am I possibly missing a driver for this?

---

### Post by kostkon on 2009-04-26
EDIT: I now saw that we are talking about *Xubuntu*. I don't know if *Xubuntu* comes with *PulseAudio*. So, please disregard the post below if *Xubuntu* doesn't have *PulseAudio*.

Your USB speakers seem to be recognised fine.

The thing you need to do is to install the *PulseAudio Device Chooser* utility from *Synaptic*.

Run it (*Applications &#8594; Sound & Video*) and then right-click on its icon in the system tray and select Volume Control.

You will be able to set your USB speakers as the default output audio device in the *Output Devices* tab. There, you should see your USB speakers and your sound card listed. Just right-click on your USB speakers and enable the *Default* option.

In the *Playback* tab you will be able to send on-the-fly the audio streams of the various applications from your card to your USB speakers and vice versa by right-clicking on the audio stream and selecting *Move Stream...*

For this to work you'll need to set your sound playbacks in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) to *Autodetect*.

Hope that helps.

---

### Post by KarenAK on 2009-04-29
Thank you kostkon - that was very helpful ! :-)

---

### Post by Shintrick on 2009-05-05
Thanks for your help. Installed Jaunty and now works fine.

---

