---
title: "Dell Inspiron 6400: intel 4965 AGN problem"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by pytiwari on 2007-05-21
Hi,

I have recently started using Ubuntu (7.06 server addition). My laptop has intel 4965AGN wireless adapter. I used ndiswrapper to get the wireless card working following a previous thread (link).

I am able to install ndiswrapper and the windows driver for the wireless card. However when I try to load the ndiswrapper module using

>>> modprobe ndiswrpaper

surprisingly system reboots moment I hit enter. I am not sure what is the problem. I will highly appreciate any help on this as I am desperately looking forward to get my wireless card working under linux.

Pradeep

---

### Post by chili555 on 2007-05-22
See post #8 here: [http://ubuntuforums.org/showthread.php?t=396204](http://ubuntuforums.org/showthread.php?t=396204)

I suggest you *sudo nano /etc/modules* to add a new line:```
ndiswrapper
```Save and close nano. Shut down your computer and turn off the wireless switch. Start, and after you are logged in, turn on the wireless switch. Did your wireless spring to life?

---

### Post by pytiwari on 2007-05-23
Hi,

First of all, thank a lot for your reply.  I tried adding 'ndiswrapper' to modules. But it did not work and result it kind of same. Whenever I tried to load the ndiswrapper module from terminal, the system either rebooted or the screen kept scrolling quickly (and hence unreadable) with some garbage. 
After adding ndiswrapper to modules, same thing happened and I was unable to boot the system. I had to boot the system using Ubuntu CD in recovery mode and delete the ndiswrapper from modules .

I was able to get the main lines of the garbage that appears when I try to load ndiswrapper.

[PHP][ 11.94000] BUG: unable to handle kernel paging request [  11.94000] BUG: unable to handle kernel paging request [11.94000] kernel tried to execute NX-protected page - exploit attempt? (uid: 0)
[11.94000] printing eip:
[11.9400] BUG: unable to handle kernel paging request [  11.94000] *pde = 0048e027
[11.9400] BUG: unable to handle kernel paging request at virtual address c01045c0
[11.94000] printing eip:
[11.94000] *pde = 0048e027
[11.94000] *pde = 00000000[/PHP]

I will appreciate if you can help me with this.

Pradeep

---

### Post by pytiwari on 2007-05-23
One more thing, I did turn off my wireless card before restarting the system. I am a bit confused about one thing, do I have to keep the wireless switch on when I install windows driver using ndiswrapper?
 i.e. when I execute

ndiswrapper -i NETw4x32.INF
ndiswrapper -m

I never saw the green light for wireless glowing under linux. When I press (fn+f2), all I see is blue light for Bluetooth turning on and off. 

Pradeep

---

### Post by pytiwari on 2007-05-24
Hi all,

I got it working finally. Just posting it in case this helps someone.
I removed ndiswrapper which I installed using apt-get.
Then I used Automatix to install ndiswrapper which also creates a menu item under System>Administration>Windows Wireless Drivers. I used this graphical utility to install inf file. Next, I hit (fn+f2) and bingo!!, the green light is on.

I know this sounds weired as automatix does almost the same thing we do on terminal, but hey who cares as long as I get it working.

Thanks anyways. I do appreciate help from everyone on this forum.

---

### Post by mikledet on 2007-06-11
I know its been a while since you wrote this thread, but if you're still around or if anyone else knows, can you please explain how to do the installation using the Automatix (step by step), since I tried it before and it didn't work, so I'd appreciate a good walkthrough.

---

