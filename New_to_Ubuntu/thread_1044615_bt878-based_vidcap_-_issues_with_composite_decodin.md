---
title: "bt878-based vidcap - issues with composite decoding (tv standard PAL-I)"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Slippy Lane on 2009-01-19
The issue is that displaying the composite input from either of my capture cards in any of the PAL standards results in a tiled, scrolling, lined, flickering mess on the screen that looks like it's either encrypted, or is decoded using entirely the wrong standard. I've tried switching cables and sources, checked everything ok thru tv composite in before plugging in to capture card, tried every TV standard and nothing seems to work.

The closest to a watchable picture comes with PAL-NC in tvtime, but that's black and white, and still flickers. I've tried altering every other setting in TVtime, repeated all the processes with both capture cards, both sets of cables and both sources - exactly the same results every time, so it MUST be something I'm missing in the configuration.

I have the following:

One PC running Intrepid
One ATI graphics card - proprietary drivers
Two different bt878-based video capture cards (I'm not using them both at the same time, have been swapping them in and out to test fault repetition)

One copy of tvtime and one of xawtv
Compiz disabled due to issues with tvtime not displaying anything at all when it's running.

If anyone can shed any light on this for me, I will fall at your feet in gratitude.

---

### Post by NoHell on 2009-08-02
Thought I would reply to this even tho its an old post.

I had the same problem and its taken me awhile to solve it, but i finally found the solution today.

Basically in one link. [http://bruury.wordpress.com/2008/11/03/pixelview-playtv-pro-bt878-fm-in-ubuntu/](http://bruury.wordpress.com/2008/11/03/pixelview-playtv-pro-bt878-fm-in-ubuntu/)

My card was a generic Bt878a, and after a bit of research I found that the closest card that was in the Bttv supported list was euresys Picolo. (bttv card 97).

I'm a Linux newbie, but from my understanding the problem was that the card was set to NTSC at hardware/driver level and I needed PAL.

Here is a copy of the file I created and put in Modprob.d.
```
# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=97 tuner=30 radio=1 pll=1 adc_crush=0
```the "pll=1" is the part that sets the standard to PAL. And the "card=97" is part that sets the Bttv driver.

Hope this helps and saves you some hair loss, as i was definitely pulling my hair out trying to get it working, but I learnt alot in the process.

P.S I'm on Ubuntu  9.04
P.S.S I forgot to add that some of the options in the code above can be removed, for a cap only card you don't need "radio=" etc.

---

### Post by frenchn00b on 2009-12-06
> **NoHell said:**
> Thought I would reply to this even tho its an old post.

I had the same problem and its taken me awhile to solve it, but i finally found the solution today.

Basically in one link. [http://bruury.wordpress.com/2008/11/03/pixelview-playtv-pro-bt878-fm-in-ubuntu/](http://bruury.wordpress.com/2008/11/03/pixelview-playtv-pro-bt878-fm-in-ubuntu/)

My card was a generic Bt878a, and after a bit of research I found that the closest card that was in the Bttv supported list was euresys Picolo. (bttv card 97).

I'm a Linux newbie, but from my understanding the problem was that the card was set to NTSC at hardware/driver level and I needed PAL.

Here is a copy of the file I created and put in Modprob.d.
```
# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=97 tuner=30 radio=1 pll=1 adc_crush=0
```the "pll=1" is the part that sets the standard to PAL. And the "card=97" is part that sets the Bttv driver.

Hope this helps and saves you some hair loss, as i was definitely pulling my hair out trying to get it working, but I learnt alot in the process.

P.S I'm on Ubuntu  9.04
P.S.S I forgot to add that some of the options in the code above can be removed, for a cap only card you don't need "radio=" etc.

wow 
thanks 
could you post the hardware you have ?
the refereence of the card? I havent much idea what is my card instead ofcopying card=97 tuner=30

---

### Post by Fitch on 2010-01-10
Hi there,
I've been battling with my configuration for a couple of months now,
I have a PCTV Rave card which although gives a perfect picture, only gives out a constant hiss for the sound.
It autodetects card=39 and tuner=33

so my bttv file is: 
# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=39 tuner=33 radio=0 pll=1 adc_crush=0

but still all I get is Hissing Sid (British Gas advert circa 1970's).

[   42.493666] bttv: driver version 0.9.18 loaded
[   42.493671] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   42.493733] bttv: Bt8xx card found (0).
[   42.493749] bttv0: Bt878 (rev 17) at 0000:04:08.0, irq: 17, latency: 16, mmio: 0xfdaff000
[   42.494609] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   42.494614] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,insmod option]
[   42.494618] IRQ 17/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   42.494667] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   42.494710] bt878 #0 [sw]: Test OK
[   42.499461] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   42.500213] bttv0: pinnacle/mt: id=1 info="PAL / mono" radio=no
[   42.500217] bttv0: tuner type=33
[   42.512129] bttv0: audio absent, no audio device found!
[   42.519165] tuner 2-0043: chip found @ 0x86 (bt878 #0 [sw])
[   42.519253] tda9887 2-0043: creating new instance
[   42.519255] tda9887 2-0043: tda988[5/6/7] found
[   42.522833] Chip ID is not zero. It is not a TEA5767
[   42.522922] tuner 2-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   42.525992] mt20xx 2-0060: microtune: companycode=3cbf part=42 rev=22
[   42.527331] mt20xx 2-0060: microtune MT2050 found, OK
[   42.529330] bttv0: registered device video0
[   42.529352] bttv0: registered device vbi0
[   42.529373] bttv0: PLL: 28636363 => 35468950 .
[   42.531282] bttv0: PLL: 28636363 => 35468950 .
[   42.532438] bttv0: PLL: 28636363 => 35468950 . ok
[   42.547799]  ok
[   42.552707]  ok

I am now bald.

---

### Post by frenchn00b on 2010-01-10
> **Fitch said:**
> Hi there,
I've been battling with my configuration for a couple of months now,
I have a PCTV Rave card which although gives a perfect picture, only gives out a constant hiss for the sound.
It autodetects card=39 and tuner=33

so my bttv file is: 
# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=39 tuner=33 radio=0 pll=1 adc_crush=0

but still all I get is Hissing Sid (British Gas advert circa 1970's).

[   42.493666] bttv: driver version 0.9.18 loaded
[   42.493671] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   42.493733] bttv: Bt8xx card found (0).
[   42.493749] bttv0: Bt878 (rev 17) at 0000:04:08.0, irq: 17, latency: 16, mmio: 0xfdaff000
[   42.494609] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   42.494614] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,insmod option]
[   42.494618] IRQ 17/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   42.494667] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   42.494710] bt878 #0 [sw]: Test OK
[   42.499461] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   42.500213] bttv0: pinnacle/mt: id=1 info="PAL / mono" radio=no
[   42.500217] bttv0: tuner type=33
[   42.512129] bttv0: audio absent, no audio device found!
[   42.519165] tuner 2-0043: chip found @ 0x86 (bt878 #0 [sw])
[   42.519253] tda9887 2-0043: creating new instance
[   42.519255] tda9887 2-0043: tda988[5/6/7] found
[   42.522833] Chip ID is not zero. It is not a TEA5767
[   42.522922] tuner 2-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   42.525992] mt20xx 2-0060: microtune: companycode=3cbf part=42 rev=22
[   42.527331] mt20xx 2-0060: microtune MT2050 found, OK
[   42.529330] bttv0: registered device video0
[   42.529352] bttv0: registered device vbi0
[   42.529373] bttv0: PLL: 28636363 => 35468950 .
[   42.531282] bttv0: PLL: 28636363 => 35468950 .
[   42.532438] bttv0: PLL: 28636363 => 35468950 . ok
[   42.547799]  ok
[   42.552707]  ok

I am now bald.

thank you !

My tv is now fully working with the following : 
/etc/rc2.d/S99startbttv
```
rmmod  bttv ; rmmod tuner ; modprobe bttv card=35 tuner=7
```

---

### Post by Fitch on 2010-01-13
That's nice, but I don't have a /etc/rc2.d/S99startbttv

---

### Post by frenchn00b on 2010-01-13
> **Fitch said:**
> That's nice, but I don't have a /etc/rc2.d/S99startbttv

Hi Fitch 

what do you mean? Is your hardware working, yes I guess?

---

### Post by Fitch on 2010-01-13
No, I mean I don't have such a file as/etc/rc2.d/S99startbttv, so can't try it.
I still have nothing but hiss, perfect picture though...

---

### Post by Fitch on 2010-01-23
I finally realised what you what you meant, but it didn't work anyway. thanks for the idea though.
The problem as I see it is that the tuner automatically defaults to PAL-BGHN, the sound carrier being 5.5MHz.
PAL I however, is at 6.0MHz, hence the constant hiss.
I can find nothing at all on any forum to say how I can change the tuner's IF to 6.0MHz.  All I can see is script files and make files and kernel files.. you get the idea.  I just wouldn't have a clue what I was doing if I went down that route.

---

