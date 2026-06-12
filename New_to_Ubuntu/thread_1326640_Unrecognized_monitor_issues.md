---
title: "Unrecognized monitor issues"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by Elliot Szabo on 2009-11-14
I've been scanning the forums for a bit trying to find out how to have my display preferences recognize my monitor.  As of right now it just says unknown and displays everything in 800x600, which is much to large.  

I'm very new to Ubuntu so I might not be the quickest, but any help would be greatly appreciated. Thanks!

---

### Post by coldReactive on 2009-11-14
In ubuntu software center, install system profiler and benchmark, then tell us what your graphics card is.

Applications > System Tools > System Profiler and benchmark

under devices, PCI there should be a VGA controller.

---

### Post by Elliot Szabo on 2009-11-14
VGA compatible controller        : nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics]

---

### Post by coldReactive on 2009-11-14
Should do this in terminal (applications > accessories > terminal)

sudo apt-get install nvidia-glx-legacy

When you type your password, it won't show asterisks or anything, just type it out and hit enter (you cannot backspace.)

---

### Post by Elliot Szabo on 2009-11-14
This is what happened when I ran that in the Terminal

I've highlighted in red what I typed in after to try out what it was telling me.

elliot@Griffin-Studios:~$ sudo apt-get install nvidia-glx-legacy
[sudo] password for elliot: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-legacy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  nvidia-glx-96 nvidia-glx-173
E: Package nvidia-glx-legacy has no installation candidate
[COLOR=Red]elliot@Griffin-Studios:~$ sudo apt-get install nividia-glx-96[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nividia-glx-96
[COLOR=Red]elliot@Griffin-Studios:~$ sudo apt-get install nvidia-glx-96 nvidia-glx-173[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx-173: Depends: nvidia-173-kernel-source (>= 173.14.20) but it is not going to be installed
                  Conflicts: nvidia-glx
  nvidia-glx-96: Conflicts: nvidia-glx
E: Broken packages

---

### Post by coldReactive on 2009-11-14
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Check that thread, under legacy drivers.

---

### Post by James_Nostack on 2009-11-14
**EDIT: SOLVED MY OWN PROBLEM (SIMILAR TO OP'S), YAY**

I'm having the same problem as Elliot's first post.  (I am using 9.04 Jaunty.)  Except my version of System Tools doesn't include Benchmark or the System Profiler.  Furthermore, when I go to Applications > Add/Remove, neither is displayed under the System Tools, and a search under "all" comes up blank.

Like the OP I have some version of NVidia but I'm not sure which at this point.

---

### Post by James_Nostack on 2009-11-14
Actually, I think I managed to resolve this:

I went into
Applications > Accessories > Terminal

and typed "lspci -v" (without quotes) and hunted around for the "VGA Compatible Controller."

I then went to
System > Administration > Hardware Drivers

and it recommended installing the appropriate proprietary driver, which eventually required a reboot.

Then I went to 
System > Preferences > Display
where Ubuntu gave me a dialogue box suggesting I use the proprietary tools.  I then moved among the proprietary stuff until I found a drop-down box with Resolution, and found something I like better than 800 x 600 or whatever.

That seems to have made the difference; hope it's helpful in your case!

---

### Post by Elliot Szabo on 2009-11-15
I just tried out James' solution, but after install the screen refresh rate was horrible.  I tried changing it after I increased the resolution size, but the computer kept crashing on me.  It also said that it was a server edition, so I don't know if that had anything to do with it.  I'm going to go check out the latest driver thread coldReactive suggested.

---

