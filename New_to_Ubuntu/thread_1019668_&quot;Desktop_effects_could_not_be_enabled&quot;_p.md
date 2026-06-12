---
title: "&quot;Desktop effects could not be enabled&quot; problem in 8.10"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by wittrura on 2008-12-23
Hi all, I am a new user to Ubuntu and am loving it so far.  The forums have been so much help to me and any issue I've had just took a few minutes to search on here to solve.

I recently tried to hook my laptop up to my LCD TV just to see how it would look, but when I switched back to using only my laptop monitor I have had a few issues.

The first is that every time I restart, the icons in the panel are moved to spaced-out locations and are no longer adjacent.  The log-out icon is in the middle of the top bar, and my volume control and time icons are also all over the place.

In addition to this, I was having issues when ctrl+alt switching between virtual desktops.  When I tried to enable desktop effects which I found were enabled, I got the error message as stated in the title.

I appreciate any help, and let me know if there is any more information you need.  The thing that confuses me is that everything was fine before connecting and disconnecting my TV.

---

### Post by Kareeser on 2008-12-23
Sounds like your xorg.conf was altered... compiz can't start because something is preventing it, like a changed setting. (I'm guessing a virtual screen that's too large, but I have no clue).

Can you open the file "xorg.conf" in "/etc/X11" and post it here?

As for your first issue with the icons... I have no clue...

---

### Post by Titan8990 on 2008-12-23
Whenever you upgrade to a new kernel, you have reinstall your restricted drivers.

Have you upgraded your kernel without reinstalling the drivers?

---

### Post by wittrura on 2008-12-23
> **Kareeser said:**
> Sounds like your xorg.conf was altered... compiz can't start because something is preventing it, like a changed setting. (I'm guessing a virtual screen that's too large, but I have no clue).

Can you open the file "xorg.conf" in "/etc/X11" and post it here?

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2704 1072
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by Titan8990 on 2008-12-23
You don't have any drivers configured.


report the following:


lspci -v | grep -i vga

---

### Post by wittrura on 2008-12-23
Thanks all for your help.

I tried hardware testing once and nothing happened, but after giving it a second try everything is working fine.

Thanks again.

---

### Post by onoj on 2008-12-25
I seem to be having the same issues; compiz worked -> tried second monitor -> compiz doesnt work. My xorg.conf is similar to that above with the 'virtual' display setting, how would i go about reverting to my old xorg.conf? (i've checked /etc/X11, and while there are what looks like auto backups, they are all very similar to the current one, and none mention the intel driver which I believe I was using previously.) 

many thanks!

---

### Post by andresmh on 2009-01-04
I have the exact same issue. It would be great to get an answer! :)
Since these thread hasn't got much attention I posted my specific case (including my xorg.conf) here: [http://ubuntuforums.org/showthread.php?p=6491288#post6491288](http://ubuntuforums.org/showthread.php?p=6491288#post6491288)

---

