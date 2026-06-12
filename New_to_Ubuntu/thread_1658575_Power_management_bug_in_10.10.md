---
title: "Power management bug in 10.10"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by Guffmeister on 2011-01-02
Hi all,

I have a little problem with the power management in my new install of Ubuntu 10.10 on an eMachines netbook. 

If I unplug my laptop from the mains power, Ubuntu tells me that my battery is critically low, and hibernates, even if it says I've got 100% battery. It sometimes doesn't happen, and sometimes it takes a few minutes before running flat. Sometimes it even shuts down immediately after I unplug. I know it's not a battery issue as I also have XP on dual boot and it works fine.

I've looked online, and found a few links that mention this, but I couldn't understand the solutions, so I was hoping someone could send me a link, or explain how to solve my problem. From what I gathered, the power manager can't read the amount of charge properly, and just shuts down. I'm sure there's a simple solution to this problem by now.

Thanks in advance.

---

### Post by JC Cheloven on 2011-01-02
Well, if gnome-power-manager doesn't work in your system, the most immediate solution is not using it. You can go to System- Preferences- Startup Applications, and uncheck power manager. Then reboot and see if that helps.

Notes: 

- You'll loose some functionality. For example, pressing the power button no longer will popup a menu, but shutdown the system right away. And obviously you will not get notified about you battery status unless you install something else.

- As a replacement, I'd suggest xfce4-power-manager. It's for the XFCE desktop environment but should work in gnome. Simply install it from the repos ```
sudo apt-get install xfce4-power-manager
``` and launch it manually ```
xfce4-power-manager
``` If you're happy with it, add it to your startup applications. 

- Also, I believe conky is able to show (among a million things) the battery status on the screen. You could consider that as well.

- Personal note: For a netbook (did you say it's a netbook, right?) I find [LUbuntu]("http://lubuntu.net/") very nice. It even has a netbook setup to choose at boot time. Unfortunately I think it also has gnome-power-manager by default. The xfce counterpart should work as well though. Also xfce (as in xubuntu) is a nice environment itself.

EDIT: WHAT ABOUT TURNING OFF gnome-power-manager BEFORE UNPLUGING THE CORD? AND RESTART IT AFTERWARDS...

Hope this helps

---

### Post by cheapie on 2011-01-02
This appears to have already been reported as [Bug 531190]("https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190").

---

