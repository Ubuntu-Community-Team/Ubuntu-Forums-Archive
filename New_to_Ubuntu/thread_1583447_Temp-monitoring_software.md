---
title: "Temp-monitoring software"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Madrias on 2010-09-27
I need easy to setup temperature monitoring software for my 10.04 Ubuntu system.  The reason is that it's a Pentium 4 laptop with a 3.0Ghz hyperthreaded chip.  Needless to say, I would like to know how hot it's running.  It's running the desktop edition of 10.04, and I'd like to input the least amount of code possible.

---

### Post by wojox on 2010-09-27
You should have [lm-sensors]("http://www.lm-sensors.org/wiki/Documentation") already installed.

---

### Post by marshmallow1304 on 2010-09-27
There's a Gnome panel applet called Hardware Sensors Monitor.  I don't remember if it's installed by default.  If not, the package name is sensors-applet.  It can display temps from a variety of sources with icons and bar charts if desired.

---

### Post by mastablasta on 2010-09-28
> **Madrias said:**
> easy to setup temperature monitoring software 
 
i don't think easy to setup with a nice GUI exist in Linux world. 
 
There is no aplication as nice as for example speedfan in windows which will let you know after 2 double clicks if your CPU is hot and fan is not fast (with nice icon so it's clear even if you are a total newbie in the whole thing). then you can also easilly change it all through GUI. i dont' think such a hting exists in Linux world.
 
Clonky is a nice monitor but installing it might not be as easy as double clicking a file to install it.
 
in CLI a couple do exist. again extensive documentation should be read before use. Ubuntu - OS for human beings (but only human beings ones with a lot of extra time to spare to go through all the manuals).

---

### Post by HarmCla on 2010-09-28
You could use the built-in applets for your panels,
or install Screenlets.
Screenlets is a desktop-widgets-manager,
to install Screenlets, just look for it in Software Center.

---

### Post by Soul-Sing on 2010-09-28
you could install lm-sensors via synaptic with:
-hardware sensors applet, or
-gkrellm

when installing lm-sensors you got some questions in the console/terminal, and a reboot is nec. to make it active!

---

### Post by madmax75 on 2010-09-28
> **marshmallow1304 said:**
> There's a Gnome panel applet called Hardware Sensors Monitor.  I don't remember if it's installed by default.  If not, the package name is sensors-applet.  It can display temps from a variety of sources with icons and bar charts if desired.

Yes, **sensors-applet** is good. Install from Synaptic, then add it to the panel (it reads as Hardware Sensors Monitor in the panel applet list). I have it on my top panel to monitor CPU temps. It also shows my graphics card temperature.

There is also **xsensors**. Shows at least cpu temps, maybe even more, I think it depends on the machine and the sensors you have available.

---

### Post by Mark Phelps on 2010-09-28
> **mastablasta said:**
> i don't think easy to setup with a nice GUI exist in Linux world. 

Then, you obviously don't know about GKRellm -- a GUI-based hardware-monitoring program.

Also, there is Conky -- also GUI -- but involves a lot of customization work, although you can find profiles already made and reuse them.

---

### Post by oldsoundguy on 2010-09-28
Gnome applet for lm sensors has a simple GUI once you have activated the program in synaptic and installed it into your panel .. been using it for several builds now. It has a small graphic+text display that rides in the Gnome panel.  Because I run a hyperthreaded CPU on the main Linux box, processor heat is something that has to be monitored closely .. if it gets too high, it will destroy the capacitors sitting next to it! (had it happen once .. and that was enough!)

---

### Post by Stunt Double on 2010-09-28
I have the same P4, 3.0Ghz processor and I agree that monitoring it is a good idea. I never run my computer without a cooling pad.
To install, follow the instructions from 2hot6ft2 in this thread: [http://ubuntuforums.org/showthread.php?t=1468843&highlight=sensors](http://ubuntuforums.org/showthread.php?t=1468843&highlight=sensors).
Answer YES to each question, and highlight the YES or  OK, as necessary,then ENTER.

---

### Post by mastablasta on 2010-10-01
> **Mark Phelps said:**
> Then, you obviously don't know about GKRellm -- a GUI-based hardware-monitoring program.


hmm i installed this GKRellm (conky seems a bit complicated though i don't know why Ubuntu doesn0 tinstall it by default and leave it in as an option - like i think DSL)

anyway it says no sensors found. great, isn't it? i am sure BIOS read the temp.... bah need to find somehting else or maybe try with conky....

it's just that is sounds a bit loud and i am not sure is it the PSU fan that is loud or CPU fan.

---

### Post by gandaran on 2010-10-01
> **mastablasta said:**
> hmm i installed this GKRellm (conky seems a bit complicated though i don't know why Ubuntu doesn0 tinstall it by default and leave it in as an option - like i think DSL)

anyway it says no sensors found. great, isn't it? i am sure BIOS read the temp.... bah need to find somehting else or maybe try with conky....

it's just that is sounds a bit loud and i am not sure is it the PSU fan that is loud or CPU fan.
no sensors found? you may need to install lm-sensors and run in terminal
```
sudo sensors-detect
```
answer yes to all questions then reboot the computer, gkrellm now should detect the sensors, this is for old motherboards, you do not need to run this for newer motherboards and if gkrellm still wont work try out the panel sensors-applet.

---

### Post by mastablasta on 2010-10-02
oh so it just needed to detect them. heh don't know why such command is not run automaticly....

well ok everything seems to be normal. thanks for the help.

---

### Post by KirbySmith on 2010-10-04
I followed the instructions of thread 1468843 referenced in message 10 (except for the hard drive parts) for my Gigabyte based desktop.  The process detected a few possible sensors, but the only one that shows up in the applet's preferences>sensors menu is that of the nVidia GPU.  None of the motherboard sensors that are available to the BIOS are shown.   I would like to know the CPU temp at a minimum.

Any suggestions to show the motherboard sensor temps with this applet, or do I need a different program?

Thanks

kirby

---

### Post by gandaran on 2010-10-04
> **KirbySmith said:**
> I followed the instructions of thread 1468843 referenced in message 10 (except for the hard drive parts) for my Gigabyte based desktop.  The process detected a few possible sensors, but the only one that shows up in the applet's preferences>sensors menu is that of the nVidia GPU.  None of the motherboard sensors that are available to the BIOS are shown.   I would like to know the CPU temp at a minimum.

Any suggestions to show the motherboard sensor temps with this applet, or do I need a different program?

Thanks

kirby
which applet did you add to panel, was it the hardware sensors monitor, this one should show cpu and motherboard temperature.
check the applet preferences, maybe you have to enable the motherboard temperature readings

---

### Post by KirbySmith on 2010-10-04
It is called "Hardware Sensors Monitor" and adding another one results in the same nVidia-only measurement.

Preferences only lists the nVidia sensor.

kirby

---

### Post by KirbySmith on 2010-10-04
Also, installing GKrellM reveals it too only sees the GPU sensor, although I haven't yet repeated the sensor detect terminal command and rebooted again for it.  That will have to wait for tonight.

k

---

### Post by Mark Phelps on 2010-10-04
There continues to be a known problem with GKRellm in that the version available through the repos does NOT have libsensors support compiled into it.  That results in it NOT being able to read some of the more common sensors.

To get this to work on my box, I had to download the source, obtain all the necessary source libraries, compile and build the executable, and then run that.

Without libsensors support, in the newer kernels, you often see little or no temperatures and/or fan speeds being reported.

---

### Post by KirbySmith on 2010-10-04
Rats! (C. Brown)
 
I probably won't be doing any compiling tonight or the near future.
 
Is it possible that this is also the problem with the Hardware Sensors Monitor applet not showing temps?
 
kirby

---

### Post by KirbySmith on 2010-10-05
Rerunning sensors-detect yielded the same results as before but now I have a better understanding of what it is trying to tell me.  From /etc/modules

```
# Generated by sensors-detect on Tue Oct  5 10:51:40 2010
# Chip drivers
# no driver for AMD K10 thermal sensors yet
```It didn't specify a driver module because it doesn't know of a suitable driver.  Maybe someone is developing one somewhere.  I'll try this soon on the other PC with the older AMD CPU and see if it works. 

kirby

---

### Post by KirbySmith on 2010-10-05
Further research found

[HTML]https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/316257[/HTML]If the K10 sensor chip driver is present in 10.04 Lucid, then is it possible to get it into 9.10 without having to recompile the kernel?

kirby

---

