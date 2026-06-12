---
title: "I would like some help before installing Ubuntu"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by chrisxuk on 2010-04-14
Hi there,

I've tried Ubuntu before in the past, and I currently have 10.04 running in a VM. I just have a few problems before dual booting Ubuntu with XP. Hopefully you'll be able to help :)

Firstly is screen resolution. Running 10.04 in a VM at the moment I have the choice of two screen resolutions (800x600 and 640x480), both of which would prevent me from using Ubuntu more. I have an ATI HD Radeon 4850, so is there anyway of being able to get more resolutions?

Next question is about wireless internet. The main reason I stopped using Ubuntu before was that I couldn't get my wireless adapter to work. I have a Inventel UR54g which was supplied by my ISP (was Wanadoo, now Orange) and Ubuntu just didn't even seem to recognise it. Are there any drivers available for it, has anybody ever got one to work with Ubuntu or should I get a new one?

Lastly, for now, I have two monitors. One 22" connected via HDMI and one 19" connected via D-Sub, both coming out of my Graphics card. Can I use both screens on Ubuntu, just like I can with XP?

Thanks in advance, and if I have any more questions I'll make sure to ask them :)

Chris

---

### Post by undecim on 2010-04-14
You can boot an Ubuntu Live CD and try out Ubuntu before you install it. You can see for yourself what works and what doesn't. You may need to installed proprietary drivers for your graphics card and wireless card, which will require an internet connection.

---

### Post by howefield on 2010-04-14
> **chrisxuk said:**
> Firstly is screen resolution, so is there anyway of being able to get more resolutions?

Have you installed guest additions to your virtual guest system ?

Amongst other benefits is the ability to resize your desktop up to full screen and seamless mode. What graphics card you have doesn't matter in this respect when in a Virtualbox, as the guest system will be supplied with Virtualbox graphics drivers. 

This won't be a problem in a "real" dual boot.

> I have two monitors. One 22" connected via HDMI and one 19" connected via D-Sub, both coming out of my Graphics card. Can I use both screens on Ubuntu, just like I can with XP?

Yes you can.

---

### Post by chrisxuk on 2010-04-14
> **howefield said:**
> Have you installed guest additions to your virtual guest system ?

Amongst other benefits is the ability to resize your desktop up to full screen and seamless mode. What graphics card you have doesn't matter in this respect when in a Virtualbox, as the guest system will be supplied with Virtualbox graphics drivers. 

This won't be a problem in a "real" dual boot.



Yes you can.

I just tried to install Guest Additions, but nothing happened :( Did a Google about installing them, and it said a window should pop up with a link to download them. I got nothing :(

I think I might just create a new partition now and just whack 9.10 on there, see how it goes. I want to use Ubuntu, just the main thing i'm worried about is not being able to get my wireless adapter to work!

---

### Post by tom.swartz07 on 2010-04-14
> **chrisxuk said:**
> I just tried to install Guest Additions, but nothing happened :( Did a Google about installing them, and it said a window should pop up with a link to download them. I got nothing :(

I think I might just create a new partition now and just whack 9.10 on there, see how it goes. I want to use Ubuntu, just the main thing i'm worried about is not being able to get my wireless adapter to work!

As far as internet, youre either really lucky and you get a popup with restricted drivers, or you just wont have wireless....

As far as Virtualbox on Windows, the guest additions dont usually apply heavily to the video drivers. Virtualbox specifically gives the desktop those 2 choices, so that the whole desktop could run 'in a window' on the computer, rather than max out the video card that is owned by the host machine. 



Like they said above, just plug in a LiveCD and find out! From there, you could see both 1.) if the internet works and 2.) what configurations you could do with your video card out of the box.


Good luck!

---

### Post by NewsephJewallz on 2010-04-15
> **chrisxuk said:**
> I just tried to install Guest Additions, but nothing happened :( Did a Google about installing them, and it said a window should pop up with a link to download them. I got nothing :(

I think I might just create a new partition now and just whack 9.10 on there, see how it goes. I want to use Ubuntu, just the main thing i'm worried about is not being able to get my wireless adapter to work!

I advise you to just install 9.10 as you suggested on your PM to me as a porn-riddled XP machine will not meet your needs due to getting Trojan's all of the time.

Just try the Live CD, and keep searching for the appropriate drivers for your Wireless Adapter, other than that I recommend getting a new compatible Wireless Adapter or Wireless Card as you can pick them up fairly cheap these days.

:guitar:

-
Newseph out.

---

