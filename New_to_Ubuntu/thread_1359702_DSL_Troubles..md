---
title: "DSL Troubles."
date: 2009-12-20
forum: New to Ubuntu
---

### Post by Marvin666 on 2009-12-20
DSL the os.
i didn't know where to stick this thread, so I'll put it here.
I'm trying to boot off of a DSL 4.4.10 live cd, but it isn't working right.
It looks like the laptop has 28mb ram, and a 233mhz pentium cpu. It came with 98 and is a dell latitude cp. I think the hard drive is 4gb.
It works fine during the command line section of boot, but when the gui starts it messes up. I can make out windows and see that text is there, but no more. Also the colors are inverted. Anybody know what is going wrong here?

---

### Post by MelDJ on 2009-12-20
maybe Graphic card related

---

### Post by jerrrys on 2009-12-20
sounds like you need video drivers.  wouldnt know hows thats done in dsl

---

### Post by Marvin666 on 2009-12-20
98 works just fine. Never thought I'd say those words...
I'm playing nethack (tiles mode) on it now.
The machine has no modem or ethernet port. I've been burning programs to a cd and moving them that way. It can't boot via usb and 98 dosn't support my U3 flash drive.

---

### Post by jerrrys on 2009-12-20
ok...looks like you dont change drivers.  you need to find out what kind of video you have and see if its compatible 

[http://www.damnsmalllinux.org/wiki/index.php/TinyX](http://www.damnsmalllinux.org/wiki/index.php/TinyX)

---

### Post by Marvin666 on 2009-12-20
98 won't tell me the hardware. Anybody have LIGHT distro recommendations other than DSL?

---

### Post by blackened on 2009-12-20
You can probably solve this using boot options from this page: [http://www.damnsmalllinux.org/wiki/index.php/Cheat_Codes]("http://www.damnsmalllinux.org/wiki/index.php/Cheat_Codes").

Pay special attention to the framebuffer example. I've had good luck using framebuffer mode on really old notebooks (circa Windows 95). A safe setting to start with would be:
```
fb1024x768
```

---

### Post by jerrrys on 2009-12-20
do you have "device Manager" on it?  if you do, look up your video

nevermind

---

### Post by Marvin666 on 2009-12-20
No luck with using cheatcodes to boot it.

---

### Post by blackened on 2009-12-20
> **Marvin666 said:**
> No luck with using cheatcodes to boot it.

Which ones did you try and what is the native resolution of the machine? I'm going to assume it's probably 1024x768. Did you try the lowram boot option? Or the explicit vga modes like vga=792?

---

### Post by diablo75 on 2009-12-20
The word VESA comes to mind... I remember using that driver back in the old days of legacy hardware.  Is there a way to boot using VESA drivers?  (I don't know, just kind of wondering aloud...)

---

### Post by Marvin666 on 2009-12-20
640 by 480, and I also told it it had 28mb of ram.

---

### Post by blackened on 2009-12-21
> **Marvin666 said:**
> 640 by 480, and I also told it it had 28mb of ram.

You're not being very forthcoming with the feedback.

Exactly which options (as in what exactly did you type) did you try and what was the error returned on each attempt?

I would suggest this as a starting point:
```
dsl xmodule=fbdev fb640x480 lowram
```

or maybe
```
dsl xsetup
```

---

### Post by snowpine on 2009-12-21
28mb of ram?!? Christmas is just around the corner... Santa needs a new computer!

---

### Post by Marvin666 on 2009-12-21
I'm getting a new laptop, but intend to use the old one as well. It has a serial and parallel port built in.
The exact cheatcode I used was:
```
dsl mem=28m xmodule=fbdew fb640x480
```I also tried the one you suggested, but still no luck.
No errors returned, just pixelated screen on launch of gui, with inverted colors.

---

### Post by blackened on 2009-12-21
> **Marvin666 said:**
> I'm getting a new laptop, but intend to use the old one as well. It has a serial and parallel port built in.
The exact cheatcode I used was:
```
dsl mem=28m xmodule=fbdew fb640x480
```I also tried the one you suggested, but still no luck.
No errors returned, just pixelated screen on launch of gui, with inverted colors.

Ok then, at least we can be fairly certain that the problem is only in the display. Try this:
```
dsl mem=28M vga=769 xsetup
```

---

### Post by Marvin666 on 2009-12-21
Okay that sorta worked.
When promted i gave it the following options:
-Xfbdev
-non-usb mouse
-no mouse wheel
-ps2 mouse
-2 button mouse
-us keyboard layout
It gives me a gui. It is centered on the screen, with quite a bit of empty space around it, not being used. It is blue on black, with a few red elements. On the desktop i can see that icons are there, but I can't make out any of them. They do have readable labels below though. Also,  I can't read the upper half of the system monitor thing on the right of the desktop.

---

### Post by blackened on 2009-12-23
> **Marvin666 said:**
> Okay that sorta worked.
When promted i gave it the following options:
-Xfbdev
-non-usb mouse
-no mouse wheel
-ps2 mouse
-2 button mouse
-us keyboard layout
It gives me a gui. It is centered on the screen, with quite a bit of empty space around it, not being used. It is blue on black, with a few red elements. On the desktop i can see that icons are there, but I can't make out any of them. They do have readable labels below though. Also,  I can't read the upper half of the system monitor thing on the right of the desktop.

Ok, well that's progress. The poor display quality is because you're probably running at 8 bit color depth.

From what I can glean from the internet, this laptop is capable of 800x600 at 24 bit color depth. That would result in a vga setting of 789. It also has 32MB of RAM with 4MB likely allocated to video. Not sure if explicitly reporting incorrect memory quantity would cause problems or not though. Try this boot line and see how it goes:
```
dsl mem=32M vga=789
```

---

### Post by Marvin666 on 2009-12-24
During the terminal phase of boot, it reports slightly over 28mb, but I messed with 98 and finally got it to spit out the ram, and it said 32mb. The cards  are of an obsolete form factor, and have no markings.
Woo-Hoo! It works. Full color depth, and full screen.

---

### Post by lisati on 2009-12-24
> **snowpine said:**
> 28mb of ram?!? Christmas is just around the corner... Santa needs a new computer!

+1 Can I have one too....?

---

### Post by Marvin666 on 2009-12-24
I believe my cd drive just failed.  Earlier today, I was having problems with it randomly ejecting  and a few reads failing, but now it won'd keep a disc in, and can't read anything. Anybody know were to find a cd drive, and battery for the second laptop in my signature?
EDIT: Drive failure seems to be intermittent in nature. Still need a new one though...

---

### Post by blackened on 2009-12-24
While you could probably find a replacement for the cd-rom on the web, it won't be worth the money.

Remember that the device is ~10 years old and is probably very dirty inside. Get an anti-static strap, take it apart and give it a good compressed air bath. While you're in there, clean the laser lens and drive hub on the cd-rom. There are tutorials on the web.

---

