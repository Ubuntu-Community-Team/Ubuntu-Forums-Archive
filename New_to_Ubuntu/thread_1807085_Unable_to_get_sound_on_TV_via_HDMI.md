---
title: "Unable to get sound on TV via HDMI"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by TEDATKINSON on 2011-07-18
Hi all - I'm new here and hoping that this forum will be a great place to help me get used to ubuntu.

I have purchased a nanosaur 330i from Dinopc.com. Unfortunately, their technical help is not helpful - they don't answer the phone! :icon_frown:

I have connected the pc perfectly to my Toshiba Regza TV via HDMI to one of the 3 HDMI ports on the tv. The picture is excellent but I can't get any sound whatsoever. I've tried going into the sound settings, and selecting HDMI output - but still no sound. :confused:

Any help would be welcome.

---

### Post by LowSky on 2011-07-18
in sound preferences, go to hardware tab, click on the hdmi audo controller. then at the bottom change the profile until it works... I find playing music helps during the process.

---

### Post by TEDATKINSON on 2011-07-18
> **TEDATKINSON said:**
> Hi all - I'm new here and hoping that this forum will be a great place to help me get used to ubuntu.

I have purchased a nanosaur 330i from Dinopc.com. Unfortunately, their technical help is not helpful - they don't answer the phone! :icon_frown:

I have connected the pc perfectly to my Toshiba Regza TV via HDMI to one of the 3 HDMI ports on the tv. The picture is excellent but I can't get any sound whatsoever. I've tried going into the sound settings, and selecting HDMI output - but still no sound. :confused:

Any help would be welcome.

If it helps, it has an NVIDIA ION chipset and Realtek sound ALC8885 on board.

---

### Post by TEDATKINSON on 2011-07-18
> **LowSky said:**
> in sound preferences, go to hardware tab, click on the hdmi audo controller. then at the bottom change the profile until it works... I find playing music helps during the process.

Cheers Lowsky. Thanks for your swift response. If I could find sound preferences I'd try...sorry for sounding like an idiot, but I've had a lifetime of Windows!

---

### Post by LowSky on 2011-07-18
> **TEDATKINSON said:**
> Cheers Lowsky. Thanks for your swift response. If I could find sound preferences I'd try...sorry for sounding like an idiot, but I've had a lifetime of Windows!

the little sound icon on the top right, click it the menu will appear. Go to sound preferences, then the hardware tab, then click on the HDMI output in the middle, then at the bottom go to profile tab and try each one til the sound works.

---

### Post by TEDATKINSON on 2011-07-18
> **LowSky said:**
> the little sound icon on the top right, click it the menu will appear. Go to sound preferences, then the hardware tab, then click on the HDMI output in the middle, then at the bottom go to profile tab and try each one til the sound works.

Thanks LowSky - tried all of the settings on this (various input and output choices) and the only sound i can get is from the analogue stereo profiles playing through the inbuilt pc speaker and not via the TV.

---

### Post by LowSky on 2011-07-18
um... open the app called terminal.

type alsamixer

check if anything is muted

---

### Post by TEDATKINSON on 2011-07-18
> **LowSky said:**
> um... open the app called terminal.

type alsamixer

check if anything is muted

I'm trying that now. Just one thing as an aside, when I log into my authenticated wireless network, I am asked to enter a passwork for a keyring "Default" to unlock? I don't know what the password is??

---

### Post by TEDATKINSON on 2011-07-18
> **LowSky said:**
> um... open the app called terminal.

type alsamixer

check if anything is muted

Sorry mate, where do I find the app called terminal?

---

### Post by TEDATKINSON on 2011-07-18
> **TEDATKINSON said:**
> Sorry mate, where do I find the app called terminal?
Found the Terminal. Those that were muted I've now maxed up. nothuing specific to HDMI though.

---

### Post by jawilljr on 2011-07-18
> **TEDATKINSON said:**
> Found the Terminal. Those that were muted I've now maxed up. nothuing specific to HDMI though.

It's usually marked spdif or IEC958... also you might have to press F6 in alsamixer to change sound cards to see it.

Also with HDMI there is no slider to move up... make sure ate the bottom there is '00' not 'MM'... 'MM' means mute.

Please post output of:

```
aplay -l
```

And which distro are you running?

Jerry

On Edit:

Also what app are you trying to watch movies with?

---

### Post by TEDATKINSON on 2011-07-19
> **jawilljr said:**
> It's usually marked spdif or IEC958... also you might have to press F6 in alsamixer to change sound cards to see it.

Also with HDMI there is no slider to move up... make sure ate the bottom there is '00' not 'MM'... 'MM' means mute.

Please post output of:

```
aplay -l
```And which distro are you running?

Jerry

On Edit:

Also what app are you trying to watch movies with?

Not sure what distro - how can I find this out? 

I received a call from the tech help people at Dinopc.com this morning. Apparently, there is no way that you can get sound with the HDMI with Linux/NVIDIA. So they recommend connecting a phono cable to the TV which is ok as far as I'm concerned, as the TV's sound output is through a surround system anyway.

Obviously, I'd rather not use this method but it shouldn't really make too much of a difference for the general use we are looking at.

---

### Post by TEDATKINSON on 2011-07-19
> **jawilljr said:**
> 

Jerry

On Edit:

Also what app are you trying to watch movies with?

I haven't attempted any movies yet - pointless without any sound. I have a bluray player and a SKY HD box, so most TV and movies would be run this way. I do however, have a lot of old movies and home movies saved to portable hard drives etc which I would like to use the pc for.

I've only been attempting to get sound using live radio/youtube thus far.

---

### Post by jawilljr on 2011-07-19
> **TEDATKINSON said:**
> Not sure what distro - how can I find this out? 

I received a call from the tech help people at Dinopc.com this morning. Apparently, there is no way that you can get sound with the HDMI with Linux/NVIDIA. So they recommend connecting a phono cable to the TV which is ok as far as I'm concerned, as the TV's sound output is through a surround system anyway.

Obviously, I'd rather not use this method but it shouldn't really make too much of a difference for the general use we are looking at.

Can't get HDMI sound withe Linux/NVidia?  That's news to me. I have 2 desktops with NVidia HDMI working, one of them is going to my 5.1 sourround A/V receiver.

Anyway What I meant to say is what version of Ubuntu are you using?

Please open a terminal and post the output of:

```
uname -a
```

And

```
aplay -l
```

Also please read [this thread,](http://www.nvnews.net/vbulletin/showthread.php?t=159346) and read this[NVidia HDMI audio documentation](ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)

Jerry

---

