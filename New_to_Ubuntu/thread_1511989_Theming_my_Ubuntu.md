---
title: "Theming my Ubuntu"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by adobrakic on 2010-06-17
Alright, I need some help making my Ubuntu look even more sexy than it already is. I know, I know, my post count says I should already know how to do this, but 95% of those posts are from my old computer's Ubuntu, and not my newer, absolutely awesometackular computer that can handle compiz and emerald and gtk and ****. 

Some background info:
Ubuntu 10.04 64bit

lspci:
```
ado@ado-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GS] (rev a1)
07:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
09:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
ado@ado-laptop:~$ 

```

glxgears:
```
ado@ado-laptop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
11579 frames in 5.0 seconds
11611 frames in 5.0 seconds
11667 frames in 5.0 seconds
11657 frames in 5.0 seconds
11884 frames in 5.0 seconds
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 42 requests (42 known processed) with 0 events remaining.
ado@ado-laptop:~$ 

```
*Note: the error is just from me closing the gears box.*



I already know where to get themes and all that, I'm just not sure how compiz and emerald work together. I also get that compiz animates my Ubuntu, emerald themes my windows, and gtk themes everything else. Someone please correct me if I'm wrong.

Say I want to install this [theme](http://gnome-look.org/content/show.php/Glassified+MacOS?content=125896), which says its a compiz theme but only has a emerald download, not sure what's up with that. Downloaded it anyway, loaded it up in emerald, and then nothing happened. 

Also, should I find GTK 2.x themes as well, or should emerald and compiz cover most of everything?

Also 1.1, is there a way to disable compiz while in full-screen video or while playing video games? Thanks!


--edit--
Okay, I've figured out how to apply themes in Emerald:

```
emerald --replace
``` 
in terminal, but once I close terminal, it goes away. Should I add that code as a startup item?

---

### Post by QIII on 2010-06-17
Emerald is dying a horrible death.  I don't know if it is worth your time and effort.  (After reading several articles suggesting Emerald's possible demise and the fact that it currently does not play well with Lucid because of the more recent version of X, I confirmed that there are problems with the Emerald Theme manager, at least for me.)

You can control Compiz/Metacity in two ways.

For a graphical method, you can install Compiz Fusion Icon.  Put it on your panel.  Left click it.  A new icon will appear on your panel.  Right click that one and you can choose between Compiz and Metacity.

I run Metacity when running VLC and I get no video tearing at all.

Alternatively, you can use the terminal.

```
compiz --replace
```switches you to Compiz.

```
metacity --replace
```switches you to metacity

---

### Post by adobrakic on 2010-06-18
Damn, that's kind of a let-down. Finally I get a machine that can run Emerald, and it's no longer as supported as it once was. Oh well, nothing that can't be worked around. Hopefully they'll still update to be more compatible with newer versions of Linux, it makes windows so pretty.

Is it recommended to switch to Metacity when playing games? For example, I like to play Urban Terror a lot, and even though I don't really notice any lag and my FPS stays above 120+, I feel like I should still switch it off.

---

### Post by QIII on 2010-06-18
I don't know if I would say "not supported" necessarily.  I'd say "not keeping up."  That's a fairly effective way to die.

I don't game, so I really couldn't tell you whether to use Metacity for that.  I do know that Compiz sometimes presents problems when using things like VLC, so I switch to Metacity when the foster kids want to watch movies on my computer.

---

