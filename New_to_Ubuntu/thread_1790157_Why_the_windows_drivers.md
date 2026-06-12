---
title: "Why the windows drivers?"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by itsadante on 2011-06-24
I'm rather new to linux (only had it a couple of weeks) and coding in general, but i do understand that there's MAJOR differences between the Linux kernel and the x86 that windows runs.

so here's my question: why is it that every single non-linux-coding solution to a hardware problem or such involves windows drivers?  wouldnt it be easier to find the mac OS X drivers for devices (since OS X runs on unix) and tweak them for linux use?  (granted you wouldnt be able to include them in the ubuntu iso file for proprietary reasons)

I'm posting this in the beginner talk forum since i'm a new user of ubuntu and i'm really not quite sure where else to post this.

thanks, dante

---

### Post by nomko on 2011-06-24
Do you have issues with some hardware now on your system?

Most hardware do work out-of-the-box. This is mainly due to the big contribution of the community.

---

### Post by mikenev on 2011-06-24
Interesting. Most hardware works just fine under Linux. Some companies (nvidia, ati) even release Linux specific drivers.

The only time I've ever had to look for a windows driver was for a wireless card using ndiswrapper. That was quite a while ago though, most of the wireless cards I've used lately have had native drivers.

Are you experiencing some difficulties with your hardware?

---

### Post by Bachstelze on 2011-06-24
> **itsadante said:**
> wouldnt it be easier to find the mac OS X drivers for devices (since OS X runs on unix) and tweak them for linux use?  

No, because the XNU kernel that Mac OS X use is just as different from Linux as the Windows kernel is.  So since there is much more drivers available for Windows than for OS X, it makes more sense to develop a Windows-Linux interface (i.e. ndiswrapper) than an OS X-Linux one.

---

### Post by doas777 on 2011-06-24
interesting. ndiswrapper is the only external driver loader I've ever heard of, and that is just needed because wifi driver operations are often patent encumbered and no entity with a license was making Linux kernel drivers. I personally haven't had to use it since '07 though. what solutions are you seeing involving windows drivers that aren't related to wifi?

---

### Post by grahammechanical on 2011-06-24
Compare the number of Windows installations with the number of OS X installs. Now think of people wanting to switch from Windows to Linux or to dual boot the two. It is likely that such people will have legal copies of the Windows WiFi drivers available. More so than OS X WiFi drivers.

Regards.

---

### Post by jtarin on 2011-06-24
> **itsadante said:**
> 
so here's my question: why is it that every single **non-linux-coding **solution to a hardware problem or such involves windows drivers? Because 99% of the hardware problems are on machines owned by you with installations of Windows.

---

### Post by itsadante on 2011-06-24
personally i've been having issues with a netgear wna3100 wireless adapter for my desktop.  it's been yes and no for people running 11.04 to get running.

the xnu kernel of mac is what i didnt know.  that windows drivers are easier to find is kind of a duh considering most people dont really even think there could be something better out there.

thanks guys!

---

