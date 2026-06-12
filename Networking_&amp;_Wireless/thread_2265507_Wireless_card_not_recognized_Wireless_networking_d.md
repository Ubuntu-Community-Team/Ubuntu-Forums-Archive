---
title: "Wireless card not recognized? Wireless networking disabled mysteriously?"
date: 2015-02-15
forum: Networking &amp; Wireless
---

### Post by jthiesen on 2015-02-15
I"m running Ubuntu 14.04 from a usb flash drive on a Compaq Presario C700 laptop. The wireless card is a Broadcom 4311. When I look at System Settings --> Software & Updates --> Additional Drivers, it says it's using the Broadcomm 802.11 Linux STA drivers from bcmwl-kernel-source. But there's no sign of any wireless functionality. The network menu shows only the wired connection.

The laptop has a push button that toggles red or blue to toggle the wireless. When I'm running Ubuntu, the button stays red no matter what. When I run Windows, it goes blue and wireless works fine.

Wired networking works in Ubuntu on this laptop.

I'm pretty much ready to conclude that Ubuntu is not capable of running wireless, at least on this hardware. Is this correct?

I"m relatively new to Ubuntu and it really surprises me that Ubuntu is so user-unfriendly on such a basic function as wireless connectivity.:mad:

---

### Post by westie457 on 2015-02-15
[COLOR=#000000]Hijthiesen.
The BCM4311 chip does work.

The usual routine for the BCM4311 driver goes something like this. [/COLOR]
[COLOR=#000000]With a temporary wired connection run the following.[/COLOR][COLOR=#000000]
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install --reinstall firmware-b43-installer b43-fwcutter
sudo modprobe -rfv b43
sudo modprobe b43
```[/COLOR]
[COLOR=#000000]You can safely ignore all errors and warnings. The last command should return to a blank line with no output.[/COLOR]
[COLOR=#000000]Unplug the cable and check for wireless networks.[/COLOR]

[COLOR=#000000]Let us know what happens.[/COLOR]

---

### Post by jthiesen on 2015-02-15
The last line sudo modprobe b43 seems to have locked up everything. It didn't return a shell prompt. No cursor, no response to mouse or to keyboard.

Is running from a usb flash drive the problem. I would that would be like any other hard drive, just slower.

---

### Post by westie457 on 2015-02-17
Apologies for not getting back sooner.

I have never had that problem happen with the 4311 chip, difficult to say what caused it. Running from a flash drive is slower and probably not the problem.
It could be caused by a memory glitch or it could be a graphics card issue. Or something else entirely.

Suggest you try again with the live Desktop using the same commands.
If you set the USB stick with persistence (remembers settings) or you try the full install we should be able to troubleshoot this issue to a satisfory conclusion.

Let us know what you want to do.

---

### Post by jthiesen on 2015-02-17
How do I set persistence on the usb stick?

---

### Post by jthiesen on 2015-02-17
I tried again and got the same result--complete lock up.

---

