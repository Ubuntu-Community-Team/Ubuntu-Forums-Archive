---
title: "Help with K10 module"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-05-20
I have an AMD CPU and it requires the K10 temperature module for lm-sensors to give the CPU temp in the panel.

Reading all over the 'net has shown somewhat ambiguous info if not out-and-out contradictions. 

I have read (the short list) here:

[https://lists.ubuntu.com/archives/ubuntu-users/2009-May/183285.html](https://lists.ubuntu.com/archives/ubuntu-users/2009-May/183285.html)

and here:

[http://stochasticflux.com/blog/?p=13](http://stochasticflux.com/blog/?p=13)

I'm not a programmer and I'm not afraid to cut & paste at the terminal, modify files as sudo/gedit-or, etc., but I don't want to harm this box. It's a production box. So, to anyone reading this, if you have experience in compiling modules (and better if lm-sensor modules) ... would you suggest what compiling tools are needed?

Reading the top URL, I see I need linux-source. At 68 meg that's a lot, but I have never figured out what compiling tools are necessary.  I've read up at 

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

but it doesn't mention .bin files and how to compile them. Only .tar and .bz/.bz2.

---

### Post by Mark_in_Hollywood on 2010-05-24
I solved this by making certain that a newer kernel than came with Lucid Lynx ver. 10.04 would have, in-built, the module or driver for the K10 AMD temperature sensor that LM-Sensors requires. Although there is some "controversy" about this K10 module and some parts never working or mis-reporting, I felt confident that I could upgrade to a newer kernel and get LM-Sensors to report my CPU's temperature.

I have upgraded the kernel. LM-Sensors reports on 3 of the 4 cores I have. Two report a believable range of temps. One reports the temp being around 232 degrees F.

---

