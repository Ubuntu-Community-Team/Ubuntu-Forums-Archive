---
title: "X Server seemed to bomb"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by CityOflawrence on 2009-02-27
PREAMBLE
-Ubuntu Studio 8.10 Intrepid
-Lame old Gateway
-Pentium 4 Processor
-1 gig (maybe) RAM
-Shares an old CRT monitor with another computer via Belkin switch

I turned on my Ubuntu machine today and pressed the button on the switch that changes which computer uses the screen, and it would not switch. I rebooted, tried again. Nothing. So I unplugged the VGA cable and keyboard from the switch and plugged it directly into the computer.

I booted up my computer and immediately noticed the resolution running at 640x480. That's no good, so I attempted to change the resolution, and the only other option is a lower one. I rebooted.

The next time, the resolution has shrunk again and now I cannot access the applications button to start a terminal, because the button is outside the screen. Thinking it may go back to the way it was previously, I reboot again.

Now the X server fails to start because though it sees the monitor, a driver problem is interfering and it cannot start X.

I would post xorg.conf, but I'm not sure how to open the text in gedit, copy it, and paste it into Lynx.


I greatly appreciate anyone's time and help.

---

### Post by Xiong Chiamiov on 2009-02-27
You can open a run dialog by pressing alt+f2 in gnome.  If X isn't working, you can get to a terminal window by pressing ctrl-alt-f1.

Paste in elinks is ctrl-v.  There are a few different commands for copying text into the clipboard in a terminal, but they depend on your system.

---

