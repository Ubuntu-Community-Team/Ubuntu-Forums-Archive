---
title: "nvidia  problem"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by ashwinipn on 2009-04-27
Hi,
I am facing a problem and could not solve it despite trying for two days.... I am running Ubuntu Intrepid 64 bit and Ubuntu Studio on that. My motherboard has integrated ATI Radeon HD 3200 card. I could not get it to work properly (the way I wanted) despite of using latest updated restricted drivers from AMD. I have Viewsonic VX2835wm (28", 1920x1200 native resolution) monitor. This resolution was rightly detected by the ATI driver/s. Since, almost all the time I had no effects enabled (compiz etc.) because it would interfere with the video playback and I had to contend with the gl or x11 instead of xv, I thought of trying my hands on nvidia as they are known to work better with Linux. I had one old 256 MB PCIe nvidia Fx Go 5750 (I think a variant of Go 5700) lying down. While installing.. came to know that only supported restricted drivers are 173 and 96 and not 177 and 180. So, went ahead with the installation of 173 along with nvidia-settings and nvidia-kernel-common. Currently able to run it successfully along with the compiz and all etc. effects enabled.
But I have couple of issues. Most important is my resolution. It is recognized as 1920x1080 and 60i refresh rate in xorg.conf file, which is not true. Screen resolution applet of Ubuntu tells different refresh rate (50-53) and nvidia-settings gives different (Auto or 60). Changing values of refresh rates in the xorg.conf file does not seem to have any effect on the configuration after restart. But if I change Option under "screen" or "device" to Mode and try it with the resolution of my choice, X does not start on bootup and have to change it back in order to boot up again. By any means I can't get the resolution of my choice that I know for sure is the native resolution of my monitor. Please help to solve this....

Edit: Also, when starting nvidia-settings.... it takes around five minutes for the settings window to load/splash. 

Thanks ...

Sincerely,

Ashwini

---

### Post by ashwinipn on 2009-04-28
Have I posted in a wrong place? There seems to be no suggestions whatsoever....

---

