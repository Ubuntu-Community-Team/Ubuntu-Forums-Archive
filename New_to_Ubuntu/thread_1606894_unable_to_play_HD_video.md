---
title: "unable to play HD video"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by beew on 2010-10-27
Hi,

I have an old Dell inspiron installed with Lucid, 2.2 GH CPU, 512M of Ram. It has a Nvidia Gforce 4 Ti 4200  Go AGP 8X graphic card. Video play back has been sluggish and choppy. After d setting vm.swappiness=10 and adding "tsched=0" to /etc/pulse/default.pa (following an instruction I found in the forum) video play back is mostly quite good if I disable compiz and enable openbox. However, I am still unable to play HD video (something > 480p in Youtube, for example). Downloading the video and play off line doesn't solve the problem, it is choppy and freezes often, I use VLC as my video player (Totem is much worse and I have actually uninstalled it) 

Is there any way to fix this, or basically that is as far as 512M of ram can go? I noticed also the cpu usage is close to 100% when I try to play a HD video, is this normal or is something not working right with the Nvidia card?

Thanks in advance for any advice.

---

### Post by XeonBloomfield on 2010-10-27
Minimum requirements for full HD video (in a well-known computer magazine was once a full HD movie and written requirements):

Processor: Pentium 4 2.8GHz or equivalent AMD
Memory: 1GB RAM
Graphic Card: NVIDIA GeForce 6600 128MB Video RAM or equivalent ATI

You have a fairly old computer, where a full HD movie will not run smoothly.

---

### Post by bioterror on 2010-10-27
> **XeonBloomfield said:**
> Minimum requirements for full HD video (in a well-known computer magazine was once a full HD movie and written requirements):

Processor: Pentium 4 2.8GHz or equivalent AMD
Memory: 1GB RAM
Graphic Card: NVIDIA GeForce 6600 128MB Video RAM or equivalent ATI

You have a fairly old computer, where a full HD movie will not run smoothly.

Do it like I did: buy a Networked Media Tank and stream over network. Or you can buy a cheap Asus eeebox machine with NVidia card/chip which is VDPAU capable.

---

### Post by Grenage on 2010-10-27
> **XeonBloomfield said:**
> Minimum requirements for full HD video (in a well-known computer magazine was once a full HD movie and written requirements):

Processor: Pentium 4 2.8GHz or equivalent AMD
Memory: 1GB RAM
Graphic Card: NVIDIA GeForce 6600 128MB Video RAM or equivalent ATI

You have a fairly old computer, where a full HD movie will not run smoothly.

My old Celeron laptop with onboard Intel graphics (beyond 4 years old) plays 720 BR rips flawlessly.  Are proprietary drivers available for your graphics card?  If the graphics card can't handle some load, then the 2.2Ghz CPU 'might' struggle.

---

### Post by XeonBloomfield on 2010-10-27
It happens sometimes good equipment that works well despite its age.

---

### Post by bioterror on 2010-10-27
> **Grenage said:**
> My old Celeron laptop with onboard Intel graphics (beyond 4 years old) plays 720 BR rips flawlessly.

Yeah, but 720p doesnt require much if we compare to 1080p with h264 level 4.1.

---

### Post by Grenage on 2010-10-27
> **bioterror said:**
> Yeah, but 720p doesnt require much if we compare to 1080p with h264 level 4.1.

I don't get the impression the OP is trying to run 1080p with h264 level 4.1.

---

### Post by beew on 2010-10-27
> **Grenage said:**
> My old Celeron laptop with onboard Intel graphics (beyond 4 years old) plays 720 BR rips flawlessly.  Are proprietary drivers available for your graphics card?  If the graphics card can't handle some load, then the 2.2Ghz CPU 'might' struggle.

Yes, I installed the Nvidia driver through "Hardware Drivers" in Ubuntu.  But then 720p shouldn't be that demanding, no?

No, I am not trying to  run  1080p with h264 level 4.1, I know this is a very old machine (7 years). I am fixing it up for a friend and try to learn something in the process.

---

### Post by XeonBloomfield on 2010-10-27
Simple math.

Full HD (1920x1080) needs to read and view:
1920 x 1060 = 2073600 pixels
HD 720p (1280x720) needs to read and view:
1280 x 720 = 921600 pixels

At each frame.

Here is the difference in requirements.

---

### Post by beew on 2010-10-27
> **XeonBloomfield said:**
> Simple math.

Full HD (1920x1080) needs to read and view:
1920 x 1060 = 2073600 pixels
HD 720p (1280x720) needs to read and view:
1280 x 720 = 921600 pixels

At each frame.

Here is the difference in requirements.

The screen resolution is 1680X1050

---

### Post by Grenage on 2010-10-27
> **beew said:**
> Yes, I installed the Nvidia driver through "Hardware Drivers" in Ubuntu.  But then 720p shouldn't be that demanding, no?

No, I am not trying to  run  1080p with h264 level 4.1, I know this is a very old machine (7 years). I am fixing it up for a friend and try to learn something in the process.

Well I have never tried Youtube 'HD' video, only playback through mplayer.  I would imagine that my system is borderline for smooth playback.  I suppose that if some of the load cannot be offloaded onto the GFX (did older cards support that?), then it would explain it.

---

### Post by beew on 2010-10-27
> **Grenage said:**
> Well I have never tried Youtube 'HD' video, only playback through mplayer.  I would imagine that my system is borderline for smooth playback.  I suppose that if some of the load cannot be offloaded onto the GFX (did older cards support that?), then it would explain it.

You are probably right. It is a very old machine so I don't really expect much, but just in case I may squeeze a little bit more out of it and it would be a good learning experience to try to get some additional features out of it. Except for the video part it does run quite smooth provided I disable compiz. Without Compiz it is smoother and faster than XP (which is what it was installed with before) With Compiz it is kind of equally crappy but XP is much uglier. Unfortunately I don't remember whether I had actually view 720p with XP before.

---

### Post by Grenage on 2010-10-27
All I can really suggest is that you try and cut down background processes as much as is possible, but there might not be much fat to trim.

I did once run a film via the terminal (mplayer backend, I think) on an older machine, and it improved playback.  If it is quite choppy as it is, you may simply not be able to make the difference.

---

### Post by bioterror on 2010-10-27
> **Grenage said:**
> Well I have never tried Youtube 'HD' video, only playback through mplayer.  I would imagine that my system is borderline for smooth playback.  I suppose that if some of the load cannot be offloaded onto the GFX (did older cards support that?), then it would explain it.

With even 360p my youtube connection is laggy and I usually watch those clips on parts while I'm waiting that player to buffer those videos like old good RealPlayer back in the 90's ;)

---

### Post by Grenage on 2010-10-27
> **bioterror said:**
> With even 360p my youtube connection is laggy and I usually watch those clips on parts while I'm waiting that player to buffer those videos like old good RealPlayer back in the 90's ;)

Aye, I bet! I don't stream things, because I think it would enrage me, lol.

---

### Post by XeonBloomfield on 2010-10-27
Yes, but when you are trying to play Full HD video, it`s always 1920x1080 and rescaled to your screen resolution.

---

