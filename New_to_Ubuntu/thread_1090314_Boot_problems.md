---
title: "Boot problems"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by bitrocker on 2009-03-08
Hi,

I am running a dual boot system with Kubuntu (8.10) and WinXP. Kubuntu is installed inside Windows. Everything was fine, till i run some calculations over night. When I wanted to continue in the morning, my system didn`t respond (guess the programm still run). I choosed the rough (and wrong way) to shutdown my laptop manually (pressing the power button).

Now, when I boot, I see the login screen. When I enter my password, the screen flashs (as if the system wants to start) but then the login box appears again.

I can login via console, but when I say 
```
startkde
```
I get an error message... something about the DISPLAY...

Anyone knows what I can do?

---

### Post by didac on 2009-03-08
Can you post the text of the error message? It will help

---

### Post by kansasnoob on 2009-03-08
Since you say:

> Kubuntu is installed inside Windows. Everything was fine, till i run some calculations over night. When I wanted to continue in the morning, my system didn`t respond (guess the programm still run). I choosed the rough (and wrong way) to shutdown my laptop manually (pressing the power button).

The "installed inside Windows" bit makes me think Wubi! And this part, "pressing the power button", really worries me because of this:

> 
Any gotcha?

Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


[http://wubi.sourceforge.net/faq.php](http://wubi.sourceforge.net/faq.php)

That was my main reason for running away from Wubi!

I've found an actual dual-boot to be much more preferable:

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by bitrocker on 2009-03-09
Hello,

kansasnoob, what you say doesn`t sound too good :( Well, the error message when I say ```
startkde
``` from the console is
```
$DISPLAY is not set or cannot connect to the X server.
```

Maybe this helps?

---

### Post by didac on 2009-03-09
Try startx instead.

Post as an attachment the file /var/log/Xorg.0.log

or read it yourself to see what you discover. The problem will be at the end, maybe.

---

### Post by bitrocker on 2009-03-11
startx causes some messages, wich didn`t really help me(was a bit much to post it).

I wanted to copy /var/log/Xorg.0.log to a hd wich I can access out of Windows. Usually my primary hd is mounted under /media, but when I log in via console, it is not there. So I didn`t find a way to access the file. What can I do?

---

### Post by bitrocker on 2009-05-02
Till now I couldn`t find a way to access /var/log/Xorg.0.log. I tryed to install an editor, that I can use from the console, but saying

```
sudo apt-get install joe
```

didn`t work. So any suggestions, how I can have a look at the Xserver log file. Or any other ideas, how to fix my system?

Hope someone knows what to do - dont`want to reinstall...

---

