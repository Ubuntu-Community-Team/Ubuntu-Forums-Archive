---
title: "Skype and PulseAudio nightmare"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by dookiebowser on 2010-06-10
I am wrestling with Ubuntu 10.4 to make my USB headset work in Skype. Upon investigation i've found this to be because of how Skype interacts with ALSA and PulseAudio(?).

With PulseAudio, Skype will only recognize and utilize my internal speakers and microphone. I use Skype as a home phone and it kills my experience. Plus I live in NYC and the background noise is a killer -- even when I **am** able to use a headset.

Others have had success by removing PulseAudio completely, which I tried. It [Skype] does start showing other devices like the USB headset. I wasn't able to get sound that way though, and it also killed Ubuntu's ability to go into the System Sound preferences. I'm going to try this again while waiting for a reply.

There was a fix made in HH: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) but i'm not sure if this is relative anymore or if it would have worked for me in the first place.

My USB headset works fine with PulseAudio everywhere except in Skype. I've went through the PulseAudio config utility and set the default devices to use, etc.


I've read, tested, and then read some more and tested some more. Hoping somebody has a fix for me. Thanks a lot in advance.

Ubuntu 10.4, Skype 2.1, PulseAudio 0.9.21 stable

**Problem Solved**

Had to download the OSS version *skype_static-2.0.0.72-oss.tar.bz2*. None of the other solutions worked.

Thanks to cesium of the OSS forums for this link, since Skype has taken this version off their servers:
[http://www.mediafire.com/?2ydhmj4yo3i](http://www.mediafire.com/?2ydhmj4yo3i)

---

### Post by cyrulution on 2010-06-12
I have a similar problem. Since 10.04 Skype only shows "Pulse Audio server (local)" in Options > Sound devices > Microphone. The webcam microphone is present in System > Preferences > Sound, but no chance to choose it in Skype.

I'd like to try your solution, but I have to confess I'm too stupid to install the package in Ubuntu. Synaptic does not take it.

---

### Post by jbrice on 2010-06-12
> I have a similar problem. Since 10.04 Skype only shows "Pulse Audio server (local)" in Options > Sound devices > Microphone. The webcam microphone is present in System > Preferences > Sound, but no chance to choose it in Skype.

Having been used to choosing the microphone source directly in Skype, I  found this confusing too. But for the two Lucid systems I have running Skype (a laptop and a desktop), selecting the microphone as source in System > Preferences > Sound > Input is all you have to do - PulseAudio does the rest.

If you have a Logitech webcam with a microphone, be careful not to set the "Input volume" at or too near to 100% as this kills the mic. signal. Also do not use the "Allow Skype to set my mixer levels" setting as it will wind the mic. gain up to 100% during a quiet moment and kill the mic. signal. Thereafter, once the mic. is dead, Skype will keep the gain at 100%.... :( (I have wasted a lot of time thanks to this behaviour on both Ubuntu and various flavours of Windows, so guess it's a flaw with Logitech hardware and/or drivers.)

---

### Post by alphacrucis2 on 2010-06-12
> **cyrulution said:**
> I have a similar problem. Since 10.04 Skype only shows "Pulse Audio server (local)" in Options > Sound devices > Microphone. The webcam microphone is present in System > Preferences > Sound, but no chance to choose it in Skype.

I'd like to try your solution, but I have to confess I'm too stupid to install the package in Ubuntu. Synaptic does not take it.

You don't need to choose it in skype. You select the input and output devices in pusleaudio preferences. If you don't already have them, it's a good idea to install some additional pusleaudio stuff via:

```
sudo apt-get paman
```

---

### Post by cyrulution on 2010-06-12
> **alphacrucis2 said:**
> You don't need to choose it in skype. You select the input and output devices in pusleaudio preferences. If you don't already have them, it's a good idea to install some additional pusleaudio stuff via:

```
sudo apt-get paman
```

Thank you, this was the solution. I did choose the Mic in Sound Preferences > Input. Now it works.

---

### Post by alphacrucis2 on 2010-06-12
> **cyrulution said:**
> Thank you, this was the solution. I did choose the Mic in Sound Preferences > Input. Now it works.


In case anyone tries it and doesn't realise why it doesn't work as I typed it in my previous post. It should have read:


```
sudo apt-get **install** paman
``` 

Sorry about that.

---

### Post by dookiebowser on 2010-06-12
> **alphacrucis2 said:**
> You don't need to choose it in skype. You select the input and output devices in pusleaudio preferences. If you don't already have them, it's a good idea to install some additional pusleaudio stuff via:

```
sudo apt-get paman
```


I'm going to try this out later. This would mean I can drop the OSS version and get whatever goodies came in the later releases.

---

### Post by HermanAB on 2010-06-12
Howdy,

My solution is to run the Pulse-audio-volume thingy and disable the audio interface input I don't want Skype to use, leaving it only the one I want it to use.

---

