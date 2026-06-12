---
title: "Linksys WMP300N Wireless Adapter"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by KevinGallo on 2009-02-18
I've read a couple forums about how to get this adapter to work with ubuntu, but I literally just installed Ubuntu today, and and completely lost in all the technical terms. Is anyone willing to walk me through, step by tiny step, how to install this adapter.

Just FYI, I don't currently have access to the internet via the Ubuntu computer, I've noticed that makes a difference.

Thanks in advance
Kevin Gallo

---

### Post by swoody on 2009-02-18
Hi! and Welcome to the forums ):P

We'll try to start it off easy, and see if you're going to be lucky enough that this will be an easy install.

Go to System>Administration>Hardware Drivers and open that up. Does it show any drivers available in there? If it does, select it (or the one marked 'Recommended' if there are multiple drivers there) and 'Enable' it. Then it should install and tell you to restart the computer. After it reboots, you should be in good shape :) (knock on wood)

If there aren't any drivers displayed in there, open up a terminal (click on Applications>Accessories>Terminal), and enter
```
iwconfig
```
And let us know the output of that. Also, which version of Ubuntu did you install? 8.04? 8.10?

---

### Post by KevinGallo on 2009-02-18
Ok. I did the driver thing, and it installed a Braodcom STA wireless driver, but i still got no internet even after restarting.

When I did iwconfig, I got 

lo no wireless extensions
eth0 no wireless extensions
pan0 no wireless extensions

I'm using ubuntu 8.10

(side note: when I did the driver install, there's a video card driver, that was recommended, but it won't let me install it. any tips?)


[COLOR="Red"]I apologize. I tried again, just to double check. and it worked!

You are awesome. Thanks again.[/COLOR]

---

### Post by avtolle on 2009-02-18
On your video driver question; the driver needs to be downloaded and installed; without internet, no download is possible. So, need to get the Ubuntu box on the 'net first.

---

### Post by swoody on 2009-02-18
> **KevinGallo said:**
> I apologize. I tried again, just to double check. and it worked!

You are awesome. Thanks again.

You're very welcome! I'm glad to hear you got everything working :D

So your wireless is working fine now? And were you able to go back and install the driver for the video card as well?

---

### Post by KevinGallo on 2009-02-19
Yep. Once I connected to the internet, it downloaded the driver.

Thanks again for all the help guys

---

