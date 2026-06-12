---
title: "Screen on startup - too fast! What does it say?"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by MorrisseyJ on 2010-03-16
I notice when i boot into Ubuntu that a bunch of text flashes on my screen. I am not sure what the text says as it moves too quickly for me to see. 

What i have been able to see is something about drivers (i think) and something like "please read instructions on the website". I have never been able to copy down the address or get much more than that.

Since i thought this might be about downloading proprietary drivers i looked in: System ->  Administration -> Hardware Drivers, and that said: No proprietary drivers are in use on this machine. 

I am not sure if this is telling me that no proprietary drivers are in use on this machine because the other screen i saw on start up was telling me that they could not be run, which would make sense. Or if it was telling me that no proprietary drivers are needed on this machine and thus the screen i saw on start up is referring to something else. 

Regardless, the point remains that i don't know what the screen says and if there are any problems with my drivers. Everything seems to work fine but i would like to know what it is that i am supposed to be reading on this website and if some of my hardware is not working.

Is there a command that i can put into the terminal which would check all my driver stuff that is being checked on startup and does anyone know what screen i am referring to, and what that screen is in turn referring to, or what the website is that it mentions and why i might need to check it?

Info: i am currently running Ubuntu on wubi.

Thanks in advance.

---

### Post by NT4usB on 2010-03-16
iirc, all that is recorded in logs somewhere.
In a terminal:```
dmesg | less
``` and you can arrow down through it.

---

### Post by MorrisseyJ on 2010-03-17
Brilliant, 

thank you very much.

---

### Post by 3rdalbum on 2010-03-17
Often, those messages are meant for distribution developers rather than the end user. If it's meant for the end-user to read, it should print into dmesg.

---

### Post by MorrisseyJ on 2010-03-17
Yes, here are some relevant parts of the readout:

> [    8.713151] lp: driver loaded but no devices found

[   32.384574] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   32.384664] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   32.384748] b43-phy0 ERROR: You must go to
[http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and
download the correct firmware for this driver version. Please
carefully read all instructions on this website.

[   32.822797] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   32.822888] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   32.822972] b43-phy0 ERROR: You must go to
[http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and
download the correct firmware for this driver version. Please
carefully read all instructions on this websiteFrom what i have subsequently read online regarding the lp driver being loaded but no devices being found, it seems that i'll need something to sort my printing ([http://bbs.archlinux.org/viewtopic.php?id=8432](http://bbs.archlinux.org/viewtopic.php?id=8432)). With this in mind i think i might need to post back on here to find out what the following actually means:

> 
If you're using hotplug, then add "alias parport_lowlevel parport_pc" to your modprobe.conf, otherwise just load parport_pc as aias saidIt seems, also, from the ERROR msg that i need to download some proprietary drivers to deal with my wireless function keys.

I am currently on a wubi install and i am likely going to do full dual install this weekend so i'll deal with all this stuff then. That said, if anyone can tell me about adding the alias parport_lowlevel parport_pc, that would be great.

Thanks for the help.

---

