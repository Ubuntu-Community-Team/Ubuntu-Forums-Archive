---
title: "emualtion video games"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by mickeyjoe on 2010-01-13
I'd like to know about emulating old style video game systems like c-64 and such on Ubuntu.  I use to do it on my Mac and download roms and such from a website called emulation.net but see it doesn't look like it's the same website anymore.  I still have a couple old gamepad pro usb controllers too.  I'd love to emulate the old c64 or other older video game systems and download some old roms.

---

### Post by ajmorris on 2010-01-13
hi there,
here's a site for c64 emulation software for use on *nix.
[http://www.zophar.net/linux/c64.html](http://www.zophar.net/linux/c64.html)

If you're looking for old system emulators for linux, you can also get emulators for things like NES, nintendo 64 etc.


AJ

---

### Post by cyqotiq on 2010-01-13
In the Ubuntu Software Center, under the Games category, there are a few programs that you may be interested in.  For the quick-and-dirty, just go into the Ubuntu Software Center and click on "Games", then search for "Emulator" to get the full listing.

Of particular note are:
FCE Ultra - NES emulator
GFCE Ultra Emulator - The front-end for FCE Ultra targeted to GNOME
ZSNES Emulator - Super Nintendo emulator
Mupen64Plus - N64 Emulator
Yabause - Sega Saturn Emulator

and my personal favorite...
DOSBox - A light-weight x86 emulator capable of running old school DOS programs and games.  Theoretically, you should be able to install Windows 3.x on this thing, though I've never tried.

(Edit - 13 Jan 2010 0712 GMT)
If you're specifically looking for C-64 or C-128 (or even VIC-20) emulators, there's an excellent emulator that will emulate all three of these machines called VICE (VIC Emulator, as the C-64 and C-128 machines were built on top of the VIC-20 designs).  You can find it at [viceteam.org]("http://www.viceteam.org#download").  NOTE the "Linux" topic under the "Related Sources" section that follows the "Downloads" section.  You will need the CBM4Linux kernel driver (including the OpenCBM library), FFMPEG codec, and the Gnome2/Gtk2 patch in order to get it running.  Optionally, if you're looking for quick-and-easy, you can download the MS-DOS version and run it on top of DOSBox.  It's not exactly an elegant solution, but given the clock speed of the 6510 microprocessor is a whopping 1 Mhz, I'd say it would serve its purpose.

---

