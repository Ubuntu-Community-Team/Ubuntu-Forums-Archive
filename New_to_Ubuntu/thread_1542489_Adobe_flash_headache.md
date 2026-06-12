---
title: "Adobe flash headache"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by rauchster on 2010-07-30
After my system that had been running Vista x64 Ultimate for years crashed and died, I re-used the components and rebuilt into a new Ubuntu Linux OS.

But, my experience so far has been abysmal. I will admit, I'm a relative Linux newbie, but I've been a computer technician for 5+ years so my technical know-how basics are there.

After installing Ubuntu 10.04 x64 version, I haven't had much luck getting many things to run, but the biggest headache of all is Adobe Flash. There are tons of different version out there for Linux and just as many installation methods. But everyone of them fails at some point or another.

I'm pretty sure right now, I have snippets of mismatched Flash players on the system, as everything Flash glitches out as soon as it appears on the page. Most of the time, it acts like I'm clicking everywhere on everything within the applet at about 100 clicks per second.

What I would like to do is figure out how to remove every piece of Flash from the system, and actually get a fully working Flash player running.

System Specs: (if it makes a difference)
ASUS M4A79 Motherboard
AMD Phenom II X4 940 Proc
8GB OCZ Reaper RAM
ATI Radeon 58xx Series Gfx Card
Dual 2TB HDD's (One OS, other backup)
Ubuntu 10.04 64-bit edition

---

### Post by clhsharky on 2010-07-30
rauchster

lovinglinux flash-aid
[http://flash-aid-extension.blogspot.com/](http://flash-aid-extension.blogspot.com/)

This should remove old or incorrect flash and install latest Adobe flash.

Sharky

---

### Post by baddnady23 on 2010-07-30
Go into synoptic and search for flash and remove it.  64 bit for is buggy and has security holes in it.  Using this technique, I have had great results with it.

[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/")

I was linked to this through the flash installation page at [http://psychocats.net/ubuntu/index.php]("http://psychocats.net/ubuntu/index.php")

Hope this helps

---

### Post by gandaran on 2010-07-30
your problem is due to the 32-bits adobe flash plugin from the ubuntu repositories doesn't work well in your 64-bits system, it does work for most ubuntu 64-bits users but some experience problems like you.
you will have to wait till adobe releases the 64-bits plugin or try  to get the only old 64-bits plugin adobe ever released, adobe removed this version because of security issues.

---

### Post by rauchster on 2010-07-30
Wish I had found that link a lot earlier.... things appear to be working at a minimal level now.
However, things are all running very slowly in every Flash applet. It takes about 5-10 clicks for a single click to register, and the video is glitchy and laggy.
I've just installed the newest Linux drivers and ATI Catalyst Control Center for my video card, so it shouldn't be that.
I disabled Hardware acceleration in the settings menu within the applet, and also turned up the storage in case it was out of room.

Ideas?

---

### Post by clhsharky on 2010-07-30
rauchster

Some more help

[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

[http://firefox-tutorials.blogspot.com/](http://firefox-tutorials.blogspot.com/) 

sharky

---

### Post by sandyd on 2010-07-30
> **rauchster said:**
> Wish I had found that link a lot earlier.... things appear to be working at a minimal level now.
However, things are all running very slowly in every Flash applet. It takes about 5-10 clicks for a single click to register, and the video is glitchy and laggy.
I've just installed the newest Linux drivers and ATI Catalyst Control Center for my video card, so it shouldn't be that.
I disabled Hardware acceleration in the settings menu within the applet, and also turned up the storage in case it was out of room.

Ideas?
```

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```add right before the last line in the file(on a new line)
```

export GDK_NATIVE_WINDOWS=1

```[s]and can you navigate to 'about:config' in your firefox address bar and copy and paste the output.[/s]

If you still have problems after adding that line, install 
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

on firefox and give it a try

---

### Post by theozzlives on 2010-07-30
You know, after 3 years of Ubuntu, I just do:
```
sudo apt-get install ubuntu-restricted-extras
```
and it installs Flash, Java, and several codecs and fonts. NEVER failed me

---

### Post by linux18 on 2010-07-30
FLASH-AID
++++++++1
it works 100,000%
get it, get it, get it














I'm laughing so much typing this
but seriously, get flash aid

---

### Post by rauchster on 2010-07-30
Alright flash is working for the most part. Thank you everybody for your help.

I have one final question concerning this issue. Typically there is one flash applet that i zoom in so it's nearly fullscreen (Using Ctrl+ in Firefox). At normal size it runs smoothly, but zoomed in it becomes almost unusable due to framerate being very inconsistent.

Instead of a smooth scrolling action, it jitters and stutters.

---

### Post by soldier1st on 2010-08-03
flash aid is helpful but in my opinion not needed as the restricted extras installs flash and other stuff and that will do and flash is buggy but that is not linux's fault it is adobe's and don't expect adobe to fix it or release a fixed 64bit version anytime soon as they love to keep you waiting and drag these things on for years. if they were smart they would dump flash and instead help and push HTML5 or fix flash's issues and make it modular so the issues it has would be fixed but i doubt adobe will do any of that.

---

### Post by beew on 2010-08-03
Anyone try using Gnash with any luck ? I played with in a bit in a live usb (x32)and nothing seems to work on youtube. 

On another note, I wouldn't get a x64 machine at this point. Too many compatibility issues, probably most of my software will stop working.

---

