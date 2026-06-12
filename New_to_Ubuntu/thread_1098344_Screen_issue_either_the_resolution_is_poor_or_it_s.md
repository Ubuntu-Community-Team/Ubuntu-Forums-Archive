---
title: "Screen issue: either the resolution is poor or it simply isn't there"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by apolaustic on 2009-03-16
Hi all,

I'm having two problems in 8.10, which I'm pretty sure are related. The first has to do with my screen resolution. I've read through a lot of other threads on this topic, but none of the solutions I found there (reconfiguring xorg, xrandr, et al.) have worked for me. Moreover, my problem has a fun little twist.

I have a 16" CRT monitor and an Intel graphics controller. My screen resolution is currently set at 832x624. I really dislike this resolution, so I accessed System->Prefernces->Screen Resolution and attempted to change to 1024x768. (This resolution also appears as an option under xrandr.) However, when I select 1024x768 and apply the changes, the resolution appears correct but now the display is confined to ~2/3 of my monitor, aligned at the upper left corner. I've attached a screen shot. I find it interesting that I was able to get the screen shot, actually, because nothing gets cut off when the display is crammed into the corner of the screen, but Ubuntu clearly knows that there's more screen area to take a shot of.

[IMG]http://img8.imageshack.us/img8/5392/wwssmallvers.jpg[/IMG]

The next part of the problem happens when I try to switch back to 832x624, since I want to use more than 2/3 of my screen. As soon I do that the screen goes black (as it usually does when switching between resolutions), but then won't come up again. I've given the monitor time to reboot, turned it off and on, but nothing works and I end up having to force a shut-down. A further odd thing about this is that when the monitor goes blank the power light blinks orange, which is exactly what it does when the monitor is on but the computer is not. The computer was on the whole time, though. I could hear it thrumming. I don't know if that's useful information, but it seemed like it could be.

I also tried switching monitors to see if that would alleviate the issue, but both problems happened when I switched to a new monitor.

Any help that anyone could offer would be really appreciated. Thanks in advance.

---

### Post by kanikilu on 2009-03-17
It sounds like more of a display adapter problem to me, since the problem occurs on more than one monitor.

Do you know what video card your computer has and what driver X is using?

I think you can get the video card information with: ```
lspci | grep VGA
``` and the driver should be listed in your /etc/X11/xorg.conf file.

---

