---
title: "Fan noice and 191 processes running"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Trandre on 2010-03-27
Hi

My computer is responding a little slow. But my fan noices all the time. I check htop and i have 191 processes running(it says so in the upper right corner after tasks:). CPU is fine though but memory is peaking in the graphics as seen in the pictures. 

1. Is this normal?
2. Somebody have an idea to how i can modify?
3.Why is mem in graphics peaking (upper left corner)?

I also want it to quiet down while using it as a document repository on a simple network.

Trandre

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151613&stc=1&d=1269701138[/IMG]

---

### Post by r-senior on 2010-03-27
It's not unusual. I'm using Xubuntu on this machine, but I have 140+ processes. 

The memory question is a common one. Ubuntu freely uses memory for caching, not just allocated to programs. This makes your machine more responsive. Ubuntu will release this cache immediately if programs need it. After all, memory is there to be used, it's not for decoration. ;)

Your machine may have been a little slow because some process was using lots of CPU. If you sort your processes by CPU time, you might see something that's a problem.

---

### Post by Trandre on 2010-03-27
Thanx for your answer r-senior

I am still trying to figure out the differences between the OS's I am used to 40-50 active processes in windows. 

Do you mean that the processes that have been active the longest is the ones to remove?

Like the top one on the picture?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=151614&stc=1&d=1269704255[/IMG]
Trandre

---

### Post by r-senior on 2010-03-27
Don't remove any processes!!! You don't need to. It's just the way it is and it's fine. No value in comparing with the number of processes on Windows.

The top one is your X-windows process. Kill it and you'll get booted back to a command prompt. ;)

Did you figure out how to sort by CPU%? Has the machine speeded up again?

EDIT: Ah, I see why you did what you did. I misled you by referring to "CPU time". It's CPU% (current usage) that's of interest when something is running slow, not cumulative CPU time used.

---

### Post by Trandre on 2010-03-27
He He, I tried to, but i think I had to gksudo it to alter, thanx for the warning or I would have been right back on the post with a new question :-)

I did figure out how to graphically alter it to sort by mem%, by clicking on it. Was it that you ment and will that alter performance?

Trandre
Linux schoolboy

---

### Post by Trandre on 2010-03-27
yes, it is faster now. I had xorg and chrome using a lot. But i uninstalled all the xorg and related drivers and then reinnstalled them and its much better now.

So if I understand you correctly, i shall use the mem% to see what processes are causing overload, and then attend them, elsewhere.
And mem usage is fine cause it releases when I need it anyway. 

Do you what i can do to lower my fan speed. Its not hot, but its on all the time?

Trandre

---

### Post by Terry of Astoria on 2010-03-27
about the fan noise - you ought to check to see if there's an issue with your motherboard  by googling the model # with "fan" or some keywords . . . If the speed sensor or the thermostat are not connected physically or if there is some failure then sometimes ubuntu can't tell if the fan should be on, so it is left always on. Read your system logs . . . Type 
```
dmesg
``` at the prompt to see some system output. Mine used to spit out messages about the fan every 5 seconds or so. Which fan is the offender? CPU fan? Or case fan? I've had a dell laptop fan that was constantly running super-fast and I didn't know what the heck to do but I finally discovered some advice that said to try to hit a certain key combination (ctrl+whatever) to reset the thermostat sensor. It worked instantly, and the fan acts normally now.  . .  
   Anyway I gotta go to work now. Good luck with yers.

---

### Post by r-senior on 2010-03-27
CPU% would usually show a process that is slowing down your computer. 

Sometimes MEM% might be relevant, but that would usually be accompanied by lots of hard disk access as memory is written out to the swap partition. You didn't mention that as a symptom and the memory looks fine.

Generally if there's a problem, it shouldn't need "kill process" intervention unless the application in question is not responding. Sometimes things do use lots of CPU for good reason.

Lowering the fan speed is not something I can help with. Laptops and newer machines may have fan-speed management but I don't know much about it. My best guess would be to look in your power management settings and see if there are any settings for fan speed. Somebody else will be able to advise better, I'm sure.

---

### Post by Mark Phelps on 2010-03-27
Sorry, didn't notice but are you running a laptop?

If so, do NOT, repeat, do NOT mess with the fan speeds.  

When the correct drivers and modules are loaded, fan speeds vary with processor usage.  But when that does not happen, fans are often set at high speed by default.

If your fans are not slowing down automatically, that probably means that your CPU isn't slowing down, too.  Reducing the fan speeds in that situation will burn out your CPU.

---

### Post by no2498 on 2010-03-28
i have a dell 6400 desk top 910 karmic and its fan was running fast and the computer was running hot
what i did was
open a terminal type, gstreamer-properties click enter
click video set the plugin to, x windows system (no xv)
and restarted the computer
its run fine since 
this was from cheese help faq's

now i see in smplayer it likes x11 

and like the last guy said do not change any fan speed yourself let the system do it

hope this helps you

---

