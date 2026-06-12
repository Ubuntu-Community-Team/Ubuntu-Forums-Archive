---
title: "Updating Flash/Firefox when running livecd"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by panaceus on 2011-08-03
Total linux newbie, running a powerpc-supporting version of Lucid Lynx off a livecd (because it's the newest version supporting ppc that also fits on a cd).  If I try to update flash and/or firefox while running the livecd (e.g. by clicking through the flash update message on a site like youtube), will it work correctly without overwriting anything on my hard disk?  I don't mind having to redo this every time I run the cd, so long as it works.

I know there was a thread on this earlier about flash, but it wasn't completely clear.

---

### Post by Paddy Landau on 2011-08-03
Everything you do from a Live CD happens in RAM, unless you explicitly state otherwise. So, your hard drive will be safe.

If you use a USB with persistent storage (I recommend at least a 4Gb USB), you won't have to keep doing it because it will save on the USB itself.

---

### Post by thefasterblueone on 2011-08-03
Yes that will work, it won't write anything to your harddrive. It will be stored in memory and deleted when you reboot.And you are right you will have to do that every time the disk is inserted.

---

### Post by panaceus on 2011-08-03
Thanks; that's a relief.  Now as to the particulars of updating flash:

I went to the Adobe install page, chose the 'APT for Ubuntu 10.04+' package, clicked download, clicked ok to use apturl, and yes to enable additional software channel.  It appeared to download the files correctly, but then I got a popup saying 'Package 'adobe-flashplugin' is virtual.  My flash player appears to still be out of date.  Any suggestions?

---

### Post by beew on 2011-08-03
> **panaceus said:**
> Thanks; that's a relief.  Now as to the particulars of updating flash:

I went to the Adobe install page, chose the 'APT for Ubuntu 10.04+' package, clicked download, clicked ok to use apturl, and yes to enable additional software channel.  It appeared to download the files correctly, but then I got a popup saying 'Package 'adobe-flashplugin' is virtual.  My flash player appears to still be out of date.  Any suggestions?


Use a liveusb with persistence instead of a live CD like Paddy Landau said.

Instead of installing flash from Adobe, the easiest way is to use the FireFox flash-aid addon, it keeps track of the latest version, remove conflicting versions and optimizes flash for ubuntu all at once. Just install that to Firefox and run the script.

---

### Post by panaceus on 2011-08-03
Still using the livecd at the moment; will try the usb as soon as I can dig one up.  The Flashaid suggestion really seemed like it was working.  It created and ran a shell script, but when I restarted firefox I got the same out-of-date flash message on youtube.  Before trying flashaid, I also tried installing the ubuntu restricted repository, which is now reading as installed.  Still no dice.

---

### Post by panaceus on 2011-08-03
Ah, so flash doesn't work for powerpc architecture, apparently.  Gnash doesn't seem to work at all, and swfdec + swfdec plugin only gives me a black screen on youtube. Is anyone aware of a newbie-friendly fix?

---

### Post by panaceus on 2011-08-03
FlashVideoReplacer looks promising, but I think it requires the gecko-mediaplayer plugin.  When I reach the ./configure stage of installing the gecko plugin, it tells me I don't have the glib-2.0 pkg, and I'm not sure what that is.  Bit of a rabbit hole.

---

### Post by beew on 2011-08-03
> **panaceus said:**
> FlashVideoReplacer looks promising, but I think it requires the gecko-mediaplayer plugin.  When I reach the ./configure stage of installing the gecko plugin, it tells me I don't have the glib-2.0 pkg, and I'm not sure what that is.  Bit of a rabbit hole.

You can install gecko-mediaplayer from the software centre.

---

