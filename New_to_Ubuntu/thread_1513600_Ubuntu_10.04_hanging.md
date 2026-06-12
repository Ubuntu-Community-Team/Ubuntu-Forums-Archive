---
title: "Ubuntu 10.04 hanging"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by guscpu on 2010-06-19
Twice in the last 2 weeks my OS has hung. Usually I know this is happening when the fan goes crazy out of the blue and its confirmed when I try to move the mouse or use the keyboard. Incidentally I wasn't running resource hungry apps on either occasion. This may have happened on another occasion but was doing something else at the time and when I got back to the computer all was fine.

Normally I'll leave it for 5 minutes or so and if there is still no response I switch it on and off. Its really annoying, always thought Unix/linux was immune to this. Embarrassingly Win XP was better behaved !! 

Regardless I have two questions:

Why is this happening in Linux, surely its designed to isolate misbehaving apps. And if so is it the kernel that's the problem?

How do I find out what is doing this?

Thanks
Gus

---

### Post by 4Orbs on 2010-06-19
Two suggestions, don't know if they'll solve your problem. This might be happening because your screensaver it trying to activate but you don't have the proprietary driver installed for your graphics card. Some of those screensavers require 3D acceleration which will make the computer freak out when the proprietary driver is not installed. Either activate the driver by going to the menu System>> Administration>> Hardware Drivers or set your screensaver to "Blank Screen Only". The other potential cause could be your Update Manager fetching it's updates. You can turn off the Auto-Update in the Update Manager settings. You will need to update manually thereafter.

---

### Post by pete1983 on 2010-06-19
Hello guscpu 

 Do you have a proprietary video driver installed?
Here is how to check go 
[COLOR="Red"]System-administration-hardware drivers[/COLOR] 
When you click hardware drivers it will check for video drivers and show if any are installed.The video drivers can cause some problems or fix them, so try them all and see if any of them fix your
problem.If you still have problems I found this post that seems to be related and is very large and may contain a fix [http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

Good luck

---

### Post by Miljet on 2010-06-19
The fan running like crazy offers the clue that something is maxing out either the CPU or GPU. I did a quick Google search for "Ubuntu CPU usage" and turned up quite a few discussions. Here are the links to a couple.

[http://ubuntuguide.net/howto-view-and-limit-process-cpu-usage-in-ubuntu-linux](http://ubuntuguide.net/howto-view-and-limit-process-cpu-usage-in-ubuntu-linux)

[https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU)

I have never personally ran into this problem, but apparently a lot of people have. Sorry I can't be of more help, but at least this post will bump yours back to the top.

---

### Post by guscpu on 2010-06-19
> **4Orbs said:**
> Two suggestions, don't know if they'll solve your problem. This might be happening because your screensaver it trying to activate but you don't have the proprietary driver installed for your graphics card. Some of those screensavers require 3D acceleration which will make the computer freak out when the proprietary driver is not installed. Either activate the driver by going to the menu System>> Administration>> Hardware Drivers or set your screensaver to "Blank Screen Only". The other potential cause could be your Update Manager fetching it's updates. You can turn off the Auto-Update in the Update Manager settings. You will need to update manually thereafter.


I don't have a screen saver activated. The proprietary driver installed and activated is the tested and recommended one. So am at a loss

---

### Post by guscpu on 2010-06-19
> **pete1983 said:**
> Hello guscpu 

 Do you have a proprietary video driver installed?
Here is how to check go 
[COLOR="Red"]System-administration-hardware drivers[/COLOR] 
When you click hardware drivers it will check for video drivers and show if any are installed.The video drivers can cause some problems or fix them, so try them all and see if any of them fix your
problem.If you still have problems I found this post that seems to be related and is very large and may contain a fix [http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

Good luck


Gosh thats a big post, might take me some time to trawl through that lot :)

Thanks

---

### Post by guscpu on 2010-06-19
> **Miljet said:**
> The fan running like crazy offers the clue that something is maxing out either the CPU or GPU. I did a quick Google search for "Ubuntu CPU usage" and turned up quite a few discussions. Here are the links to a couple.

[http://ubuntuguide.net/howto-view-and-limit-process-cpu-usage-in-ubuntu-linux](http://ubuntuguide.net/howto-view-and-limit-process-cpu-usage-in-ubuntu-linux)

[https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU)

I have never personally ran into this problem, but apparently a lot of people have. Sorry I can't be of more help, but at least this post will bump yours back to the top.

Will have to have a look at the second link which looks interesting at least its given me something to look at :)

Thanks

---

