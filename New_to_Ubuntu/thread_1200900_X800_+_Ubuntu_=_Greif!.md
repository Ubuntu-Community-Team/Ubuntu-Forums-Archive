---
title: "X800 + Ubuntu = Greif!"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by jimsheep on 2009-06-30
here we go again.

after much agonizing and rebooting and editing xorg.conf and completely removing and replacing fglrx (both the Ubuntu way and the ATI way, according to the howto), i'm about ready to drive over my box with a large, pointy tractor. :evil:

i finally used the recovery-mode boot menu to run xfix and dpkg.  i have a display that works now, but no shiny features.

Intrepid Ibex
AMD 2500+ @ 2420 KHz
2GB RAM
ATI X800 (as stated above)
Asus M8N Deluxe MB
NEC MultiSync LCD1760(i think)

in winblow$ i can run MilkDrop through Winamp at roughly 60fps, but i can't even get glgears to top 30.  the hardware works, but this whole ATI thing...i dunno.  it's frustrating the crap out of me.

---

### Post by Hospadar on 2009-06-30
This is in a desktop I assume?

If you've gone the restricted driver route and also the ati way and couldn't even get a display, it might just be that fglrx just doesn't work on your card.  Some cards from some manufacturers just don't play nice at all with linux.

I'd honestly suggest maybe just getting a different (nvidia) card.  On newegg you can get a low end 7 series for as cheap as 25 bucks.  And you can often get good deals on not-so-bad video cards on craigslist or ebay.  I suspect if you look in the right place you can get your hands on an nvidia card that will play movies and do desktop effects just fine for under $20.  Look for used stuff and whatnot.

Of course the alternative is to locate a super linux nerd and have him or her play with your machine for a while.

---

### Post by jimsheep on 2009-06-30
yup, this is in a desktop.

the kicker is that it worked once before, but i had other **issues** (read: hard disk fail) that meant i had to reinstall.  with the reinstall it never worked again...

---

### Post by jimsheep on 2009-06-30
ok, here's the error message i get:

```
(EE) fglrx(0): Unable to initializePCS database
(EE) fglrx(0): Missing PCS defaults in /etc/ati/amdpcsdb.default
(EE) fglrx(0): preInit failed
(EE) Screen(s) found, but none have a usable configuration
```

and here's my /etc/X11/xorg.conf:

```
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier    "NEC MultiSync LCD1760NX"
	HorizSync     31.5-69
	VertRefresh   56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"NEC MultiSync LCD1760NX"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes "1280x1024_60.00"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```

i've recently attempted to install the driver using [Envy]("https://launchpad.net/envy"), but to no avail.  it's what added the "Module" section and "fglrx" to the "Device" section.

any assistance is greatly desired and appreciated!

---

### Post by jimsheep on 2009-07-02
Bump.

---

### Post by jimsheep on 2009-07-03
bump again! please, i'm pulling my hair out!

---

### Post by snl2587 on 2009-07-03
Have you tried using 8.04? Video card problems are the reason I had to revert twice back to Hardy after trying 8.10 and 9.04...maybe it could work for you as well?

---

### Post by ChaiTan on 2009-07-03
If you are using Ubuntu 9.04, fglrx won't work for any ATI card less than the HD 2000 series. So you have two options either stick with the open source ATI drivers or use Ubuntu 8.04 or 8.10

---

### Post by jimsheep on 2009-07-03
> **ChaiTan said:**
> If you are using Ubuntu 9.04, fglrx won't work for any ATI card less than the HD 2000 series. So you have two options either stick with the open source ATI drivers or use Ubuntu 8.04 or 8.10

i'm already using 8.10.

^^i don't reeally want to go back to 8.04, but if that's the only way to get some kind of decent graphics back without upgrading my hardware...

there's gotta be a better way.

---

