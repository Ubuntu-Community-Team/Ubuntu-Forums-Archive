---
title: "Numerous questions"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by peteking on 2009-07-12
Hey all.

I've just partitioned my hard drive and installed Ubuntu 9.04 from the Linux Format Ubuntu special. I chose to try out Linux because I was utterly sick of Microsofts ********, and didn't have the money to swap to Mac/OSX. The process went smoothly, but I have quite a few questions to ask!

1. How do I find my drivers? Can I? If so, how do I update them?

2. My Display Configuration goes mental when I try access it. It worked fine when I was tinkering around in the OS, getting used to it, THEN, I asked it to recognise my moniter, it slowed down my computer to a near halt and I had to reboot. Now whenever I try to access it, the window appears blank and my computer slows down again, on the system moniter tool, it says one of my CPU's (intel DG35EC quad core 2.5ghz) is being run at 100%, then switches to a different CPU for a second (straight to 100%) then back again. Every time I try to use Display Configuration I have to reboot, the slowing doesn't go away.

3. The reason I was trying to access Display Configuration was because my usual moniter, a Samsung SyncMaster 225MW stopped working when I booted up Ubuntu, it said (something like) "Not optimal settings, 1600x1200 60hz". The moniter works fine when I boot up windows XP, but doesn't want to work when I use Ubuntu. I'm currently using my old Phillips moniter.

I was trying to access Display Configuration (on the smaller moniter) so I could change the display settings to 1600x1200 60hz and see if my Samsung moniter would work again after I rebooted.

4. Can I transfer some files over (large patches from games, world of warcraft, left4dead etc) so I don't have to download them again? I plan to use WINE to run them.

5. Should I use WINE or keep the extra partition? I'd much prefer to use Ubuntu completely, but if there's no avoiding it then i'll keep XP.

Thanks in advance. When I get to grips with the OS i'll try my best to contribute ^^

---

### Post by camaron1 on 2009-07-12
For No.1 go to Systems>Administration>Hardware drivers and it should be able to tell you if you have any drivers to install. If you do install them. This might solve your problems with your monitor.

Wine has not worked for me, but it has worked for others. You have to try it your self, I think. 

Keep asking, people that know more than me (just about everyone...) will eventually help you.

Good luck

---

### Post by AndThenWhat on 2009-07-12
As I'm sure the monitor problem is the most frustrating, I will try to help you get that fixed. Here is a solution that may help:

```
System -> Preferences -> Startup Applications
```

Then click the "Add" button.

For "Name" just put anything you want ie. "Set Monitor Resolution".

For "Command" put "xrandr --output LVDS --mode 1600x1200". (NOTE: If you know of another resolution your monitor supports you can use that for the 'mode' option)

The "Comment" box is optional..just leave it blank.

After you've entered that info above, click "Add" to add it to the list of startup applications. Then you are going to want to reconnect your other monitor and restart Ubuntu. If you can't even reach the Ubuntu login screen without the resolution error, then when Ubuntu is booting up try pressing CTL+ALT+F1 and login then type "sudo dpkg-reconfigure xserver-xorg" and that process should fix the problems.

That's a lot of info and you might not need it, but I hope it helps.

---

