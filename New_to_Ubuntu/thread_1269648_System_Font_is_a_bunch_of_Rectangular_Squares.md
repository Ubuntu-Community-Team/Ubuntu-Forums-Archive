---
title: "System Font is a bunch of Rectangular Squares"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by dbun on 2009-09-18
Hello, I'm relatively new to linux.  I'm having this strange problem that I haven't seen anywhere but here:
[http://ubuntuforums.org/archive/index.php/t-907278.html](http://ubuntuforums.org/archive/index.php/t-907278.html)

However none of the solutions there have worked for me thus far.

The problem is as the title says Square font has replaced almost everything on my desktop environment and also all the programs, such as where the address bar is now I have something like "[][][][][][][][][][][][][][]" except the brackets are really rectangular squares.

The problem started after I installed azureus.  Too many happy clicks to get my torrents downloading. I think it must have been when I was about to choose a language to run in for azureus. I can't remember what it asked.  Removing azureus hasn't done anything for me.  

If anyone can pose a solution that would be so appreciated, it really drives you insane.

Anyhow I'm really loving linux, more so loving fluxbox to death.

---

### Post by LowSky on 2009-09-18
If you cant read anything then navigating to menus is going to be tough, better offf reinstalling

---

### Post by dbun on 2009-09-18
I have a sylvania gnetbook, the thing came with gOS (ubuntu hardy) installed on it.  It doesn't have a disk drive so I can't run any installations through any disks, is there some other way?  Through reinstalling or through the terminal, my terminal works fine.

---

### Post by LowSky on 2009-09-18
got a 1GB USB flash drive?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by dbun on 2009-09-19
I tried installing from a SD Card (I don't have a usb flash drive unfortunately) - but it wasn't working out for me.  Most of what I found on google, has also said its pretty much impossible, grub won't recognise it.

But I've come back with more information, I found out my culprit!
PANGO that *******! I uninstalled Azureus, and reinstalled it, and ran it through the command line.  And here is what I got in the command line:
-----------------------------------------------------------------
(SWT:3735): Pango-WARNING **: failed to choose a font, expect ugly output. engine-type='PangoRenderFc', script='latin'

(SWT:3735): Pango-WARNING **: failed to choose a font, expect ugly output. engine-type='PangoRenderFc', script='common'
DEBUG::Sat Sep 19 03:04:48 EDT 2009  Data Missing /tmp/azupdater_1.8.3.zip

(SWT:3735): Pango-WARNING **: failed to choose a font, expect ugly output. engine-type='PangoRenderFc', script='greek'

(SWT:3735): Pango-WARNING **: failed to choose a font, expect ugly output. engine-type='PangoRenderFc', script='cyrillic'

(SWT:3735): Pango-WARNING **: failed to choose a font, expect ugly output. engine-type='PangoRenderFc', script='hebrew'

(SWT:3735): Pango-WARNING **: failed to choose a font, expect ugly output. engine-type='PangoRenderFc', script='arabic'

(SWT:3735): Pango-WARNING **: failed to choose a font, expect ugly output. engine-type='PangoRenderFc', script='thai'

(SWT:3735): Pango-WARNING **: failed to choose a font, expect ugly output. engine-type='PangoRenderFc', script='han'

(SWT:3735): Pango-WARNING **: failed to choose a font, expect ugly output. engine-type='PangoRenderFc', script='hangul'
-----------------------------------------------------------------
All this crap.  Speaking of which I installed Pango today, because I needed it for something else I failed at installing.  If you know of any thing that could help me out.  I've been able to translate text by throwing it in the web browser, so I am able to maneuver around.

Thanks alot anyways, I thought the reinstallation would be my answer, unfortunately as of yet to my knowledge I can't figure out how.

---

### Post by dbun on 2009-09-19
a lot people have been having the same problem as me.  I finally found the solution, and that was to just remove Pango.  Since I installed it from source, someone said to just use the following commands:

cd /usr/local/lib
sudo rm libpango*

I'm sure I didn't uninstall it correctly!  But I broke it and thats what's working for me and thats what's going to get me to sleep tonight.  That was hell.

---

### Post by venuinu on 2012-11-03
Thanks!i was expecting it is pango lib issue,your fix just worked.

---

