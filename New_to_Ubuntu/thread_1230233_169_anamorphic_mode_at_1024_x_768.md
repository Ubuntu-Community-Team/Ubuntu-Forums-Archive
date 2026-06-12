---
title: "16:9 anamorphic mode at 1024 x 768?"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by spaceprobe on 2009-08-03
Hi all,
I have a Linux Ubuntu machine connected to a large plasma screen TV because it's used to play a looping slideshow of our portfolio of past work.

The native resolution of the screen is 1024 x 768, 16:9 pic ratio. I cant find a way to get Ubunto to drive the screen in this configuration. The closest I can see is 1360 x 768 (this is the only 16:9 listed).

the screen displays the 1360 image VERY badly because it has to drop more than 300 columns across the width of the image. 

Is there a way I can force Ubuntu to drive the monitor in a non-square pixel (16:9 anamorphic) mode at 1024 x 768?

Any help greatly appreciated: Desperate to get this right because I persuaded everyone here we should go the Linux route for this project and it's been fraught with difficulty so far!

Cheers,
K

---

### Post by CatKiller on 2009-08-03
> **spaceprobe said:**
>  The native resolution of the screen is 1024 x 768, 16:9 pic ratio. 

These can't both be true.

---

### Post by Mark Phelps on 2009-08-03
> **spaceprobe said:**
> The native resolution of the screen is 1024 x 768, 16:9 pic ratio. I cant find a way to get Ubunto to drive the screen in this configuration. The closest I can see is 1360 x 768 (this is the only 16:9 listed).

That's because 1360x768 IS 16:9; whereas 1024x768 is 4:3. You can't force hardware to do the impossible.

---

### Post by spaceprobe on 2009-08-04
Hmm? You telling me my job?

1024 x 768 16:9 is most definitely possible. All the Macs we have here have no dificulty - it's described a s a "stretched" mode in the OS.

It's not impossible - it's anamorphic. Most widescreen TVs operate this way, widescreen film projectors used to operate this way.

The image sent to the screen is "squashed" horizontally (circles look egg-shaped) and the display panel/screen/monitor stretches it back out to fill the 16:9 screen (the pixels are then brick-shaped rather than square) and circles look perfectly round again.

So, back to my query; I guess from these responses Linux has difficulty in this area?

Cheers,
K

---

### Post by HavocXphere on 2009-08-04
> **spaceprobe said:**
> The closest I can see is 1360 x 768 (this is the only 16:9 listed).
You've got it the wrong way round. You need to be looking at 4:3 **resolutions** not 16:9 resolutions because that is the **number** of pixels the screen has. i.e. **signal aspect**. The pixel type (which is set in stone) will stretch that to 16:9.

However, in order to prevent stretching you need to tell xorg that your screen is a bit funky and that it needs to compensate in the calcs. You do this by telling it that you **Display size ** is 16:9.

 i.e. set DisplaySize in xorg.conf to the physical millimeter size of the screen.

[http://www.mythtv.org/wiki/Aspect_ratio](http://www.mythtv.org/wiki/Aspect_ratio)

> **spaceprobe said:**
> I guess from these responses Linux has difficulty in this area?
Anamorphic displays aren't really standard so there are few people interested in writing code for it in their free time.

> **spaceprobe said:**
> Hmm? You telling me my job?
You asking for help?

---

### Post by spaceprobe on 2009-08-04
> **HavocXphere said:**
> You've got it the wrong way round. You need to be looking at 4:3 **resolutions** not 16:9 resolutions because that is the **number** of pixels the screen has. i.e. **signal aspect**. The pixel type (which is set in stone) will stretch that to 16:9.

However, in order to prevent stretching you need to tell xorg that your screen is a bit funky and that it needs to compensate in the calcs. You do this by telling it that you **Display size ** is 16:9.

 i.e. set DisplaySize in xorg.conf to the physical millimeter size of the screen.

[http://www.mythtv.org/wiki/Aspect_ratio](http://www.mythtv.org/wiki/Aspect_ratio)


Anamorphic displays aren't really standard so there are few people interested in writing code for it in their free time.


You asking for help?

Yes, I'm asking for help. I'm sorry - I didn't mean that to sound the way you took it.

I'm not sure I have anything the wrong way round; I know - I need a 4:3 resolution "stretched" to fit a 16:9 screen ( I thought I'd made tyhat very very clear); I'm just having trouble explaining, as was evidenced by the first two (unhelpful) replies to my help request.

I've briefly checked out your link - it looks a bit involved for a Linux beginner, but I'll give it a try. I don't even know what a Xorg is!

I'm sorry if I sound a bit peeved. If you're interested, here's why (don't read any more if you don't want to read me ranting my personal opinions)...

Before delving into Linux, I was told over and over that its easy, it will do everything any other platform will do, there's loads of software, it doesn't go wrong, an idiot can do it, etc etc etc.

I was encouraged by all manner of people at tech shows, local computer fairs and Unix enthusiasts to ditch commercial OSs on the strength of all this.

In reality, after installing three times, after having to MAKE A SPECIAL FLOPPY for Bob's sake, after having to buy a new video card and throw away the PC's sound card, I actually find it can't drive a simple flat panel monitor/TV, it won't play DVDs, I can't get any slide
show software to run for more than an hour before crashing. Installing software is an absolute joke - packages and compiling and all that - it seems like I've stepped back into 1972!

Here's my conclusion and you're not going to like it: Linux is "sold" on the strength of it being a grown up mature alternative to "toy" OSs like Mac OS and XP, yet I can get a million different icon sets, skins, bells, whistles, and things to make Linux look good, but nothing as simple and grown up as a video driver that suits my purposes. And you all seem happy with the "few people interested in writing code for it in their free time" excuse. Is it a serious OS for a working environment, or not?

If it is not, then it shouldn't be dressed up as such.

There: enemies made, spleen vented, flame-proof suit donned.

K.

---

### Post by HavocXphere on 2009-08-05
> **spaceprobe said:**
> Yes, I'm asking for help. I'm sorry - I didn't mean that to sound the way you took it.
No worries you are clearly frustrated and rightly so.

> **spaceprobe said:**
> I was told over and over that its easy, it will do everything any other platform will do, there's loads of software, it doesn't go wrong, an idiot can do it
Some people get the under promise over deliver thing the wrong way round. If the people promoting it make exaggerated promises then its bound to end in disaster.

There are a few cases were everything does *just work* but for most people the Win/Mac -> Linux transition is bound to be sketchy for the first 6 months.

> I've briefly checked out your link - it looks a bit involved for a Linux beginner, but I'll give it a try. I don't even know what a Xorg is!

Shouldn't be too difficult. #1 make back-ups #2 Set resolution to 1024x768 in ubuntu itself. #3 Add info to xorg.conf #4 Restart

```
Section "Monitor"
  Option                 "CalcAlgorithm" "UseFrameBufferTiming"
  **DisplaySize  432 324**
  HorizSync      30-81
  Identifier    "Monitor[0]"
  ModelName      "SyncMaster"
  Option                 "DPMS"
  VendorName    "Samsung"
  VertRefresh  56-75
  UseModes        "Modes[0]"
EndSection
```
**Your millimeter measurements will obviously be different than the ones in the example.** Ignore the other options in that section...I don't think you'll need them.

I'm guessing you are running w/ a nvidia graphic card...but if you have an ATI card and are using the proprietary fglrx driver then you need an extra command to make the driver use the info in xorg:
```
aticonfig --input=/etc/X11/xorg.conf --tls=1
```


Also keep in mind that it is possible that the machine won't boot. My ubuntu experience is somewhat limited and I might have made a mistake somewhere. Hence step 1 is backups. ;)

> **spaceprobe said:**
> nothing as simple and grown up as a video driver that suits my purposes.
The buggy drivers annoy me too, but keep in mind that this is to some extent the hardware manufacturers fault. The proprietary drivers are provided by the manufacturers not ubuntu. And the ubuntu people can't fix the situation since the driver code & documentation is buried in non-disclosure agreements (Though this is changing slowly).

---

### Post by Mark Phelps on 2009-08-05
> **spaceprobe said:**
> Before delving into Linux, I was told over and over that its easy, it will do everything any other platform will do, there's loads of software, it doesn't go wrong, an idiot can do it, etc etc etc.

I was encouraged by all manner of people at tech shows, local computer fairs and Unix enthusiasts to ditch commercial OSs on the strength of all this.
Unfortunately, "enthusiasts" of all kinds can be less than accurate about the deficiencies of the things they love. 

Several of us have tried to indicate that Linux is not for everyone.  I, especially, have taken to task many times the Wine-fans who repeatedly claim that Wine will run everything that MS Windows will run -- even though the Wine vendor clearly indicates in writing that it will not.

> In reality, after installing three times, after having to MAKE A SPECIAL FLOPPY for Bob's sake, after having to buy a new video card and throw away the PC's sound card, I actually find it can't drive a simple flat panel monitor/TV, it won't play DVDs, I can't get any slide show software to run for more than an hour before crashing. Installing software is an absolute joke - packages and compiling and all that - it seems like I've stepped back into 1972!
Ouch!! Sounds like you've had a LOT more problems than most -- and unfortunately, the continuing evolution of infrastructure changes in Ubuntu releases (different audio system defaults, different XServer versions, different key handlers) coupled with the lack, and sometimes retirement, of Linux drivers, coupled with exposure of Linux to folks not accustomed to hacking out solutions -- all of this can combine to produce a very unpleasant "experience".

Just to show you you're not alone, I've been running Linux successfully on several machines for years, and then, when Canonical changed some infrastructure stuff, my tablet PC simply would not work properly anymore.  So, begrudgingly, I returned to using MS Windows on it -- where everything worked. Now, I'm running the Windows Seven RC on that box, and it works even better than Vista did, and (surprisingly) every bit as well (and in some cases, better) than did Ubuntu 8.04.
> Here's my conclusion and you're not going to like it: Linux is "sold" on the strength of it being a grown up mature alternative to "toy" OSs like Mac OS and XP, yet I can get a million different icon sets, skins, bells, whistles, and things to make Linux look good, but nothing as simple and grown up as a video driver that suits my purposes. 
Yeah, lack of a full function video driver can pretty much negate everything else an OS provides, but again, in the case of ATI chips/cards, the vendor retired their drivers for Vista at the same time.  At least in the case of Seven, they can run the "legacy" drivers in Vista compatibility mode and still get full resolution and hardware acceleration. In Linux, they (including me) are stuck with the open source drivers.

In my profession, they call this problem "lack of expectation management" -- getting folks all hyped up about something that they're not going to get, and then having to deal with the fallout when they're unhappy with the results.

Maybe, in your case, Linux is not the solution that works best.

---

### Post by spaceprobe on 2009-08-08
Thanks, both.

I tried the suggested fix and although the PC booted up and the Ubuntu desktop displayed I could only see a very small section of it. I managed to get everything back to the way it was eventually.  

I suspect the mistake was mine rather than the instructions being faulty, so I'm going to tray again when I have a moment.

Thanks again for your help and comments.

K.

---

