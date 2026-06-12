---
title: "Display suddenly looks . . . off"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by litlfrog on 2009-03-12
Hmm, one problem solved, another crops up. I needed to see how a webpage looked under different screen resolutions. I went to System -> Preferences -> Screen Resolution and dropped down from 1152x864 to 1024x768. The resolution seemed to change correctly, but a pink box with the word "unknown" in it appeared at the top left hand corner. When I tried to change back, I was able to select 1152x864 in the drop-down menu, but clicking Apply did nothing. I restarted the computer and it looks like the resolution changed back, but things look different. A lot of things are gray that didn't used to be (for instance, the autocomplete address bar in Firefox) and there are these chunky gray bars in a couple of places on the panels. It looks like something went wrong when I tried to switch resolution, but what?

---

### Post by dwasifar on 2009-03-12
If I understand this correctly, you came back from a resolution change without your Metacity appearance choices working properly.  I bet buttons and tabs changed shape too, right?

Log out and log back in, so as to start a new X session.  If that doesn't work, try rebooting.  If it STILL doesn't work, then post information about your video hardware.

---

### Post by litlfrog on 2009-03-12
Huh, weird. The first restart didn't fix the problem, but on the second restart everything looks like it's back to normal. Never mind, I guess.

---

### Post by High Camp on 2009-03-12
Mine did the same thing the other day. I tried rotating my screen (who doesn't?) and when I rotated back everything was fuzzy and "off". I was working in the sun so I though maybe it was just my eyes. When I rebooted of course I had come in from the sun and everything looked normal again. I'm glad to know I'm not loosing my vision.

---

### Post by litlfrog on 2009-03-17
> **dwasifar said:**
> If I understand this correctly, you came back from a resolution change without your Metacity appearance choices working properly.  I bet buttons and tabs changed shape too, right?

Log out and log back in, so as to start a new X session.  If that doesn't work, try rebooting.  If it STILL doesn't work, then post information about your video hardware.

The problem went away for a while, but it seems to have come back. Sometimes it will even happen if I come back from lunch to find that the system is hibernating, but when I move the mouse I get an error message. I'm ashamed to say that I don't remember what it says, but it asked me something about wanting to change the configuration, etc. So, how do I post information about my video hardware? This is a work computer and I don't know what hardware it has installed.

---

### Post by litlfrog on 2009-03-18
Bumped for great justice. I can't figure out why this problem will sometimes come up when I start the computer, then go away with a restart

---

### Post by Kareeser on 2009-03-18
Can you post the contents of the file /etc/X11/xorg.conf?

---

### Post by litlfrog on 2009-03-19
> **Kareeser said:**
> Can you post the contents of the file /etc/X11/xorg.conf?

Wow, this looks pretty dang minimal. :)

> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by 123456789123456789123456 on 2009-03-19
I can't be sure.  Perhaps someone will know more, to any one who posted to this thread.  Sounds like Ubuntu somehow lost all infomration about the video device, and switched to a default driver.  One that is not fully compatable with the Video card.  My version did the same thing when I installed it, because that version of Ubuntu back then, did not have the drivers for my video card.  The default driver worked, but I was limited on my screen resolution, and I could not use any animation.

---

### Post by litlfrog on 2009-03-19
OK, if xorg.conf doesn't list it, how do I find out what the video card is?

---

### Post by litlfrog on 2009-03-19
After some searching, I found out how to discover my card: S3 Inc. ProSavage KM133. The driver was already installed, but I used Synaptic to reinstall it. How do I now tell Ubuntu to use that driver?

---

### Post by litlfrog on 2009-03-21
Bump. I've never worked with video card drivers on Ubuntu before; what do I need to do to configure the computer to use the correct driver if it doesn't appear in that conf file?

---

