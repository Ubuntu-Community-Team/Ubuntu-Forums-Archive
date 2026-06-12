---
title: "Video driver or media player?"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by Northern Mike on 2009-09-22
Just put a new system together, the new cheaper route that I'm sure will be quite popular in future, however it's quite new and seems to possibly have issue with Ubuntu 9.04 currently.  I am using a Gigabyte GA-MA785GM-UD2H mother board with the ATI 4200 on board video.   I installed the available restricted driver ATI/AMD propietary FGLRX graphics driver.   I currently have the AMD unsupported hardware watermark on the lower right of my screen.   The issue is with video playback.   Flash player works fine for youtube but when I try to watch an avi it is very choppy from my desktop and crashes firefox if I try to watch online.   VLC works slightly better that Movie player but both are unwatchable.   I have put in the restricted extras package and have added the medibuntu repositories.   

My question:
Does this sound like a driver issue or a media player issue?

---

### Post by NoaHall on 2009-09-22
Disable compiz, and see if it's any better. ATI support currently sucks, but it will be much better soon(ish)

---

### Post by halitech on 2009-09-22
sounds like a compiz interference issue to me. Go into the appearance option and disable visual effects and see if it helps any.

---

### Post by doas777 on 2009-09-22
I had the same problem with an almost identical board yesterday.

I just downloaded the linux driver package from ATIs site, and ran the .run file in a console as sudo, and now everything seems to work right. no watermark/nag-tag. I'm going to be digging into the nitty-gritty tonight (HDMI audio is my next hurdle) so hopefully this setup remains stable.

ps, the video issues I was having yesterday did occure in several players (though very little problem with mplayer).

---

### Post by Northern Mike on 2009-10-01
Thank you all for your help, I attempted installing the driver manually and ended up making a mistake and screwed things up.   I had Karmic Alpha 6 sitting here and since I had nothing on the system anyway reloaded it.   Works great with the Alpha 6 of karmic.

---

### Post by markbuntu on 2009-10-01
The 4200 was not out when the 9.4 fglrx driver available in jaunty was released so it is not supported and will not work properly. What you need to do is remove that driver and install the latest one from the ati site. 

Karmic has a pre-release version of the 9.10 driver which will be out later this month.

---

