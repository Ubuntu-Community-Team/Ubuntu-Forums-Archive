---
title: "Wireless breaks without gdm"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by buggi22 on 2009-08-30
Hi All,

I have been trying to experiment with a "pure" command-line interface, with no X running at all.  I got the impression that it was necessary to disable gdm on startup to accomplish this.  After digging around, I was able to bypass gdm by commenting out a line in my /etc/event.d/gdm file.

However, when I start up in this way, I can no longer access my WPA wireless network (only temporarily, though -- I can uncomment the same line, or run `sudo /etc/init.d/gdm start`, and it goes into GNOME and works perfectly).

What I'd like to know is, what exactly does gdm do during its startup process that enables wireless?  (Also, it would be nice to know whether I'm "disabling" gdm in the correct way.)

Potentially relevant: My hardware is a Dell Mini 12 (with a Belmont something-or-other wireless card), and I'm running Ubuntu 8.04. (Also, I think NetworkManager runs by default, but I'm not sure if it would be easier to try to bypass that, too...)

Here's what I've found so far:

First, I noticed that when booting up without the gdm event.d script enabled, the wireless driver "wl" does not appear in lsmod.  (I found the name of the driver by running `nm-tool` while connected to my wireless in GNOME.)  I got a wireless interface "eth1" to appear after running `sudo modprobe wl`, but it still doesn't seem to find any wireless networks (via nm-tool).

I've done a lot of blind experimentation with modprobe, wpa_supplicant, ifconfig, and iwconfig, but none of it seems to enable the wireless to detect networks.  A few times, I happened to get wireless networks to show up in nm-tool, but I'm not sure what combination of commands caused this change.  And on top of that, it still wasn't able to connect via WPA.   It seems like there are too many options for me to try all of them one-by-one and restart each time.  :(

Instead of my prior approach, I feel it would be a lot more efficient (and educational) to find out how gdm/GNOME is enabling wireless -- and whether that's possible to replicate purely from the console.

So, I've made some progress towards answering this question, but I still haven't found the actual code that gdm runs in order to get wireless working. I'm actually less interested in a solution to the wireless problem than I am in learning how to diagnose it and trace the sequence of execution during startup. (As they say -- give a man a fish, and he eats for a day...)

Any help would be much appreciated.  Thanks!

---

### Post by tgeer43 on 2009-08-30
> Also, it would be nice to know whether I'm "disabling" gdm in the correct way.I don't know if the method you are using is detrimental in any way but it's certainly not the 'correct' way. That file doesn't even exist on all installations.

There's more than one 'correct' way but for my money the simplest way is to just uncheck it's entry in the Services applet under the Administration menu.

tgeer

---

### Post by buggi22 on 2009-08-31
Strangely enough, the gdm entry is already unchecked on my machine, and I don't remember disabling it.  As far as I can tell, the event.d script, by default, was the only thing starting gdm.

To go on a bit of a tangential rant... I've found that this is one of the more frustrating things about Linux... there are so many ways that different programs can and do configure themselves that you never know where to look for a setting.  And programs are almost never as self-documenting (at least w.r.t. configuration) as an open-source program can and should be.  GNOME is particularly bad about this -- there are dozens of fancy GUI settings dialog boxes, but in cases like these, they can become totally out of sync with the "true" underlying configuration.  Anyway...  </rant>

---

