---
title: "problems straming flash videos?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by insanity99 on 2009-01-19
i have flash 10 installed but videos are still choppy and sometimes appear blank if i goto full screen and then end up going off full screen

---

### Post by superprash2003 on 2009-01-19
what is your internet connection speed?

---

### Post by insanity99 on 2009-01-19
4MB, thats not the issue i dont think because it works fine on windows

---

### Post by CarpKing on 2009-01-20
I notice you are using an ATI card; which drivers are you using?  If it's the open-source ones, try enabling AccelDFS in xorg.conf: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/300346](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/300346)

---

### Post by insanity99 on 2009-01-20
i got the drivers catalyst control center. is that what you mean?

---

### Post by Ub1476 on 2009-01-20
Then you are probably using the official drivers from ATI (you can see if they are enabled in System-Administration-Hardware Drivers). 

If you aren't using those you are using the open-source driver.

---

### Post by Tatty on 2009-01-20
Are you using 64bit ubuntu?

I often found flash objects crashed to a blank image before I installed the alpha 64bit player.  I suspect it may be an issue with npluginwrapper

---

### Post by insanity99 on 2009-01-20
yea there in the drivers menu.

---

### Post by kansasnoob on 2009-01-20
While it's counterintuitive please go to the upper toolbar in Firefox > Tools > Addons > Get Add-ons and search for and install Flashblock 1.5.7.1.

You'll be prompted to restart Firefox so do!

This is assuming you're using Firefox 3.05.

Yes, you'll see flash objects replaced by a "button".

Click the button and play!

---

### Post by utnubuuser on 2009-01-20
Don't suppose you enabled flash through synaptic rather than through Firefox?

---

### Post by insanity99 on 2009-01-21
> **kansasnoob said:**
> While it's counterintuitive please go to the upper toolbar in Firefox > Tools > Addons > Get Add-ons and search for and install Flashblock 1.5.7.1.

You'll be prompted to restart Firefox so do!

This is assuming you're using Firefox 3.05.

Yes, you'll see flash objects replaced by a "button".

Click the button and play!
ok thanks i'll try that

> **utnubuuser said:**
> Don't suppose you enabled flash through synaptic rather than through Firefox?
well i think i got flash as part of medibuntu, dont know if that helps or not

---

