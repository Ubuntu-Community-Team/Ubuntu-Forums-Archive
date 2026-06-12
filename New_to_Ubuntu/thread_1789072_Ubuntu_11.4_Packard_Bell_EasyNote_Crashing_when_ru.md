---
title: "Ubuntu 11.4 Packard Bell EasyNote Crashing when running on battery with WiFi"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by squigles1 on 2011-06-23
[COLOR=black][FONT=Verdana]Having a problem with my Packard Bell Easy Note. I have Ubuntu 11.4 running on it. When every I try connecting to a mobile WiFi broadband while running on Battery power the computer crashes. I then need to force power off and restart the computer. If I am running on Mains Power, the system is stable.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Any suggestions for a solution?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Anyone else experiencing this problem?[/FONT][/COLOR]

---

### Post by crispy_420 on 2011-06-23
Could it be a faulty battery? Is it reporting a full charge?

---

### Post by squigles1 on 2011-09-13
Still crashing if A/C is disconnected while using WiFi.
No problem if connected to A/C.
It is as if the WiFi drains the battery.  Less than 5 seconds after disconnecting from A/C a message pops up about critical low battery power. powr being less than 14% then system crashes.

---

### Post by anewguy on 2011-09-13
Sounds to me like you have either a bad battery, or else the charging circuit in the laptop is no longer working.  I would lean towards a bad battery.  Yes, wireless takes power, especially when it's broadcasting.  However, it should not drain a good battery in 5 seconds.

Dave ;)

---

### Post by jdgregson on 2011-09-13
I had the same problem on my Dell Vostro 1014! I have never found anyone else with this problem till just now. For me, the problem was the Linux kernel. I could use the 2.6.31-32-generic kernel with my battery just fine, but with any kernel after that, if I unplugged the laptop from the charger it would crash. Not immediately, but after 10 - 15 minutes. And by crash I mean, complete lock up. The monitor stopped changing the picture, the keyboard/mouse no longer gave input (caps-lock wouldn't work) and if I was playing audio, it would just repeat the half a second of audio that it was playing until I turn the computer off. It seemed like the bridge between the hardware and software was down. And what is that bridge? The kernel. The only thing I could do to fix it was to switch to switch to Ubuntu 11.10 beta1 as my primary OS, which currently has the 3.0.0-11-generic kernel. I haven't had one crash since I switched. For me, the problem started with the Wi-Fi on battery, then as I upgraded kernels, it would crash on battery use, period. You should see if it is the kernel.

---

### Post by squigles1 on 2011-09-14
> **anewguy said:**
> Sounds to me like you have either a bad battery, or else the charging circuit in the laptop is no longer working.  I would lean towards a bad battery.  Yes, wireless takes power, especially when it's broadcasting.  However, it should not drain a good battery in 5 seconds.

Dave ;)

I would think that, only the computer runs for a few hours on battery if the WiFi is turned off.  Had Windows Vista on the system prior to changing to Ubuntu and did not have this problem.

So I am thinking it was more of a software or driver issue.  

[LIST=1]
[*]With either the computer management believes the battery has discharged when it is full, and is crashing as a result.
[*]Or, Their is an over use of power to run the WiFi causing the battery to discharge at an exponential rate resulting in a crash.
[/LIST]


> **jdgregson said:**
> I had the same problem on my Dell Vostro 1014! The only thing I could do to fix it was to switch to switch to Ubuntu 11.10 beta1 as my primary OS, which currently has the 3.0.0-11-generic kernel. I haven't had one crash since I switched. For me, the problem started with the Wi-Fi on battery, then as I upgraded kernels, it would crash on battery use, period. You should see if it is the kernel.

To be honest I am such a new user to Ubuntu that I dont know what a Kernal is or how to check it. :(

---

### Post by jdgregson on 2011-09-14
If you want to get technical, Linux IS the Linux kernel. The kernel is the primary part of the operating system. It allows the computer hardware to communicate with the software, and vise versa. When you press the 'a' key on your keyboard, the kernel is what 'answers' the keyboard's input. It then tells the rest of the software on the computer that the letter 'a' was pressed on your keyboard, so the computer can print the letter 'a' on your screen. 

What do you mean by crash? is it like I described in my first post, or does it turn off?

What kernel are you using? You can check by running the following command in terminal:

```

uname -r

```

---

### Post by squigles1 on 2011-09-14
> **jdgregson said:**
> If you want to get technical, Linux IS the Linux kernel. The kernel is the primary part of the operating system. It allows the computer hardware to communicate with the software, and vise versa. When you press the 'a' key on your keyboard, the kernel is what 'answers' the keyboard's input. It then tells the rest of the software on the computer that the letter 'a' was pressed on your keyboard, so the computer can print the letter 'a' on your screen. 

What do you mean by crash? is it like I described in my first post, or does it turn off?

What kernel are you using? You can check by running the following command in terminal:

```

uname -r

```

Thanks jd,
I am using Kernel 2.6.38-11-generic

My crash is a bit different from yours.
If I unplug the AC when battery is showing fully charged 
5 seconds later for a hairs breadth of a second message comes up that battery has less than 14% charge.
The image then disappears of the screen and a large amount of code appears (similar to with a controlled shutdown.) 
The screen then instead of going to the Ubuntu purple goes all rasta lines of white and purple and freezes.
At this point only solution is to hit the power off button, connect the AC
then turn the laptop back on.

---

### Post by jdgregson on 2011-09-15
Yeah, that problem is a bit different than mine. 

It could be your battery, but as you said, it was working fine with Windows Vista, so I still think it could be your kernel. 

If the kernel is the problem, it may be fixed automatically when Ubuntu 11.10 is released in October. It may seem like too long to wait, but I dealt with my problem for around 4 months, so hang in there.

---

### Post by anewguy on 2011-09-15
I found a launchpad bug report for this problem (ignore that it's reported on a different laptop):

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/516023]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/516023")

Someone does report a temporary work-around as this:

gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false

I don't know if this has to be applied each time you boot or not, or if there is a way to make it permanent.  But that's getting ahead of the game - try it and then unplug the AC and see if it stays up or not.

Let us know......


Dave ;)

---

