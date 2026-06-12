---
title: "Everything working, just wondering"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by steel_lady on 2007-01-04
I am dumb for linux. There is some thing I am wondering about because I am afraid thet something goes wrong.  I have Dell inspiron 6400 with dual core processor that has wifi incorporated. In xp wifi is working normally having wifi light displayed. When I boot it in ubuntu and turn on wifi, irst it is lit uniformly and then it starts to blink with higher and higher frequency. It works, just that is blinking in anusual way and I am afraid that something will go wrong. Also i heard that probably my dual procvessor is not used completly in Ubuntu. Is it true?

---

### Post by n00b@linux on 2007-01-05
1. Blinking light
Nothing to worry about. My WG111T USB wireless adapter blinks sporadically.  If it's going to fail, it'll fail and there's nothing you can do about it.  RMA it back if you are still concerned.  Cover it over if it's annoying you.
 
2. Dual processor
It's probably true of every operating system out there, including windoze, that multi-core processors are not being used to their full potential. This fact has little to do with the operating system (Linux has had multithreading since the Intel 486, ie. 1989) and everything to do with the applications that run on it. The applications have to be specifically written with multi-threading in mind in order for the benefits to be obtained. This is quite a difficult job to do. Most (if not all) current applications on Windoze, Mac and Linux are not multi-threaded.
 
No one is dumb for linux. We all started out not knowing how it works.

---

### Post by eggdeng on 2007-01-05
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=277400](http://ubuntuforums.org/showthread.php?t=277400)

---

### Post by eggdeng on 2007-01-05
Sorry, should be a little less concise. If you want to see both cores working:

Open Synaptic
Mark the linux-686-SMP package (and its dependencies)
and click apply.

Right click on the panel->Add to Panel-> System and Hardware-> System Monitor. Sit back and enjoy.

---

