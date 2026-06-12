---
title: "What to do about high CPU temperature"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by Djalmahal on 2009-06-28
Hi,

I have this old laptop running 9.04 and since a couple of days it just shuts down. I now realized (with help of a sensor applet) that my CPU is running extremely hot, right now at 84C with only firefox running. If I do multiple programs the temperature rises quickly, leading to the mentioned emergency shutdown. 

I cleaned out the vents of my laptop, anything else that I can do?

How do I clean the vents of the laptop properly?

Anything else I can do?

Thanks for the answers

Andreas

---

### Post by H2SO_four on 2009-06-28
limit how many programs you use at the same time to help keep the cpu temp down.  some like to install new fans in the lappy.  or look for less cpu intensive apps

---

### Post by Djalmahal on 2009-06-28
Well, the odd thing is that it worked fine till 3 days ago, I could run as much as I want with no problem. Now I see that there are a bunch of threads

[http://ubuntuforums.org/showthread.php?t=1178291](http://ubuntuforums.org/showthread.php?t=1178291)

concerning Jaunty and heat problems with laptops which confuses me because I ran Jaunty since it came out with no problems until a couple of days ago. So now I don't know if I should follow some threads advising CPU scaling or what.

---

### Post by QIII on 2009-06-28
If you were running Jaunty without problems for some time and suddenly you are getting overheating problems, my first two guesses would be that either:

1.  You have added an application recently that is running in the background or are using one frequently that is using an inordinate amount of your CPU.

2.  You are beginning to have indications of an impending hardware failure.

I think the second is less likely than the first.

Could you run

top

from the terminal and post the results back here?

---

### Post by DPJ93 on 2009-06-28
I had the same problem. Though, if you put a couple of soda korks under you laptop (to lift it a bit off the table) it should help. ;) You can also turn down the light on the monitor.

---

### Post by Steelmourne on 2009-06-28
If its only 3 days, then it probably isn't the cpu fan or its bracings in the laptop case. Have you installed any new software that might have caused this? You can also try cpu frequency scaling: [http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/).

---

### Post by ahndoruuu on 2009-06-28
all i can think of is that it must be some sort of background process eating up your resources

anything new you've recently installed?

---

### Post by MyR on 2009-06-28
Buy a laptop cooling fan. the end.

---

### Post by diablo75 on 2009-06-29
It sounds like the fan itself isn't spinning.  I can't imagine a fan failing to cool a CPU if it were running at full blast, especially after blowing the fins clear with a can of compressed air.  So the fan itself has probably died.  Happened to a client of mine a couple of weeks ago actually and it only took a 30 dollar part to fix the problem.  Check ebay out or google.

---

### Post by mcduck on 2009-06-29
> **diablo75 said:**
> It sounds like the fan itself isn't spinning.  I can't imagine a fan failing to cool a CPU if it were running at full blast, especially after blowing the fins clear with a can of compressed air.  So the fan itself has probably died.  Happened to a client of mine a couple of weeks ago actually and it only took a 30 dollar part to fix the problem.  Check ebay out or google.

I agree, any computer should be able to handle continuous 100% CPU usage for long times without any problems. If it doesn't, that's a hardware problem.

---

### Post by Djalmahal on 2009-06-29
Ok, I first guessed that it's some new application so I went into Synaptic looked up history and uninstalled everything I added in the last days.

But, I found out the fan broke, so that explains everything. I'll look into a replacement, for now I just run a normal fan and aim it at the "exhaust".

Thanks for all your help

Andreas

---

