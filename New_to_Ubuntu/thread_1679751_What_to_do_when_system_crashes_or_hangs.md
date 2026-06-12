---
title: "What to do when system crashes or hangs?"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by New00Folder on 2011-02-01
My system apparently crashed today. All I had was a cursor and a pointer which won't move. I was running 3 things:

1> Rhythmbox. It stuck and kept on repeating a few words (i'm on my own). There was nothing wrong with the song after restart.

2> Firefox. I was trying to sign in to a website when the crash occured. Later on restart it turned out that I couldn't sign in using my e-mail ID but the other option of signing in using facebook worked.

3> Sakis3G. I use it to connect to the internet using USB modem.

Any ideas about what could have gone wrong?

I didn't know what to do so I powered off using the power button and booted-up again.
What should have I done?

I was under the impression that when something went wrong I could press ctrl+alt+f1 to get a terminal. But it didn't work. What should I do when something similar happens again?

---

### Post by 45acp on 2011-02-01
My Maverick system also hard locks occasionally. I'm not sure what's causing it. It appears to happen only with the latest kernals. It doesn't seem to happen with the older -22 kernal (I think) which I have gone back to using.

---

### Post by sydbat on 2011-02-01
As 45acp suggests, use the previous kernel and see if that helps.

Also, if your box freezes, do this - hold down "Alt+SysRq" and type "REISUB". This should reboot a non-responsive Linux box in a safe manner. If this does not work (as in, it does nothing at all), you might have bigger problems like hardware beginning to fail.

---

### Post by New00Folder on 2011-02-02
Thanks sydbat and 45acp.

I don't think I'd ever find out if using older kernels helped because this thing happens very rarely (twice during the 1 year I've used Ubuntu) while I've had at least 7-8 kernel upgrades. I would definitely try  "Alt+SysRq" if it happens again, though.

---

### Post by chazzerthehorse on 2011-02-11
Hey guy's. Am new to ubuntu, And i am also having issues where ubuntu hangs up.
It goes to the blackscreen with a flashing cursor etc etc.. The same as everyone else.
It mainly happens when i am on fire fox.
And the only solution is to turn it off. I know that this is a bad bad thing, Especially as i have only just got a new hdd.

I will try the "alt+sysrq+ next time (ive also tried most of the other general keyboard short cuts to no joy)

When i turn my machine off. i may have to restart it many times before grub will load
(using windows + linux ubuntu 10.10)
Q, Is grub not loading a sign that my HDD is about to die?
Q, Is there any keyboard short cut to invoke grub?
Q, Has anyone found a successful permenant solution to this problem?

Any help would be apprieciated greatly..:D

---

### Post by New00Folder on 2011-02-11
@chazzerthehorse: Apparently there is something wrong with 10.10 which has linux 2.6.35.25 kernel. It crashes easily when processor usage is high. For example trying to play a video while re-encoding it from .ogm to .mkv causes the system to crash. Rhythmbox is also erratic; closing the window will sometimes cause it to quit and sometimes not.

I can't say for sure whether reverting to older kernels is a solution as I never tried the video thing in older versions. But till date 10.10 has crashed thrice (in less than 2 months) while with older versions system crashed only once in about 11 months. So you might give it a shot.

And alt+sys req doesn't work.

I am not having any trouble with grub at all.

---

### Post by chazzerthehorse on 2011-02-17
Hey there. Thanks for the response..

I fear that my ubuntu is crashing due to my PC overheating.
And maybe not the kernel issue that many many people are suffering from.
I have removed the cover an stuck my air-con on full (it's 36degree's in here)  as Both the HDD's were quite warm
and checked the seating of all leads etc while i was there.
So it could be a fluke of fate or increased ventillation..
But Ubuntu have been on now for a few hours with rythem box, fire-fox, thunderbird, etc
running fine without a glitch..
I'll leave it on for the night and check it.
I'll post back with the verdict. As it may be helpful to others to check this out first.
Fingers crossed! ;)

---

### Post by chazzerthehorse on 2011-02-17
Hey dude, thanks for the response.. ALT+PRTSC +REISUB worked fine.
Having over heating prob, think i ve have it sorted now. 
CHEERS AGAIN

---

### Post by New00Folder on 2011-02-19
One more thread about the same problem

[http://ubuntuforums.org/showthread.php?t=1678185&highlight=usb+modem+lan](http://ubuntuforums.org/showthread.php?t=1678185&highlight=usb+modem+lan)

And a more detailed answer to the question which is the subject of this thread

[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

EDIT:

Sys rq key needs to be turned on.

Add a line
```
kernel.sysrq=1
```
in /etc/sysctl.conf

It will be on after reboot. You can crosscheck by
```
cat /proc/sys/kernel/sysrq
```Output should be 1.

---

