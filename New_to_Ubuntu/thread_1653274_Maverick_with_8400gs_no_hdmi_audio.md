---
title: "Maverick with 8400gs no hdmi audio"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by NoBrightIdeas on 2010-12-26
Still new Ubuntu user with limited pc skills seeks huge monitor with ease of use.

I got a vizio flat screen for christmas. I thought, sweet, new monitor! Well, after hooking everything up, I have video, and it's beautiful. I have audio, but only through my headphones. I have read through so many posts, and yet my problem still remains unsolved. I tried getting into bios, but there isn't anything about enabling hdmi audio there, I've tried pulseaudio mixer and alsamixer, and there isn't even an option to enable hdmi. I just upgraded from 10.04 to 10.10 and was hoping for the best. I'm not even sure if this is coming out coherent, as my eyes and brain are spent from searching for an answer. If someone could even just point me in the right direction, that would be great. Thanks in advance to whomever responds.

---

### Post by IchBinWamphyri on 2011-02-11
Also having same problem:
Maverick 10.10
Nvidia 8400GS
Hdmi cable to tv 
vga to acer monitor
only analog sound through cpu speakers cannot get sound via hdmi on tv

---

### Post by mikewhatever on 2011-02-11
Having searched for '8400gs hdmi audio', it looks like the problem is not Ubuntu or nvidia driver related. People say there should be something connecting the sound card to the video card.
[http://www.hardwareanalysis.com/content/topic/76101/](http://www.hardwareanalysis.com/content/topic/76101/)

---

### Post by uRock on 2011-02-11
> **mikewhatever said:**
> Having searched for '8400gs hdmi audio', it looks like the problem is not Ubuntu or nvidia driver related. People say there should be something connecting the sound card to the video card.
[http://www.hardwareanalysis.com/content/topic/76101/](http://www.hardwareanalysis.com/content/topic/76101/)
Great find. I hope it works.

---

### Post by Hedgehog1 on 2011-02-11
Getting Audio working on an NVidia card over HDMI is not as hard as it used to be.

The various posts already out there were based on how things were on Ubuntu 10.10 at the time they were posted.  Things have improved...

I will do my best to tell you what worked for me about 3 weeks ago when I setup my Ubuntu system with an NVidia card with an HDMI out to my 55" TV.

Step one: If you have not already, load the NVidia drivers for Linux from the manufacturer site.

Step two: in the terminal, type:

```
alsamixer
```

You will see a character based audio mixer that will have a variable number of channels depending on how many channels your analog audio card has (mine has 8 analog channels).

Press F6 and select the HDA NVidiva card.  Hit enter.

You will see S/PDIF channels (I have four, you may have more or less).  You need to un-mute them all,  change the value of every S/PDIF channel to '00' ('MM' means muted')

To change the level from Muted to '00', press the letter 'M' on your keyboard.  Arrow right and left as needed. Once you have un-muted all the S/PDIF channels, press [escape] to exit the mixer.

Step Three (final step!): Menu to Preference >> Sound >> Output and select 'HDA Nvidia' (You may see two HDA NVidia choices, for me the 'HDA NVidia' one works. Try both until you get sound from Rhythm Box.

I think this is all that is needed for a up-to-date Ubuntu 10.10 install.

We will know soon...

:KS

---

### Post by Hedgehog1 on 2011-02-11
> **mikewhatever said:**
> Having searched for '8400gs hdmi audio', it looks like the problem is not Ubuntu or nvidia driver related. People say there should be something connecting the sound card to the video card.
[http://www.hardwareanalysis.com/content/topic/76101/](http://www.hardwareanalysis.com/content/topic/76101/)

This extra connection was not needed in my case.  Also the Win7 side of my dual boot had sound right away via HDMI.

The NVidia drivers for Linux concentrate on awesome x-windows support, and they just did not get around to the auto-setup of HDMI audio out for Linux.

I consider it a small price to pay for supporting compiz graphic animations.  I have yet to show them any anybody who wasn't speechless at how amazing they look.

When they finally can speak, they say: 'Show me that again!'.

:KS

---

### Post by mikewhatever on 2011-02-12
> **Hedgehog1 said:**
> This extra connection was not needed in my case.  Also the Win7 side of my dual boot had sound right away via HDMI.

The NVidia drivers for Linux concentrate on awesome x-windows support, and they just did not get around to the auto-setup of HDMI audio out for Linux.

I consider it a small price to pay for supporting compiz graphic animations.  I have yet to show them any anybody who wasn't speechless at how amazing they look.

When they finally can speak, they say: 'Show me that again!'.

:KS

Yours is a much simpler solution, hope it works for everyone here.
As for compiz, it got me curious for about 15 minutes back in 2007, wasn't speechless one second though. After that, I got annoyed and turned it off.:P

---

### Post by Hedgehog1 on 2011-02-12
Honestly - if you don't have a powerful video card, then Compiz is a let down.

I built this system in January for  Ubuntu 10.10 and Win 7 dual boot.  The powerful graphic card was for GPU acceleration of Photoshop.

I now spend 90% of my time on the Ubuntu side.  So I have all this horsepower doing 'wobbly windows' and such.

You know what really gets everybody?  The water drop effect.  Totally useless. Totally cool.

:KS

---

### Post by mikewhatever on 2011-02-12
The people you talk to are easily amused, but to each his or her own.

---

### Post by Hedgehog1 on 2011-02-12
I suppose it is all the frame of reference the observer comes from.

Case in point:  Before the days on Non-Linear editing, I had an A/B roll video tape editing bay with a Commodore Amiga for graphics and effects.  It was crude by todays standards - but looked good for its time.

My wife used the edit bay as well, and kept asking why the windows computer we had could not do that (Mac's didn't do video in those days, either).

At a trade show she joined me at, a person demoed some new 'whizbang' video overlay card running on a 286 system with Windows 3.1.  My wife listened, asked questions, and then explained that her video processing computer already did this, did it better, and had been doing it for many years already.  She had no idea the limits of other hardware.  In the end, the presenter was in tears.

I made my wife swear not to tell people about the Amiga and it's advanced video processing for the rest of the trade show.  I explained that no other hardware did what it did (and hence why we used it in the edit bay).  But she asked me all weekend why the much more expensive hardware being shown didn't do 1/2 of what we already did on a cheap Amiga.

Folks assume that a 'computer doesn't do that'.  Well, Windows doesn't do fancy & fun graphics for the shear joy of it.  Mac does some.

Most folks buy cars because of the body style, color and wheels, right?  Do any of these things make the vehicle operate better?  Not typically.  But the look affects them emotionally.

Compiz and pretty effects are like that.  Music, too.  Not logical, but very powerful.

When was the last time you had 'fun' with an OS?  For us, about 30 seconds ago.  On my Windows PC at work?  Not often.

Apple sells the 'fun' in OSX (and it does work).

Ubuntu will be 'selling' the visual fun in 11.4.

Anyway - that was WAY off topic.  I wonder if the OP got HDMI sound working yet?

---

### Post by uRock on 2011-02-12
Please keep the thread on topic fellas.

Thanks,
uRock

---

### Post by Hedgehog1 on 2011-02-12
Hey there [SIZE="2"]NoBrightIdeas[/SIZE] an [SIZE="2"]IchBinWamphyri[/SIZE]

Were you able to try my steps on your NVidia/HDMI systems:

> 
Step one: If you have not already, load the NVidia drivers for Linux from the manufacturer site.

Step two: in the terminal, type:

Code:
alsamixer
You will see a character based audio mixer that will have a variable number of channels depending on how many channels your analog audio card has (mine has 8 analog channels).

Press F6 and select the HDA NVidiva card. Hit enter.

You will see S/PDIF channels (I have four, you may have more or less). You need to un-mute them all, change the value of every S/PDIF channel to '00' ('MM' means muted')

To change the level from Muted to '00', press the letter 'M' on your keyboard. Arrow right and left as needed. Once you have un-muted all the S/PDIF channels, press [escape] to exit the mixer.

Step Three (final step!): Menu to Preference >> Sound >> Output and select 'HDA Nvidia' (You may see two HDA NVidia choices, for me the 'HDA NVidia' one works. Try both until you get sound from Rhythm Box.

I think this is all that is needed for a up-to-date Ubuntu 10.10 install.


Please let us know if this did the job for you.  I have hopes of this simpler set of steps being the 'newer solution' with up-to-date Ubuntu 10.10 installs.

Thanks!

---

### Post by ScottSatkin on 2011-02-27
I am having the same issue.  However, I cannot get alsa to even list the nvidia card as an audio output option:

```
sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/scott not ours.
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have tried installing the latest alsa and nvidia drivers which has not helped.  Any advice would be greatly appreciated!

---

### Post by uRock on 2011-02-27
Did you try plugging in the cable mentioned in post #3?

---

### Post by ScottSatkin on 2011-02-27
> **uRock said:**
> Did you try plugging in the cable mentioned in post #3?

Yes.  It is connected to the SPDIF output on my motherboard.

---

