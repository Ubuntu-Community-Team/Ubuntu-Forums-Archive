---
title: "Ubuntu heating problem"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by alok.gautam on 2010-03-26
I have installed Ubuntu recently with the option "Install inside WIndows". It's great for surf and blog, but it gets heated ( My system is DELL XPS m1530 2.4GHz and 3Gb RAM). The hardisk keeps running and heats up the place to rest hands on my notebook. Any cure ? I am almost beginner so no heavy stuff please. TY.

---

### Post by 3rdalbum on 2010-03-26
What you should check first is that there are no runaway processes eating up CPU time. If there are programs running your CPU at 100% this can explain a warm laptop.

You can check this rather easily - go to System > Administration > System Monitor and go to the Processes tab, and then click on the CPU column twice to sort the list by CPU use.

Or, a more accurate method will be to open a terminal (Applications > Accessories > Terminal) and type:

```
top
```

Every couple of seconds, this program will show the top CPU-using programs. If one program stays near the top of the list and the number in the "CPU %" column is high, then this could be your culprit.

Kill the program; if you don't know how to do it from within 'top', then use System Monitor.

---

### Post by no2498 on 2010-03-26
doing what he said top or htop

in a terminal it will tell you how to install them
 it ask for your password you will not see it as you type it click enter


now type top or htop click enter

---

### Post by alok.gautam on 2010-03-26
I have tried that also, but no help. I recently used synaptic to install packages to access the Windows disk partition and played some video and application. But the problem was still there before that when RAM usage goes upto 60% and Processor use upto 50% on my system.

---

### Post by alok.gautam on 2010-03-27
[IMG]http://imgur.com/mqJ27.png[/IMG]
Here are the screen shots for the processes running on it, and it's heating up the system. What processes are causing this (in general terms ) ?

---

### Post by Phrea on 2010-03-27
> **alok.gautam said:**
> [IMG]file:///home/monsterdell/Desktop/Screenshot-1.png[/IMG]
[IMG]file:///home/monsterdell/Desktop/Screenshot.png[/IMG]
Here are the screen shots for the processes running on it, and it's heating up the system. What processes are causing this (in general terms ) ?

You have to upload those pictures somewhere.
I like [www.imgur.com](www.imgur.com)

---

### Post by gnometorule on 2010-03-27
I read 'install within Windows' == installed using Wubi. I have the same on an old laptop (a Vaio). It runs fine, but heats up quite a bit. Where it heats up (where you rest your hands) is just a function of where your Dell has its components. Dell's are typically bad at cooling stuff, so yes, go ahead and check if you got runaway processes; but my hunch is that the heating up is just normal. I'd only be concerned if the heating up is more than when you run your computer under Windows.

---

### Post by alok.gautam on 2010-03-27
Exactly, it doesn't heat that much when running Windows. I didn't mention but I can hear the buzzing sound of harddisk running while operating on Ubuntu, but nothing like either happen on Vista. I installed it with Wubi & IDK if Dell are bad with Ubuntu, some of their recent models consist of Linux.

Here are the screen shots of processes ----

[IMG]http://imgur.com/PBiQo.png[/IMG]

[IMG]http://imgur.com/mqJ27.png[/IMG]

---

### Post by gnometorule on 2010-03-27
That's odd. Only thing I notice is that a <sleeping> firefox eats up 48% of your CPU. That's weird. I checked it on my very old laptop right now, and while it can spike up briefly to around 50% on mine too when loading a page, when sleeping, its usage is, on mine, near 0% of CPU. Do you have the same issues when you don't run firefox? I doubt its a Dell issue. Dells overheat easily, but they would not overheat more under Linux than under Windows (at least I can think of no reason why they should).

---

### Post by no2498 on 2010-03-28
2 things i can think of trying 
download  opera in place of fire fox

open a terminal type, gstreamer-properties click enter
click video set the plugin to, x windows system (no xv)
or to x11

gstreamer-properties come from the cheese help faq's

x11 from smplayer

hope this helps

---

### Post by achase79 on 2010-03-28
You may also want to look up cpu scaling.  Even when not using all of the power of your processor, the processor may be using up all the evergy it can, this causes heating.  My Dell Inspiron 1000 cooled down considerably when I fixed the scaling issue.

---

