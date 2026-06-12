---
title: "Logitech QuickCam Orbit AF no audio, Skype doesn't see device"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by phubert28 on 2010-05-24
I am running 64 bit Ubuntu 10.4 on a Dell Optiplex 360 2.66GHz Intel Core Duo

I have a Logitech QuickCam Orbit AF.
Cheese sees the video & can manipulate the device.

Skype doesn't even SEE it and receives no audio FROM it.

The Skype window that comes up has no Preferences or Options controls.

Anyone know anything about Skype OR the Logitech device??

---

### Post by BandD on 2010-05-24
Hi.  It's me again!  :)  For the camera you can try a possible fix I talked about on this [thread]("http://ubuntuforums.org/showpost.php?p=9317367&postcount=4")  The directories might be slightly different on 64bit.  Check for a /usr/lib/lib32/libv4l directory if it doesn't work.

I don't have any experience wit a mic/webcam combo, but does it show up in Sound Preferences (left click the volume icon) Input tab under "Choose a device for sound input"?  If not you can try and install pulse audio device chooser (package name is padevicechooser) and see if you can set the camera as the input device there.  It's a gui frontend to the pulseaudio sound server.

Skype does have an options menu in linux,it's just not intuitive.  There's a little skype icon in the lower left of the main skype window.  Click on it.  The menu might be dark text on dark background, but when you hove the mouse over it should lighten and you can find the options menu.  (to fix the dark text issue, when the options menu pops up  on the general tab at the bottom it says "Choose Style" select "Desktop Settings".  Anyway in the options menu there is a sound devices tab and video devices tab. 

Hope that helps!

---

### Post by phubert28 on 2010-05-24
Well, I found out I have more of a problem with the sound adjustments than with device function or recognition. I was unaware of the System > Preferences > Sound ... and found that it recognized both my headsets, the Orbit, and of course the sound bar on my RH monitor.

However, for at least the FREETALK headset, if I did anything with the sound slider, it either shut the sound off ENTIRELY or blasted my ears off.

I seem only able to obtain SOME degree of granularity in sound adjustment when the speakers are selected.

However, it explains why I thought the sound wasn't working at all.

'Sounds' to me as though Linux needs better sound DRIVERS.

Anyway, I've gotten Skype to work... I don't know how well it will work (sound clarity) however... I guess I'll just have to wait 'til my (nearly deaf) friend returns and wants to make a video call.

Thanks for dropping-in.

---

### Post by SRST Technologies on 2010-05-24
What makes you say that Linux needs better sound drivers?  Is it that you didn't have to install one at all, and that with Windows scouring the net for a driver with an operating system that never tells you chipsets or what is even plugged into the bus if you don't have the drivers is loaded?

---

### Post by phubert28 on 2010-05-24
Well, I said that because the sound level adjustments simply don't seem to work well at all.

Under Windows, I had one control with settings for each type of output.

Windows had ITS problems, but at least for each output device (headsets, speakers) and the microphone inputs I could adjust sound continuously with reasonable granularity and decent quality.

Right now on this system with these devices (the same system I had been running Windows on 'til it tanked (would boot fully then hang... and yes, I may STILL reinstall as it got to that point... I just considered it an opportunity to dive into Ubuntu ... and perhaps unwisely chose 64 bit rather than 32), how the controls respond depend on which device (even which HEADSET) I'm using... and both mic and phone sound quality seems poorer.

So, are none of these driver issues???

But then I've also heard that 64 bit Windows OSes have issues as well.

I find that a bit strange since every CPU put out these days is 64 bit capable... why IS anyone still doing 32 bit, anyway???

---

### Post by BandD on 2010-05-24
Out of curiosity, which "sliders" are you messing with?  

Did you install the padeviechooser package.  It functions slightly differently, so you may find it works better than the System --> Prefences --> Sound settings.  Worth a shot.

---

### Post by phubert28 on 2010-05-25
Well, the sound icon on the launcher bar has a slider.
Also, System > Preferences > Sound has sliders for Input and Output.

What else could there be????

---

### Post by Linuxforall on 2010-05-25
Enable partner repository, Skype is now there and an updated version, see if that fixes it for you.

---

### Post by phubert28 on 2010-05-25
Well, that set me off looking to find what Partner Repositories were and how to activate them... Google is SO helpful! :-)

So, THANK YOU, Linuxforall, for pointing me to that. Another little tidbit about Ubuntu.

I upgraded the Skype, but I think sound may be another issue since it BEHAVES differently for each of my headsets and the speakers.

BEFORE the upgrade I had gotten Skype to access all of these.
The sound quality is poor, however, and sound controls for the headsets are pretty bad.
I suppose I should get a headset with its own sound controls to compensate.

Again, I suppose it may also be that I'm suffering because I chose 64 bit over 32 bit Ubuntu... I wonder when 32 bit will be simply left behind in the dust - as it SHOULD.

---

### Post by BandD on 2010-05-26
You may be able to change some settings for the driver that improve your input capabilities.  You can type the following in a terminal to tell you what soundcard you have: ```
lspci | grep -i audio
```

And also the following to tell you what chipset/codec is used: ```
aplay -l
```  Depending on your output there may be some settings/profiles you can change in the ALSA driver being used.

---

### Post by phubert28 on 2010-05-26
Thank you again, BandD.

By the way, does the handle have anything to do with music? "band"

---

### Post by phubert28 on 2010-05-26
But it appears I have Intel:

paul@Aragorn:~$ lspci | grep -i audio

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)

paul@Aragorn:~$

And:
paul@Aragorn:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Audio Device   ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Everyman [FREETALK Everyman], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
paul@Aragorn:~$

---

