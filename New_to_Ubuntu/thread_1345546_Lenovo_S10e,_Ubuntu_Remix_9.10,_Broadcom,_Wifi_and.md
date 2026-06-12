---
title: "Lenovo S10e, Ubuntu Remix 9.10, Broadcom, Wifi and D-Link"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by pkr1979 on 2009-12-04
Hi all!

I'm pretty new to this Ubuntu stuff. That means I have been using it for a while, but whenever I've had any problems I just asked my brother who solved them for me.
Anyway, I have to start trying to figure out stuff for myself so I tought I'd try using this forum to improve my Ubuntu skills.

My problem is this. I have this Lenovo S10e with a broadcom wifi card. I have innstalled Ubuntu Remix 9.10 on it and the wireless internet connection seems to work fine. Infact, it detects several different networks (secured and open), except the secured set up for my roommate and me (its not hidden) through a D-Link rooter.

As far as I can tell both the Broadcom B43 wireless driver and the Broadcom STA driver is installed, and I have been trying to activate theese off and on in different combinations. The B43 seems to partly deactivate itself whenever the STA is on, but I'm not sure on this. Also restarting my computer after activating the STA seems to interfere with the function of restarting the computer, it sort of hangs up... I often have to hold in the computers power switch to turn it off. This might be a different matter though, and it has been working fine the latest couple of times. So maybe its solved by itself?

Anyway, I did not install the drivers myself they were preinnstalled if this is of any importance.

I should also say that this problem of detecting my network did not start with remix 9.10, but with remix 9.04. In the beginning it worked just fine with the remix 9.04 until it suddenly could not detect my network anymore (several others though). With the Ubuntu (not remix) 9.04 on my other laptop it has always worked fine. I dont think this computer uses broadcom though. Computers using mac and windows also detects this particular network.

Does anyone have any ideas on why it cant detect my network? Is it due to remix 9.04/9.10? Broadcom? D-link? I find it odd that other computers find the network. After all a netbook is something you buy for going online on the move and hence relie on detecting the wireless connections that exist. This should also be the case with the Remix versions of Ubuntu. I was quite happy with 9.04, a little less with remix 9.04, and even less happy with remix 9.10.

Please help me.

---

### Post by ikt on 2009-12-04
> **pkr1979 said:**
> Please help me.

Sorry I'm a little confused, you're saying the wireless worked originally with 9.04 ubuntu netbook remix, then you upgraded to 9.10 ubuntu netbook remix and it no longer works?

---

### Post by pkr1979 on 2009-12-04
Hello.
In the beginning it worked with 9.04 ubuntu remix, then it stopped to work. Then i installed 9.10 remix in hope that it would work again. But it didnt. I can detect other networks though. Just not my own. Other computers can detect it though.

---

### Post by ikt on 2009-12-04
> **pkr1979 said:**
> Hello.
In the beginning it worked with 9.04 ubuntu remix, then it stopped to work. Then i installed 9.10 remix in hope that it would work again. But it didnt. I can detect other networks though. Just not my own. Other computers can detect it though.

Are you able to manually input the connection info?

System > Preferences > Network connections > wireless

---

### Post by pkr1979 on 2009-12-04
Yes, I have done that. It seems like the computer sets up its own network. It will say I am connected 100% (the wifi icon) but I cant go online.

---

### Post by pkr1979 on 2009-12-07
It seems like I figured it out. I had to change some of the settings in the rooter.

---

### Post by ikt on 2009-12-07
> **pkr1979 said:**
> It seems like I figured it out. I had to change some of the settings in the rooter.

What settings did you change?

---

### Post by pkr1979 on 2009-12-07
I dont really know. She (the customer service lady at d-link) talked me throu it and I didnt really pay atention. It was within the wifi-configeration I guess. There were some things I disabled... some more stuff as well. I didnt really know what I was doing.
Anyway, I know that the settings were changed to something that fitted better wifi-networks cards better. It was here opinion that the networkcard/driver in my ideapad S10e and the Ubuntu Remix 9.10 drivers couldnt handle the previous settings.
Understandable? More or less I hope...

---

