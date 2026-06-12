---
title: "Virus"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by bigal1932flying on 2010-06-25
I am sure that I have a virus on my Lucid Lynx.
I have installed Avast Antivirus but when I try to update it I receive the following message:
"An error occurred in avast!engine:Invalid argument
deleted stale stock file'/home/afrancis/.avast/lockfile-afrancis
An error occurred in Avast!engine:Invalid argument"
Any idea how to fix this problem or remove the virus another way?

---

### Post by proggy on 2010-06-25
Gee i didn't even know Avast had a Linux anti-virus but i doubt you have a virus , did you use a Debian package from here? [http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4)

---

### Post by snkiz on 2010-06-26
Despite your assurance that you have a virus. It maybe a good idea to list some symptoms your having, what you have done recently (downloads, updates, installs...) and any processes you believe suspicious, before you run out and install a bunch of software you don't know how to use.

As for your error, what exactly you did to produce the error would be helpful.

---

### Post by bodhi.zazen on 2010-06-26
I do not know how to fix Avast, you might contact them directly as they are a third party application.

What makes you so sure you have a virus. In theory it is possible, but it is extremely rare.

Linux is not windows and most problems are not due to viruses.

---

### Post by snkiz on 2010-06-26
I was going to say that, but you never know... I have yet to see a security measure anywhere that can effectively prevent social engineering attacks, short of unplugging from the web.

---

### Post by wilee-nilee on 2010-06-26
It is a easy fix look through this forum the avast forum post six has the terminal command.
[http://forum.avast.com/index.php?topic=57812.0](http://forum.avast.com/index.php?topic=57812.0)

It is not a virus that it is keeping it from working.

---

### Post by bigal1932flying on 2010-06-26
Tried the command "sudo sysctl -w kernel.shmmax=128000000
kernel.shmmax = 128000000" as suggested on the website. Avast is now running will see what happens.
THANKS.

---

### Post by wilee-nilee on 2010-06-26
> **bigal1932flying said:**
> Tried the command "sudo sysctl -w kernel.shmmax=128000000
kernel.shmmax = 128000000" as suggested on the website. Avast is now running will see what happens.
THANKS.

There was a thread on this today where dcstar gave the instruction on having that command run on reboots. If you reboot you lose the reset that the command gives you. But it is a easy command to just save if you can't find the thread.

---

### Post by yetiman64 on 2010-06-26
My avast install fix (I use it here)

```
gksudo gedit /etc/sysctl.d/60_AvastFix.conf
```Add in the contents,

> 
#
# Fix to allow Avast4workstation to download and install updates correctly.
#

kernel.shmmax=100000000Save the file and reboot, the fix will take effect on the next boot. To have the fix take effect immediately **without** rebooting use

```
sudo service procps start
```No virus likely to be present but a problem with the Ubuntu kernel.shmmax variable (Avast's virus database is too big for the default value).

The stale lock file occurs as a result of this error and the crashing of Avast, once again not a virus behaviour.

Once you do this, update Avast and use as normal. Cheers.

---

### Post by wilee-nilee on 2010-06-26
> **yetiman64 said:**
> My avast install fix (I use it here)

```
gksudo gedit /etc/sysctl.d/60_AvastFix.conf
```Add in the contents,

Save the file and reboot, the fix will take effect on the next boot. To have the fix take effect immediately without rebooting use

```
sudo service procps start
```No virus present but a problem with the Ubuntu kernel.shmmax variable (Avast's virus database is to big for the default value).

The stale lock file occurs as a result of this error and the crashing of Avast, once again not a virus behaviour.

Once you do this update Avast and use as normal. Cheers.

Yay:p Thats the one.

---

### Post by stmiller on 2010-06-26
The solution is to remove Avast. 

:)

---

### Post by bigal1932flying on 2010-06-26
Well Avast is working and says no virus found.
The reason I thought I had a Virus or some sort of Malware was some strange looking pop-ups which first appeared when I logged onto Facebook and then other sites.
The last application I installed was Shotwell Photo Manager and then after that I installed a number of updates.
Over the last few days something strange happens when I shutdown. The screen goes black as usual but then multi coloured arcs appear in the lower left hand corner of the screen and then a blue screen appears with lines of text the first line reads:
"Broadcast message from root@afrancis-desktop"
This screen then goes and the computer shuts down.
Hope this will mean something to someone.

---

### Post by carlinhawaii on 2013-01-28
:)Thank you yetiman64. Your fix works perfectly.

> **yetiman64 said:**
> My avast install fix (I use it here)

```
gksudo gedit /etc/sysctl.d/60_AvastFix.conf
```Add in the contents,

Save the file and reboot, the fix will take effect on the next boot. To have the fix take effect immediately **without** rebooting use

```
sudo service procps start
```No virus likely to be present but a problem with the Ubuntu kernel.shmmax variable (Avast's virus database is too big for the default value).

The stale lock file occurs as a result of this error and the crashing of Avast, once again not a virus behaviour.

Once you do this, update Avast and use as normal. Cheers.

---

### Post by lisati on 2013-01-28
> **carlinhawaii said:**
> :)Thank you yetiman64. Your fix works perfectly.

From the forum code of conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

