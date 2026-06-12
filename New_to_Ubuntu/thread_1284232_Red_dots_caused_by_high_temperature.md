---
title: "Red dots caused by high temperature?"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by whoelse on 2009-10-06
Hi,

I have a problem and hope that some of you may help me.

As I was just surfing the Internet today I saw several red dots on my display. When I closed the window it disappeared, but afterwards new dots appeared elsewhere.
These dots do not appear anywhere else other than ubuntu (neither in bios nor in Windows).
Afterwards I checked the BIOS for temperature and it was very high (70 celsius), but I am not sure what is my standard temperature. Can this temperature cause the dots?

My config: 
Ubuntu 9.04
core 2 duo
Radeon x1950pro

If this is the problem, do you have good suggestions to decrease the temp in bios?

who

---

### Post by QIII on 2009-10-06
If you are running a Core 2 Duo at 70C, you are headed for trouble.  You may be operating above the max, depending on the particular model.  Make sure your home smoke detectors are working properly.

(Not sure if that is the issue with your display, but I would say you need to address this issue before you do anything else.)

Could you let your machine cool down for several hours (!) and then post the results of 

```
top
```while you are running your browser?

You can press Cntl+C to stop the update and C&P the results.

I don't know if you can use frequency scaling in Intrepid with a Core 2 Duo to throttle your cores, but that may be worth a look see.

---

### Post by whoelse on 2009-10-06
Without starting the pc I can say that the output of "top" will not reveal any heavy usage processes, if that is what you are getting at. CPU usage is only higher than 10% if I do anything special but not in idle mode. 
The temperature is already high when I enter BIOS, but there like in Windows I have no problem.

---

### Post by QIII on 2009-10-06
You might give frequency scaling a try then.  (But be sure first that there are no problems with dust accumulation, etc...)

[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

---

### Post by whoelse on 2009-10-06
> **QIII said:**
> You might give frequency scaling a try then.  (But be sure first that there are no problems with dust accumulation, etc...)

[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)
I disassembled the Desktop and cleaned the CPU fan, so it should not be any of that.

Thanks for the link, I will see, if that helps.

---

### Post by whoelse on 2009-10-06
Hi,

after a short test, an update. Perhaps someone can help me now:

I use "QIII's" link to install frequency scaling, which works. But I can only change 1.86 to 1.6 which is not quite much and will not decrease cpu-temp a lot.

I also installed lm-sensors with the sensor applet. The two CPU cores were shown at 65 and 62 celsius. The applet tells me that it is not yet critical, but I have these red dots.
But there is one sensor which is way beyond good. The problem is that it is only called AUX and shows over 125 degree. It seems that lm-sensor itself does not know what this sensor is. 
Any ideas there? The only thing I saw that it seems like the sum of the two sepereate cpu-temps but of course it can be something else. Especially that I have no problems in Windows (with ATI-drivers) while problems in Ubuntu (without ATI-drivers) make me wonder if it can have something to do with my graphics card.

---

### Post by QIII on 2009-10-06
A bit of bad news.  ATI has put your card in the "legacy" heap and bailed out on you...

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

... so I'm not sure you could do anything more than keep with the open source driver.
I'm surprised those are the only two choices given for frequency scaling.

I'm not at my Ubuntu machine, but I think that this should get you a handle on what scaling options you should have

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

---

### Post by whoelse on 2009-10-06
> **QIII said:**
> I'm surprised those are the only two choices given for frequency scaling.

I'm not at my Ubuntu machine, but I think that this should get you a handle on what scaling options you should have

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```
output: 1862000 1596000

It seems that the temperature was a technical problem, I have borrowed a fan from a friend and now the temperature is 50 and 54, although I would prefer lower temps instead of high speed.
But AUX is still very high (127) and I still have red dots.

Anyone who can tell me what AUX is?

---

### Post by QIII on 2009-10-06
Haven't had time to digest this, but it might be helpful:

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

For red dots, try running the LiveCD and see if the behavior is the same.

---

### Post by sandyd on 2009-10-06
have you tried underclocking your GPU?
mine **was** factory overclocked when i bought it... but after a while, weird things started happening to the screen so i underclocked the card. all the problems dissapeared.

---

### Post by whoelse on 2009-10-06
thanks, as I understand your link I just ignore everything I do not like. :P

I will give the live CD a try.

Now I am even more curious about the red dots. 
With an average of 53 degree the CPU should not be responsible for graphic errors (unless it has been damaged previously by the high temperatures). 
And it also should not be the monitor, as it is working in Windows.

> **carlee said:**
> have you tried underclocking your GPU?
mine **was** factory overclocked when i bought it... but after a while, weird things started happening to the screen so i underclocked the card. all the problems dissapeared.
Sorry but I have no idea how to do that. I have only checked the ATI tool in windows and the temperature there is about 40 degree.

Okay, rovclock seems a way to do that, any suggestions for parameters for a radeon 1950pro, if this card even works with rovclock and is not using some stuff from the original ATI drivers.

---

### Post by QIII on 2009-10-06
The Radeon x1950pro is a card, is it not?

If it is, does your motherboard have on-board graphics?  You might be able to eliminate hardware for sure (I suspect it's not hardware since the "other OS" works fine) by taking the card out and running from on-board graphics...

But that would really be a pain!

---

### Post by whoelse on 2009-10-06
> **QIII said:**
> The Radeon x1950pro is a card, is it not?

If it is, does your motherboard have on-board graphics?  You might be able to eliminate hardware for sure (I suspect it's not hardware since the "other OS" works fine) by taking the card out and running from on-board graphics...

But that would really be a pain!
There is no on-board graphics.

---

### Post by QIII on 2009-10-06
Crud.

Well, I'm not convinced it's hardware anyway, since it works in Windows.

---

### Post by Terl on 2009-10-06
I have an X1650 and it does the same every now and then.  If I am in windows eventually a window pops up saying the graphics driver had to reset.  In Linux I just use the open source driver.  I have thought it was the graphics card acting up.  If I put the nVidia 7300 back in it never does crashes like the ATI.

---

### Post by whoelse on 2009-10-08
Hi, I just wanted to tell you:
I wanted to try your ideas but I have not encountered any dots yet, although I have not done anything.

I always thought that Windows is the only real random function but it seems that Ubuntu has now something similar. :P
I just hope that it is now gone forever. And I am still wondering what the AUX sensor means.

Thanks for your help...

---

### Post by lavinog on 2009-10-08
The open source ati driver has DynamicClocks disabled by default.  This can make your card run hotter. Try enabling it.
use **man ati** for more info.

---

