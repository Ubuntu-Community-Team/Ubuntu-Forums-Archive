---
title: "CPU Performance Test Application"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2008-12-28
Does anyone know an application or a tool that can stress test the cpu and/or entire system under ubuntu? I was hoping to overclock my cpu and then monitor the results, and i want to know if such package or software exists.

Originally, I was going to stress test the cpu by running some heavy applications at the same time (for example, converting an entire movie in Avedimux + tar a 1GB directory) and then monitor results in conky. I just want to know if there is a good, simple tool that does that for me.
Thanks

---

### Post by Michael.Godawski on 2008-12-28
hi,

have a look at this thread, perhaps it the right one:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=227625](http://ubuntuforums.org/showthread.php?t=227625)
[/LIST]

---

### Post by RomeReactor on 2008-12-28
Hi. You could also try the [Phoronix test suite]("http://www.phoronix-test-suite.com/?k=downloads").

---

### Post by Abu_Dayya on 2008-12-28
> **RomeReactor said:**
> Hi. You could also try the [Phoronix test suite]("http://www.phoronix-test-suite.com/?k=downloads").

This one looks comprehensive and professional, although a little more than what I wanted. I'll try this one when I get out of work. 

Does it monitor CPU temps? or do I have to monitor it with another program (like lm-sensors or conky)

Thanks

---

### Post by RomeReactor on 2008-12-28
> **Abu_Dayya said:**
> Does it monitor CPU temps? or do I have to monitor it with another program (like lm-sensors or conky)

As far as I know, it only does benchmarks. To monitor temperatures, you could also try sensors-applet:
```
sudo aptitude install sensors-applet
```
You can then add it to the top panel by right-clicking on it, selecting "Add to Panel...", then choosing "Hardware Sensors Monitor".

---

### Post by phoronix on 2008-12-28
> **Abu_Dayya said:**
> This one looks comprehensive and professional, although a little more than what I wanted. I'll try this one when I get out of work. 

Does it monitor CPU temps? or do I have to monitor it with another program (like lm-sensors or conky)

Thanks

If you have lm-sensors installed and configured, when running the Phoronix Test Suite run:

MONITOR=all phoronix-test-suite benchmark <command>

and it will plot on a line graph all sensors it detects while the benchmark(s) are running.

---

### Post by theozzlives on 2008-12-28
As a Tech, I advise against overclocking. It can make the system unstable.

---

### Post by Abu_Dayya on 2008-12-28
Well, I agree that overclocking is not that important or necessary, and it may be a bad idea as it can cause hardware damage and instability. The only reason I want to do it probably is because I can. And it will satisfy my ego. I don't know why I want to do it actually, I just want to try it. 

And I won't overclock the CPU to the extreme. Just give it a little bump. I have the 2.0GHz intel E4400, and I'm trying to push it to 2.6 or 2.8 at the max

---

### Post by shifty_powers on 2008-12-28
> **theozzlives said:**
> As a Tech, I advise against overclocking. It can make the system unstable.

well thats a gross generalisation.

i would say do not overclock if you do not know what you are doing, sure.

but if you know what you are doing, you can get some good extra increases in system speed and keep stability....

whether you NEED to is another matter.

---

### Post by Abu_Dayya on 2008-12-28
> **phoronix said:**
> If you have lm-sensors installed and configured, when running the Phoronix Test Suite run:

MONITOR=all phoronix-test-suite benchmark <command>

and it will plot on a line graph all sensors it detects while the benchmark(s) are running.

Thanks alot.
Is there some kind of tutorials or useful FAQs to the test suite that I can read?

---

### Post by sdennie on 2008-12-28
I would actually advise against overclocking simply because CPU speed has become less and less relevant lately.  A 20% increase in CPU speed probably won't translate into any noticeable performance gains unless you are doing CPU bound tasks (and desktop applications aren't).  However, if your motivation for overclocking is simply, "Because I think it would be fun", then yes, go for it and enjoy.  ;)

---

### Post by RomeReactor on 2008-12-28
> **Abu_Dayya said:**
> Thanks alot.
Is there some kind of tutorials or useful FAQs to the test suite that I can read?

The [documentation]("http://www.phoronix-test-suite.com/documentation/1.4/index.html") seems fairly comprehensive, and there's a [forum]("http://www.phoronix.com/forums/forumdisplay.php?f=49") as well.

---

### Post by Messyhair42 on 2008-12-28
mprime is the linux version of prime 95. i've been running prime 95 constantly for years as part of GIMPS. it offers a wide range of stress test possibilities i.e. low or high memory test based on the FFT size

---

