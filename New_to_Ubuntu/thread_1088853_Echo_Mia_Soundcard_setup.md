---
title: "Echo Mia Soundcard setup"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by deeprince on 2009-03-06
I am new to this and can't figure out how to get it to work I checked on the compatibility and it is listed as compatible.  Any help would be appreciated

---

### Post by ertrinken on 2009-12-03
Does anyone have an answer?  I am having problems with a Mia as well... too cool for linux, is it?  :confused:

I've got Echomixer seeing the card and it picks up any audio stream i play, I've got it set to route to the digi out like it should, correct channels being used etc etc etc etc etc, but nogo.

Bah, what a dearth of information available on this topic, unfortunately it may be time to jump ship back to trusty ole Windows + ASIO, guaranteed compatibility with the card. 

Please help.

---

### Post by gnottage on 2009-12-08
I'm also trying to get a Mia working under Ubuntu 9.10 (64-bit on an Intel C2D). I've used one for many years under Windows and so brought another to use under Linux. My original card isn't detected at all, but the newer one is (both work fine under WinXP), so I'm using the newer one. I have got the latest ALSA firmware source and done the configure, make make install. I get the following:
```

$ dmesg | grep Mia
[   17.968454] Echoaudio Mia 0000:04:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   17.968485] Echoaudio Mia 0000:04:01.0: firmware: requesting ea/mia_dsp.fw
[   18.057830] Echoaudio Mia 0000:04:01.0: firmware: requesting ea/loader_dsp.fw
[   18.094343] Card registered: Mia rev.0 (DSP56361) at 0xe5000000 irq 19
```

So it looks like the card is working. I can fire up the echomixer and I can get movement on the mixer bars V0 and V1 when I play an mp3 etc. However no audio comes out... I can get audio passed through the Mia through the analogue and S/PDIF inputs, and that comes out fine - just nothing sourced within Ubuntu.

What could I possibly have missed to configure or turn on?

I notice that on [another thread from a few years ago]("http://ubuntuforums.org/showpost.php?p=3173268&postcount=34") that the Mia that worked was rev.1
> [ 36.411990] PCI: Enabling device 0000:00:0b.0 (0014 -> 0016)
[ 36.412009] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
[ 36.642135] Card registered: Mia rev.1 (DSP56361) at 0xda800000 irq 19

Does anyone know if a rev.0 Mia works under Linux? Or if the output I'm seeing from dmesg is wrong???

---

### Post by gnottage on 2009-12-12
I've tried going to 32-bit 9.10 incase 64-bit was ths issue. Still I get the same result - here (and attached) is a screengrab indicating the actual issue I have:

[IMG]http://eylant.com/ubuntu-mia.png[/IMG]

It looks like audio gets to the card, but the mixer isn't taking it from the virual channels (V0 and V1) to the output (A0 and A1). Anyone have any clues? Is the audio actually getting to the card?

If I use the analogue input, I get analogue output, and here's a screengrap to show it:

[IMG]http://eylant.com/ubuntu-mia-a.png[/IMG]

---

### Post by gnottage on 2009-12-13
I can confirm that the Mia card in question works with the rest of the hardware under WinXP SP3 32-bit.

[IMG]http://eylant.com/winxp-mia.png[/IMG]

So what's up with Ubuntu Linux?

---

### Post by steve_steve on 2010-02-14
I was on the verge of getting an Echo Mia on the strength of the Echomixer app, thinking that it's presence indicates that Echo cards are supported.
In searching the forums, I see lots of audio-issue threads that are all from the original poster (no answers) so let me ask - did this problem get resolved?

~or~

Can anyone recommend a good sound card (with midi) either PCI or USB or firewire that will work with Ubuntu 9.10 relatively seamlessly?

I'm not sure if I can handle another long learning curve this week.

---

### Post by gnottage on 2010-02-14
OK, First try under Ubuntu 10.04 (Lucid) pre-release, and straight away once getting the packages installed (it needs medibuntu to get alsa-firmware) it's working! So avoid 9.10 and go with any other version...

---

### Post by gnottage on 2010-02-14
Steve - how odd that you'd ask at the same time that I posted to say that it's now working! In Lucid (10.04) it's been really easy - no compiling or configuring to do - it works which is what I'm sure you're after. Needed to install a few packages (medibuntu and alsa stuff as well as the mixer). But it's been plain sailing for me (although my graphics card hasn't been as smooth under 10.04, but it does work). Find the Alpha2 release of Lucid [_here_](http://www.ubuntu.com/testing/lucid/alpha2)

---

### Post by steve_steve on 2010-02-14
I'm a little leery of an alpha, but it might be ok if it doesn't mess with existing kernels.  I might just wait until April 29 (or thereabouts) for the release version.

Have you done any audio recoding?  If so, have you had any latency problems?

---

### Post by gnottage on 2010-02-15
I haven't got round to any recording yet. I don't think the ALSA driver has changed, so is stable. I'm having some other graphics (nVidea and X) issues with Lucid, so will probably wait for the release before a clean reinstall and then exploring more audio.

---

