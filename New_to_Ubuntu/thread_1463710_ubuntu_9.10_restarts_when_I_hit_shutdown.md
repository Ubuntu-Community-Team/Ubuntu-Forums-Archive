---
title: "ubuntu 9.10 restarts when I hit shutdown"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by munnster on 2010-04-27
Please forgive me if this has been solved and I missed it (point me to the thread if you can!)

I am running a dual boot with xp and when I hit shutdown, within 30 seconds my computer is restarting. It used to be if I hit shutdown and didn't wait for the timer (hit the shutdown button in the box to make it faster) it would restart, now it restarts even if I wait for the 60 seconds. I tried  "sudo shutdown -h now" but that didn't work either.  I have two choices in shutting down; I can either hit the power button on the front of my machine or let it reboot into xp and shut down from there.  :confused:

Any suggestions or links for me to read?
Thank you so much for any help!!

---

### Post by Axel-P on 2010-04-27
Any error message? When it boots, after the unwanted reboot, do you get your normal login or a recovery shell? have you tried the shutdown command with the -P option?

Also, it's usually not recommended, but sudo init 0 should shutdown your machine.

---

### Post by munnster on 2010-04-27
The only error message I get is right after I choose Ubuntu (instead of windows)--I get "vga 771 is deprecated use set gfxpayload 800x600x8, 800x600 before linux comes and instead" but I read that that shouldn't be an issue and from the way it sounds isn't related to this(?). Then my desktop comes up (I do not use a password to log in).

I will try sudo shutdown -P and see what happens. Thanks. If that doesn't work, is it better to turn it off by the button on the front of my computer (I have that set to shut down when pressed) or just as bad as using sudo init 0?

---

### Post by Crazedpsyc on 2010-04-27
This happened to me for a while, and so I just used sudo shutdown -h 0 and it worked fine. then the next time I tried to shut down with the normal System>Shut Down it worked fine as well. no idea why though!

---

### Post by munnster on 2010-04-27
sudo shutdown -P now did not work--it started up quicker than using -h now. :(

---

### Post by Axel-P on 2010-05-02
I've never had such issue, so it's kind of hard to help you without any output.
Have you had this problem since you installed 9.10? Have you tried 10.04? If you didn't had this problem just after installing 9.10, when it started? Have you checked the output of dmesg?

Also, if you find some command that will actually shut down your machine take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=856788"), it might help you to change the way your computer shuts down.

---

### Post by Crazedpsyc on 2010-06-17
have you tried using the other options like hibernate and reboot? if they don't work try suspend just to give it a rest for a while. also try sudo shutdown -h 0 or whatever from another virtual console (press ALT+F1. finally try (ONLY FOR EMERGENCY) kill [PID] where PID is the pid of init (hopefully 1) and while you have the ps -A list open, look for any unusual processes, could be some sort of queer malware (is the cpu usage higher than normal? somebody might be using you as part of a zombie net if so).

---

### Post by Kellemora on 2010-06-17
Check your computers BIOS, we have most of our machines set to boot on power-up, so using a software shutdown only creates a cold boot instead of actually shutting off the computer.  After a power outage they all come back on again IF they were ON before the power outage.  If OFF they stay OFF, but this is a function of the bios.

Have you tried a full cold reboot to see if that stops the software from causing a reboot?  Something may have got SET that shouldn't be in the software so it does a warm reboot instead of a shutdown.

TTUL
Gary

---

