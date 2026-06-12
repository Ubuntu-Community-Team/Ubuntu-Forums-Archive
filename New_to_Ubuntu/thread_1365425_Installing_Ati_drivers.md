---
title: "Installing Ati drivers"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2009-12-27
Hi :) I downloaded Ati drivers which are a .run file. How do I install them? Also I have no proprietary drivers in hardware Drivers. Is that usual? Do I need to install a package? Thanks for any help.

---

### Post by diablo75 on 2009-12-27
Your user info says you are running Ubuntu 7.10.  Is that correct?

If there are no drivers available to enable in Hardware Drivers, it's probably because the proprietary drivers that are available from ATI are not compatable with the latest version of Xorg, and it's been that way since 9.04 I believe.  So typically the open-source ATI drivers are enabled by default upon install and are already in use.  It is best to just stick with these and not attempt to replace them with the proprietary drivers as you will likely turn your computer into a paper weight.

In short... it's best to not do anything at all.  ATI will not be issuing further updates for their proprietary drivers for what they deem "legacy" (old) models, so the only solution is to use the open-source drivers which have their drawbacks but at least have more potential.  I'm in the same boat as you with this issue, at least on my laptop; my home PC uses nVidia and is much nicer by comparison...

---

### Post by halitech on 2009-12-27
what ATI video card do you have? and what version of Ubuntu? The newer cards work fine with either the Open Source drivers or the ATI driver but the ATI driver only supports models above the HD2400 series. 

@diable75
> It is best to just stick with these and not attempt to replace them with the proprietary drivers as you will likely turn your computer into a paper weight.

in no way will anyone turn their computer into a "paper weight" by installing drivers that aren't supported. At best you boot into the recovery console and repair xorg, at worse you reinstall the OS but that doesn't turn it into a paperweight.

---

### Post by ThePinkWitch on 2009-12-27
Thankyou both for answering. I have a Saphire X1650 Pro (AGP). I'm having a weird occurance of windows fading to a dark grey and then coming back. My picture is slow and stuttery especially on facebook apps. I'm not sure if I have a hardware issue. My sound is awful as well. It's on board Realtek ac97. I'll probably have to reinstall Ubuntu because I'm not sure what I'm doing and I probably screwed something up :D
I'm running Ubuntu 9.10. Sorry I have really old info on my user CP. I changed it now.

---

### Post by halitech on 2009-12-27
the ATI X series isn't supported by the newest drivers from ATI so don't try to install it. Basically you will be using the open source drivers as provided when you installed. If you want to get better performance, drop back to 8.04 or 8.10 when the ATI drivers did work. 

9.10 still has a few bugs so hopefully if you do all the updates it will fix the sound issues. If not, you might want to go back to 8.04. It's a LTS release and will be supported for 3 years for updates. As far as facebook goes, it uses a lot of flash and java which don't work well in linux.

---

### Post by ThePinkWitch on 2009-12-28
Thankyou for the answers. I don't know whether to try to solve the graphic and sound issues or reinstall the previous version. I've spent days messing with getting things to run. Maybe it would be best to put a previous version on. Anyway. Thanks :)

---

