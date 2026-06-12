---
title: "Headphones Problem"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by elysianfields44 on 2009-07-09
Hello all, 

I've been trying to get my headphones to work on Hardy, but regardless of what I do the sound keeps coming out of the front speakers of my laptop (i.e. no sound in the headphones). Of course, they work on Windows XP (on the same machine). 

In Volume Control, I have checked "headphones" under "switches", but to no avail. Also, under Volume Control > File > Change Device, there are a number of devices to choose from. The currently selected one is "0: HDA Intel (Alsa mixer)". (Since my sound card is HDA Intel).

In Alsamixer, I can see that the value for headphones seems to be disabled (it appears to be zero and doesn't change when I try to increase it). I'm providing a screenshot, as I don't think I'm explaining this very well. 

Here's the output of some commands that might be helpful.

```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```



```
lspci -v | less | grep Audio

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Subsystem: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
```


It's almost as if it doesn't recognize that the headphones are plugged in. Could anyone help me out? Thanks.

---

### Post by pytheas22 on 2009-07-10
Unless I'm misreading, it looks like you actually have two sound devices--one from Intel and another from ATI.  If you go to System>Preferences>Sound, you should be able to choose which of the cards to use for which tasks.  I would try experimenting with this.

If one of the sound devices is built into your motherboard, your BIOS may also have an option for disabling it.  Alternatively, if this is a desktop computer and one of the sound cards is a PCI device, you could physically remove it.  Does disabling or removing one of the sound cards solve the problem?

Also, do you only have one set of sound ports on this system?  I would expect there to be two sets, and maybe you have your headphone plugged into the wrong one.

---

### Post by LowSky on 2009-07-10
pytheas22, the ATI card your seeing is actually a Video card that supports HDMI, it has nothing to do with this problem.

elysianfields44, I'm not entirely sure of a fix but what version of Ubuntu are you using, possibly an upgrade could easily fix it, but you can lower the front speaker sound while wearing headphones and that should turn the laptop speakers off in the mean time

---

### Post by elysianfields44 on 2009-07-10
> **LowSky said:**
> pytheas22, the ATI card your seeing is actually a Video card that supports HDMI, it has nothing to do with this problem.

Correct, the ATI card is a video card, I realized that after I posted.


> elysianfields44, I'm not entirely sure of a fix but what version of Ubuntu are you using, possibly an upgrade could easily fix it, but you can lower the front speaker sound while wearing headphones and that should turn the laptop speakers off in the mean time

I have 8.04, I wasn't planning on upgrading until the next LTS.

I'm not sure what you mean by turning the front speakers sound off - since there's no sound in the headphones at all, ie. the sound is only coming from the laptop speakers.

Thanks for your suggestions.

---

### Post by elysianfields44 on 2009-07-10
> **pytheas22 said:**
> 
Also, do you only have one set of sound ports on this system?  I would expect there to be two sets, and maybe you have your headphone plugged into the wrong one.

I already tried plugging them in both, it made no difference.

Thanks for the reply anyway.

---

### Post by pytheas22 on 2009-07-11
Thanks for the correction on the second video card--I didn't realize video cards can also do sound (interesting), but I understand now.

You might want to try burning a live CD of Ubuntu 9.04 just to see if your sound problems are solved there; if so, you can think about upgrading.

It might also help to compile alsa from source using a later version than the one available in 8.04.  A quick google for "compile alsa ubuntu" turned up [this page]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html"), with a script that looks like it should work.  Just replace these lines:
```

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2
```

with:
```

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.**19**.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.**19**.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.**19**.tar.bz2
```

so you're getting the most recent source code.

---

### Post by elysianfields44 on 2009-07-13
pytheas22, thank you for the ideas!

I have a 9.04 live cd handy, so I am typing this from Jaunty. Unfortunately the sound is still coming from the laptop speakers not from the headphones. Oh well-- it was worth a try.

As for installing Alsa from source - I downloaded version 1.0.20 (what seems to be the latest stable release) from [here]("http://www.alsa-project.org/main/index.php/Download") and I ran a bash script like the one you suggested. Alas, there seems to be no difference.

---

### Post by pytheas22 on 2009-07-13
elysianfields44: I'm sorry to hear neither of those ideas helped.  Unfortunately, I'm kind of out of other ideas.  The only other thing I can think to do is google around to see if you can find other users having the same problem on Ubuntu with your hardware.  You already know it's Intel 82801H audio, so that's a good search term.  You might also want to run 'lspci -nn' and look for the line pertaining to your sound card; it will contain an eight-character string in the form XXXX:XXXX.  This is a unique identifier for your particular model of sound card and can also be a good search term.

It's also possible that playing around with audio-device options in your BIOS might change something...unlikely, but worth a try.

---

