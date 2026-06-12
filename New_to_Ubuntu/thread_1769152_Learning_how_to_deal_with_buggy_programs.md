---
title: "Learning how to deal with buggy programs"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by Haur on 2011-05-27
Hi guys and gals.

So i've had this problem happen to me a couple of times, i'm playing a old might and magic game using wine 1.2.3. and it works pretty good most of the time (It didn't work at all in Windows 7) but sometimes it seems to take down the entire system or maybe it's just the gdm display. 

Anyways the problem i've been having is something like this. If i leave the computer for a ten minutes and the laptop display goes to sleep the screen is just black when i try to resume. I hear the program is still running but i can not get it to quit. I have been solving this issue by opening a virtual terminal and doing ```
ctrl alt sysrq rseiub
``` but that seemed so drastic so i figured out that ```
sudo restart gdm
``` would be a little bit better.

But surely there must be a even better way. Either something like getting to the desktop from the program or a command in terminal that doesn't close all my running programs? So yeah if anybody has a better way i would be really great-full, learning these little things is what makes using ubuntu fun for me :)

Thanks.

---

### Post by wildmanne39 on 2011-05-27
> **Haur said:**
> Hi guys and gals.

So i've had this problem happen to me a couple of times, i'm playing a old might and magic game using wine 1.2.3. and it works pretty good most of the time (It didn't work at all in Windows 7) but sometimes it seems to take down the entire system or maybe it's just the gdm display. 

Anyways the problem i've been having is something like this. If i leave the computer for a ten minutes and the laptop display goes to sleep the screen is just black when i try to resume. I hear the program is still running but i can not get it to quit. I have been solving this issue by opening a virtual terminal and doing ```
ctrl alt sysrq rseiub
``` but that seemed so drastic so i figured out that ```
sudo restart gdm
``` would be a little bit better.

But surely there must be a even better way. Either something like getting to the desktop from the program or a command in terminal that doesn't close all my running programs? So yeah if anybody has a better way i would be really great-full, learning these little things is what makes using ubuntu fun for me :)

Thanks.
Hi,a lot of people are having this problem, but I have not seen a fix, have you tried setting power management where the monitor and the drive do not go to sleep.

---

### Post by Haur on 2011-05-27
Would this be a bug with Wine or just Ubuntu in general?

---

### Post by wildmanne39 on 2011-05-27
> **Haur said:**
> Would this be a bug with Wine or just Ubuntu in general?

Hi, I think it is to do with the monitor going to sleep or  the screen saver coming on, and a lot of people are having trouble with waking there system up from hibernation, I have that problem, but in my case it might be caused by the fact I did not give my setup in swap.

---

### Post by Haur on 2011-05-28
Well i did create a swap space. But this bug doesn't happen to me everytime. ALso the power management is kind of buggy for me, i can not control the monitor brigtness and the display goes to sleep no matter what i set.

---

### Post by wildmanne39 on 2011-05-28
> **Haur said:**
> Well i did create a swap space. But this bug doesn't happen to me everytime. ALso the power management is kind of buggy for me, i can not control the monitor brigtness and the display goes to sleep no matter what i set.
Hi, that sounds like a bug, you can check here to see. [https://launchpad.net/](https://launchpad.net/)

---

