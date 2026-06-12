---
title: "Problem: Mouse seems to cease to work when watching videos/flash on 10.10"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by egervari on 2010-10-16
I have a weird problem where after watching a video (.mkv in vlc player) or a video on you tube (rand paul vs. jack convey debate), the mouse just stops working. I can still move the mouse cursor. Things will even hover and change colour too like they are supposed to... but clicks don't work any more. So the system because unusable with the mouse.

The keyword seems to work though, so I can press alt-ctrl-delete and then press the down arrow to "restart". That fixes it, but this is not a very good solution :/

After awhile if I don't restart, the system becomes unstable.

Is this a known problem? Any fix?

---

### Post by egervari on 2010-10-16
Now that I think about it, it might have had something to do with going to fullscreen. I had both the youtube video and the mkv file in full screen, and maybe switched it a few times while it was playing.

---

### Post by flyver on 2010-10-16
I have the exact same problem on my Sony, with 10.10. Thought it was because of flash/java problems on the 64-bit version of the operating system, but then I changed to 32-bit and the same happens...

I also tried disconnecting my wireless mouse in both versions, but the problem still occured with the touchpad.

So... Sorry, I don't have an answer, but you're not alone... I don't know what to do, but I'll consider going back to 10.04.

---

### Post by egervari on 2010-10-16
Yeah, I don't think it really has anything to do with the mouse, but rather, playing videos. There is something wrong with the playback that is causing problems. I don't think fullscreen has anything to do with it either. I've had it happen just by watching a 5 minute embedded video on dailypaul.com. After the video was done, I notice the mouse stopped working. 

If I don't play any videos, it just doesn't happen. This is a really big problem though. Something definitely changed from 10.04 to 10.10. Absolutely.

---

### Post by flyver on 2010-10-16
Yeah, at first I thought it only happened when viewing a movie online in fullscreen, but then it happened without the video being fullscreen... And it also happened with videos on my harddrive (Divx). So it probably doesn't have anything to do with flash, but rather with videos in general. Hmm. In my other post, someone suggested changing video drivers, from proprietary (or not proprietary?) to the other type, but I don't know what that means. I went to *system*, then *administration*, then *additional drivers*, and then it tells me that no proprietary drivers are installed on the computer.

---

### Post by egervari on 2010-10-17
Weird... I do have propritery drivers... but I never bothered to manually set them. They may or may not have been used. I have an Nvidia GeForce 9600 GT. Not exactly a bad/unknown video card :/

Currently, 10.10 is using version 173 of the nvidia drivers, and the ubuntu people say they work. I can upgrade to "version current". This is the one that failed on me last time on 10.04 though when I tried it then. It seems weird that I'd be getting problems now with 10.10 when I had no problems with the regular drivers in 10.10. I'll try the proprietary ones, but last time, it messed things up and I had to revert back.

---

### Post by egervari on 2010-10-17
I installed the latest/current drivers for my video card. While they work great on 10.10, it did not fix the problem.

I think I may know more about WHY this is happening. I watched another video for ScalaDays 2010, and when I used the volume button on my keyboard, instantly my mouse ceased to work.

So, I unplugged both my mouse and my keyboard, waited a bit, and plugged them back. This fixed the problem without having to ctrl-alt-delete out of the situation and reboot.

Could this have something to do with Microsoft keyboards that include special keys for increase volume? It might make sense that I used these keys while watching videos... which may have inadvertently caused me to think that the video playing was the culprit.

I also recall using my scroll wheel in VLC player to increase/decrease the volume, which may have caused the problem too.

**EDIT: YES, it IS is the volume buttons on the my "Microsoft Digital Media Pro Keyboard" The cause the mouse of all things to lock up.**

---

### Post by flyver on 2010-10-17
I too have a Microsoft keyboard (Microsoft Arc) and I just did a test: watching a video from my camera, then a flash video online, but without the keyboard and mouse connected. The problem never occured!

However, I want to continue using both my external mouse and keyboard, and I don't feel like disconnecting them every time I want to watch a video... So I would like a solution. Hmm, maybe finding some other driver for the Microsoft keyboard...?

I'll let you know if I figure something out...

---

### Post by egervari on 2010-10-17
Yeah, something definitely happened with the drivers - I suspect the keyboard, or perhaps a keyboard/mouse pair - that was not present in 10.04. This was a driver problem or a bug that is definitely new to 10.10.

How I can say this? I installed Ubuntu through the wubi installer that was 10.04. It worked. I upgraded it to 10.10 while still having wubi, and I had those problems. I just thought it was because of the upgrade, and I wanted to put on a real installation anyway.

So I uninstalled wubi, shrunk my partition, installed 10.10 off the cd, etc. -> the same problems.

10.10 is definitely the culprit, in some manner.

---

### Post by flyver on 2010-10-17
So [this]("https://bugs.launchpad.net/udev/+bug/637208/comments/40") seems to have fixed the problem - at least for now. Haven't done a lot of testing but the problem seems to have stopped...

---

### Post by egervari on 2010-10-17
I'll have to find that for x64... that one is for i386

---

### Post by flyver on 2011-02-03
[https://launchpad.net/~xorg-edgers/+archive/ppa/+build/1930625/+files/xserver-xorg-input-evdev_2.5.0%2Bgit20100822.990540fa-0ubuntu0sarvatt_amd64.deb](https://launchpad.net/~xorg-edgers/+archive/ppa/+build/1930625/+files/xserver-xorg-input-evdev_2.5.0%2Bgit20100822.990540fa-0ubuntu0sarvatt_amd64.deb)

(Comment number 44 in same thread.)

---

### Post by flyver on 2011-02-03
Hmm. My link probably doesn't work.

It seems that adding **ppa:xorg-edgers/ppa** works for 64-bit. 

Replace the icon that appers with ":" followed by "x".

---

