---
title: "wrong time"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by jrev on 2011-02-04
Hi all,
I cannot adjust the time indicated on the main control board which is not correct.
It indicates 17.39 but the real time is now 19h 15 min .
So why this difference in the display ?

I corrected it already some time ago but at times the time goes wrong again

How can I put back the right time now and keep it ?

Thanks for your answer :confused:

---

### Post by SlightlyChaotic on 2011-02-04
Click the date and time > Click the "Locations" rollout > Click Edit > Times Settings at the bottom of the window.

Does that not work?

---

### Post by jrev on 2011-02-04
> **SlightlyChaotic said:**
> Click the date and time > Click the "Locations" rollout > Click Edit > Times Settings at the bottom of the window.

Does that not work?

No it doesn't work !
the time is correct in the Time setting : no change to be done 
the trouble is the display doesn't show this same time :p

---

### Post by vivek.pandey on 2011-02-04
try this remove the applet from the panel...and then again add it

---

### Post by jrev on 2011-02-05
> **neo_aryan said:**
> try this remove the applet from the panel...and then again add it

Thank you neo_aryan  for this solution 

and now how to prevent the fault to come back ?

I have had it already many times on Ubuntu 10.04 ...

---

### Post by Paqman on 2011-02-05
Is the time in your BIOS correct? And do you have your clock set to sync online?

---

### Post by jrev on 2011-02-05
> **Paqman said:**
> Is the time in your BIOS correct? And do you have your clock set to sync online?

How do I synchronize my clock on line ?
in which chapter do I find the time in my BIOS ?  my BIOS is an Award

I have under Power Management setup :
X resume time 0  0  0

---

### Post by vivek.pandey on 2011-02-05
check this documentation...probably you have a dual boot if i am right
[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by techunit on 2011-02-05
If you are getting this problem on a regular basis your cmos battery might be going bad.

---

### Post by jrev on 2011-02-06
> **techunit said:**
> If you are getting this problem on a regular basis your cmos battery might be going bad.
When I start a new time on the panel, sometimes the increment is not effective and the display is not updated.

---

### Post by Paqman on 2011-02-06
> **jrev said:**
> Do I have to go to the corner computer shop to change it ?
Or can I change it myself ?

If it's a desktop you just need to pop open the case and swap the battery for a new one, it's very simple. Laptops can be a bit more problematic to disassemble, you can often find videos online showing how to disassemble a particular model, but I wouldn't advise it unless you're reasonably confident with disassembling electronics.

---

### Post by techunit on 2011-02-06
Please note this is only an educated guess.

---

### Post by jrev on 2011-02-11
[[IMG]http://data.imagup.com/6/1112088387.png[/IMG]](http://www.imagup.com/data/1112088387.html)

---

### Post by jrev on 2011-02-11
As you can see from the above snapshot the time is OK when I start the PC. Then the updating is faulty and the displayed time only changes when I change the time again

---

### Post by rburkartjo on 2011-02-11
jrev are you dual booting from windows to linux or viseversa. if you are i have a solution.let me know

---

### Post by jrev on 2011-02-11
> **rburkartjo said:**
> jrev are you dual booting from windows to linux or viseversa. if you are i have a solution.let me know

Thanks, I am always booting from the same Linux Ubuntu from 2 Linux systems installed on the hard drive :D

---

### Post by vivek.pandey on 2011-02-11
did you check out the link i gave?

---

### Post by jrev on 2011-02-12
> **neo_aryan said:**
> did you check out the link i gave?
Thanks, I am going to study the case and the doc :P
The fault is now steady : no time update on the control panel

---

### Post by Clever_Username on 2011-02-12
If the box is showing the correct time at boot, I would think the CMOS battery would be fine.

> **jrev said:**
> How do I synchronize my clock on line ?


To sync to an NTP server use this command:
```
sudo ntpdate 
```
When entering the command above, follow it with the IP of a public NTP server. A quick Google search should provide that for you

---

### Post by jrev on 2011-02-13
Where is the fault then ?

in the hardware or software ? I cannot decide yet ...

[http://www.zimagez.com/zimage/capture-jeanjean1.php](http://www.zimagez.com/zimage/capture-jeanjean1.php)

My problem is not with NTP but with [B]the ticking of the clock every minute 
[/B]
The correct time cannot reach the main control panel

the time indication is now 9.07

---

### Post by jrev on 2011-02-13
How does the time changes every minute on the main panel,
this is the question :P

it is still 9.07 on my clock

---

### Post by rburkartjo on 2011-02-13
jrev try this fix it worked for me i dual boot in ubuntu and win7. this also explains your problem. once i did the win7 reg thing the problem was fixed

[http://lifehacker.com/#%215742148/fix-windows-clock-issues-when-dual+booting-with-os-x](http://lifehacker.com/#%215742148/fix-windows-clock-issues-when-dual+booting-with-os-x)

---

