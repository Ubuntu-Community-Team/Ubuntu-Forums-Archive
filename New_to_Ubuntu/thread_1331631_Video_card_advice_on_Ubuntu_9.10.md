---
title: "Video card advice on Ubuntu 9.10"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by renan.fs on 2009-11-19
Hello, I´m a new user of Linux, but advanced USER of windows and got completely amazed by the performance, security, community, simplicity and personalization of Ubuntu 9.10. I am actually ready to wipe my windows partition. The thing is, I got a new pc and the only thing that is missing is a video card. I don’t like games but love films and series. 
Can anyone help me to choose a pci-e Video Card with no issues of compatibility on Karmic, good enough to play HD media? Searching the forum I realized that Ati is not a good choice for that, is it correct?
Thank you very much.

---

### Post by danill2008 on 2009-11-19
Have tried searching for drivers? It can be found under : System > Administration > Hardware Drivers. Do a refresh and see what it comes up with...

---

### Post by Redmage913 on 2009-11-19
It sounds like what you're looking for is not current drivers for a device, but instead you just want to know which cards would be best for Ubuntu.

I cannot answer your question myself, but I did want to focus your question a bit.  The prior response didn't seem to quite answer what you were looking for.

---

### Post by danill2008 on 2009-11-19
> **renan.fs said:**
> Hello, I´m a new user of Linux, but advanced USER of windows and got completely amazed by the performance, security, community, simplicity and personalization of Ubuntu 9.10. I am actually ready to wipe my windows partition. The thing is, I got a new pc and the only thing that is missing is a video card. I don’t like games but love films and series. 
Can anyone help me to choose a pci-e Video Card with no issues of compatibility on Karmic, good enough to play HD media? Searching the forum I realized that Ati is not a good choice for that, is it correct?
Thank you very much.

> **Redmage913 said:**
> It sounds like what you're looking for is not current drivers for a device, but instead you just want to know which cards would be best for Ubuntu.

I cannot answer your question myself, but I did want to focus your question a bit.  The prior response didn't seem to quite answer what you were looking for.

Sorry I misread the post...

---

### Post by WinterWeaver on 2009-11-19
I tend to go for NVidia cards... but other may have different advice.

---

### Post by braete on 2009-11-19
it would help if you would tell how much are you ready to pay for a video card and maybe a preferred online shop

---

### Post by renan.fs on 2009-11-20
> **braete said:**
> it would help if you would tell how much are you ready to pay for a video card and maybe a preferred online shop

That´s true my friend. As I am going to use the computer to play hd media, not games, I think that US$ 150 is Ok. I found two models that I liked:
ATI Radeon HD 4670 512MB GDDR3 – delivers audio and video through HDMI.
Geforce 8500 GT 1gb DDR2 - really good cost here in Brazil

What do you guys think ? 
Thanks everyone for the answers.

---

### Post by ST3ALTHPSYCH0 on 2009-11-20
I've had no problems running my 42" LCD with the HDMI on my onboard ATI HD3300, but I've not run the sound through it (I've got sound running through my stereo receiver), so I can't attest to how well that works.

---

### Post by braete on 2009-11-20
i think you can get more that that for 150$ as there are a lot of nvidia 9600GT cards for less than 150$. i even saw hd4850 cards for ~150$.

but you said "no games" so, if i where to chose from those 2 cards i would go for the 4670. it's more expensive but imo it's worth it.

---

### Post by jbrown96 on 2009-11-20
The Nvidia drivers are significantly better than ATI. Intel is also good, but I don't think you would have the same performance. For HD video playback, 9400GT is an awesome choice. It can decode most HD formats on the card. For a home theater, they make a fanless version. They are only $30-$40 on newegg.com. 

I have an ATI HD3200 in my htpc and it's really disappointing. Video tears really bad, and the system slows to a crawl if I have to open a menu while watching a video. The drivers do seem to be getting better, but ATI is probably 8-12 months behind Nvidia with Linux drivers. There's no indication that they are closing the gap either. Nvidia just released new drivers a week or two ago, and they are a great improvement. 

For HD video playback, there are three technologies for doing the decoding on the card: VDPAU from Nvidia -- this was the first decoding supported on Linux and is the most featureful, best supported, and most stable; VA-API from Intel -- I don't know much about this, but I don't think Intel sells much capable hardware; XvBA from ATI -- this was only released a couple weeks ago and isn't mature.

---

### Post by Lvcoyote on 2009-11-20
I would agree that based on driver quality alone, nvidia would be a good choice.  Past that the only suggestion is to get as good a card as the budget allows.

---

### Post by renan.fs on 2009-11-21
> **jbrown96 said:**
> The Nvidia drivers are significantly better than ATI. Intel is also good, but I don't think you would have the same performance. For HD video playback, 9400GT is an awesome choice. It can decode most HD formats on the card. For a home theater, they make a fanless version. They are only $30-$40 on newegg.com. 

I have an ATI HD3200 in my htpc and it's really disappointing. Video tears really bad, and the system slows to a crawl if I have to open a menu while watching a video. The drivers do seem to be getting better, but ATI is probably 8-12 months behind Nvidia with Linux drivers. There's no indication that they are closing the gap either. Nvidia just released new drivers a week or two ago, and they are a great improvement. 

For HD video playback, there are three technologies for doing the decoding on the card: VDPAU from Nvidia -- this was the first decoding supported on Linux and is the most featureful, best supported, and most stable; VA-API from Intel -- I don't know much about this, but I don't think Intel sells much capable hardware; XvBA from ATI -- this was only released a couple weeks ago and isn't mature.

Hi, thanks ! One more question I was reading the nvidia website, and realized that only few card are compatible with Pure Video HD. Is this technology worth it or is just a marketing argument ?

---

### Post by 3rdalbum on 2009-11-21
> **renan.fs said:**
> Hi, thanks ! One more question I was reading the nvidia website, and realized that only few card are compatible with Pure Video HD. Is this technology worth it or is just a marketing argument ?

Pure Video HD is the marketing term for what we on Linux and Unix call "VDPAU". (Video Decode and Presentation API for Unix). HD video can be quite processor-intensive to decode and render with a CPU; what Nvidia has is a chip on their graphics cards that can decode and render certain types of video files without loading up your CPU too much.

It does definitely make a difference. You get smoother motion video and lower CPU utilization when playing back high definition content (as long as your player supports VDPAU - Mplayer does). Also I believe all current Nvidia graphics cards should support it, even the cheapest ones.

ATI's cards have a similar feature, but **it doesn't work on Linux yet.**

VDPAU works with these codecs:

1. H.264
2. MPEG 1 and 2
3. VC1
4. WMV

Not coincidentally, Blu-ray discs are H.264, MPEG 2 or VC1. In short, any Nvidia card will be miles better than any ATI card on Linux if you like to play videos.

---

### Post by gordintoronto on 2009-11-29
> **renan.fs said:**
> Hi, thanks ! One more question I was reading the nvidia website, and realized that only few card are compatible with Pure Video HD. Is this technology worth it or is just a marketing argument ?

A 9400GT card will work just fine for playing videos, and should cost at least $100 less than your budget.

---

### Post by cascade9 on 2009-11-29
For just watching HD, you just want an nVidia card supporting VDPAU

> **jbrown96 said:**
> VDPAU from Nvidia -- this was the first decoding supported on Linux and is the most featureful, best supported, and most stable 

Complete list of supported cards here-
[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

If you not going to be playing games much, if at all, I would get a 8400GS or 9400GT.

---

