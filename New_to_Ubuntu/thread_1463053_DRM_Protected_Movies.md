---
title: "DRM Protected Movies"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by OneLine on 2010-04-26
Hi, I have 14 DRM protected movies (wmv format) on my external hard drive, total cost was shy of £70, how can I watch them on Ubuntu. Thank You.

---

### Post by HarrisonNapper on 2010-04-26
Depends. If they still have the original dvd encoding, you may need to enable the medibuntu repositories and install libdvdread4 and/or libdvdcss3 (if it gives you that option). If they are not encoded, there's probably not an issue.

[http://www.medibuntu.org](http://www.medibuntu.org) for instructions on adding the repos

then add (if they exist): libdvdread4, libdvdcss3, and w32codecs

Also, while you're at it, might want to download VLC; it has been the best by far for me, especially for restricted codecs.

Edit: Also, if you mean you own these illegally, we do not support piracy

---

### Post by OneLine on 2010-04-26
> **HarrisonNapper said:**
> Depends. If they still have the original dvd encoding, you may need to enable the medibuntu repositories and install libdvdread4 and/or libdvdcss3 (if it gives you that option). If they are not encoded, there's probably not an issue.

[http://www.medibuntu.org](http://www.medibuntu.org) for instructions on adding the repos

then add (if they exist): libdvdread4, libdvdcss3, and w32codecs

Also, while you're at it, might want to download VLC; it has been the best by far for me, especially for restricted codecs.

Thank You, I will look into that.

> **HarrisonNapper said:**
> Edit: Also, if you mean you own these illegally, we do not support piracy

Illegal? no, I purchased the movies online, as they were buy to download they are DRM protected, I paid £69.74.

---

### Post by HarrisonNapper on 2010-04-26
No worries, just wanted to make sure you got the disclaimer :)

Cheers.

---

### Post by Chronon on 2010-04-26
I doubt those packages will help.  They are intended to, variously, decrypt DVDs, read them, and decode unencrypted media streams.  I am not aware of any package that removes DRM from protected-WMV.

---

### Post by LowSky on 2010-04-26
Sorry OneLine but to watch those files you are probably stuck with Windows. the same applies to files purchased through Apple's iTunes, and Amazon's video player.

Your only option is to rip the file into an another spported file so they can be enjoyed on any operating system.

If you wan't to blame anyone, send your love toward the MPAA.

---

### Post by HarrisonNapper on 2010-04-26
> **Chronon said:**
> I doubt those packages will help.  They are intended to, variously, decrypt DVDs, read them, and decode unencrypted media streams.  I am not aware of any package that removes DRM from protected-WMV.

Right you are on dvd encoding. Just adding extra for good measure. However, the w32codecs will add video codecs to ffmpeg's libraries for decoding.

As for what LowSky said, that may be right, I've never tried to play a wmv file. The only files I have that are not ogg/ogv are some wma files which I converted from mpc, so you may be able to re-encode the files using ffmpeg to another file format. I assume if wma works, wmv could work in theory. And LowSky is right in that it will not remove the DRM.

I would say at least install w32codecs, but probably install the *dvd* packages for good measure, then try to play them in VLC. If they won't play, you may try converting the files with ffmpeg.

---

### Post by Chronon on 2010-04-26
The problem here isn't decoding audio/video streams, it's removing encryption added to the streams (the DRM).  We don't have packages (that I am aware of) that handle this process, so protected WMV and iTunes's M4P, among others, are off-limits to us in Ubuntu, as far as I have seen. 

(Legally, such packages would be off-limits to me as a citizen of USA, anyway.)

---

### Post by HarrisonNapper on 2010-04-26
It is a testament to what the introduction of DRM has done to my music-listening habits that the obvious part of this equation you just talked about did not occur to me at all. I was assuming the DRM was something that just prevented the file from being copied (like a header in the file) rather than encryption of the contents entirely.

My DRM experiences are limited to someone asking how to listen to their DRM music and so far those total 2. :)

---

### Post by barbirolli on 2010-04-27
I am afraid I think Chronon is right. I have not so far found a method of cracking drm encryption. Trying FFMPEG only produces 4 seconds of garbled video and no sound. Quite why these people think they should be able to sell you video, then dictate what hardware and software combinations you can use to watch it is beyond me. Isn't this a restraint on trade and therefore illegal (in EU, anyway)?

---

### Post by andrew.46 on 2010-04-27
Hi barbirolli,

> **barbirolli said:**
> Quite why these people think they should be able to sell you video, then dictate what hardware and software combinations you can use to watch it is beyond me.

I agree completely. It makes more sense when you realise that when people talk of 'digital rights management' they are leaving consumers out of the equation completely, *our* rights are not being considered...

Andrew

---

### Post by Grenage on 2010-04-27
Yeah, but people know that it's DRM encrypted before they buy it.  Society is its own worst enemy.

---

### Post by Chronon on 2010-04-27
> **andrew.46 said:**
> Hi barbirolli,



I agree completely. It makes more sense when you realise that when people talk of 'digital rights management' they are leaving consumers out of the equation completely, *our* rights are not being considered...

Andrew
I know a group of people who insist on referring to DRM as "digital restrictions management".  It really does seem more apt in every way.

---

### Post by HarrisonNapper on 2010-04-29
If anyone was around for the Windows Media Player issues when it upgraded to 8 or 9 (don't remember the version), you may remember having some of your paid-for music disappear or stop working in the only form you had it at the time. For people who view copying as theft, you would think they might view theft as theft.

---

### Post by areteichi on 2011-05-14
> **Chronon said:**
> The problem here isn't decoding audio/video streams, it's removing encryption added to the streams (the DRM).  We don't have packages (that I am aware of) that handle this process, so protected WMV and iTunes's M4P, among others, are off-limits to us in Ubuntu, as far as I have seen. 

(Legally, such packages would be off-limits to me as a citizen of USA, anyway.)

Does anyone know if there is a reliable program that can remove DRM encryption under Windows? I do have Windows installed on VirtualBox so I would be more than willing to try something out if there is a way. I did find some [names of programs]("http://undrm.info/remove-DRM-protection/") but I'm not sure any of them can be trusted. I guess there is are lossless and lossy methods? (I prefer lossless of course.)

I'm interested in this simply because I don't want to rely on virtual Windows to watch DRM restricted videos. So I just want to convert my videos for my own personal use :P

---

### Post by PhillyPhil on 2011-05-14
> **HarrisonNapper said:**
>  Edit: Also, if you mean you own these illegally, we do not support piracy

''We''? Some of ''us'' do support unauthorised copies

Perhaps you meant to say UF does not permit support of unauthorised copies here.

---

### Post by wildmanne39 on 2011-05-14
Hi, so the media and video how to guide will not fix his problem? I run windows when I have to in virtualbox but I do not think it will play movies well even if you get the software because it tends to have problems with audio when it comes to movies at least when I used it for netflix.):P

---

