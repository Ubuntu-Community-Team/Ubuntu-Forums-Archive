---
title: "X keeps crashing"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by ovid9 on 2009-12-13
Yeah, you've seen me here before.  On my wife's Dell Inspiron 1100 laptop, I gave up on 9.10 and put on 8.04.  Works much better, except X keeps randomly crashing.

When I boot, it goes to a blank screen unless I go to "recovery mode" and reset X, then it boots fine.  

Also, it was just sitting and suddenly the screen when black and X killed itself again.

(I'm working off the assumption that X is what the interface is called in xubuntu.)

I don't even know enough to know what threads to read and maybe fix this?  I looked at one that talked about blank screen on startup, but I got sorta lost.

Or, for simplicities sake should I just try regular Ubuntu on here since I just keep  having nothing but trouble with xubuntu?

---

### Post by overdrank on 2009-12-13
Hi and could you give us some specs on Dell Inspiron 1100, like memory and graphics. You can find the graphics model with the command in the terminal ```
lspci | grep VGA
``` The memory can be found under system, administration, system monitor.
Also have you installed the graphics drivers if any are needed, system, administration, hardware drivers?

---

### Post by ovid9 on 2009-12-13
Graphics:
> 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

It has 1gig ram, 2.0 celeron processor as well.

---

### Post by leprkhn on 2009-12-13
The 'X' in Xubuntu stands for xfce. xfce is the name of the desktop environment it uses (as opposed to GNOME: used by basic ubuntu; and KDE: used by kubuntu. There are others, but I'll digress...); not to be confused with X11 (xorg, x-server) which is the service that serves up your windows. xfce (and GNOME and KDE and the unmentioned others) sits on top of X11... making it pretty, functional, containing most of the tools a person needs to do whatever they do on a desktop/workstation.
On to your issues:
What kind of video card does this box have in it?
Which video driver are you using?
While in recovery mode how are you resetting "X"?

---

### Post by overdrank on 2009-12-13
> **ovid9 said:**
> Graphics:


It has 1gig ram, 2.0 celeron processor as well.

Hardy 8.04 usually works well with the intel graphics. With that amount of memory you may try to increase the amount shared with the intel graphics in bios. You can enter bios on the boot up with the F2 or F12 keys on some models of dell.

---

### Post by ovid9 on 2009-12-13
Thanks overdrank, I might just go that route.  
Now to leprkhn

Here's the full lspci
> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)Not sure the driver I'm using, probably whatever is standard installed with 8.04, i don't recall installing any others.

As to restarting resetting x, i have 3 or 4 options to choose, the bottom one says something like "reset x" and i choose it, it says "overwriting possibly customized" something (sorry, i can't remember and its during startup)  then i choose continue with boot and it works.

Edit:  All that is in recovery mode.  I just hit Esc during boot and go into it.

---

### Post by leprkhn on 2009-12-13
But you can get it to run after this, yes?
Once logged into Xfce you could try reconfiguring X.
From the terminal:
```
sudo /etc/init.d/gdm stop
```
CAUTION: This will kill your window manager. You will be left with nothing but a terminal (so maybe write down the commands you'll be entering before stopping GDM)
Once you're logged back in to the main terminal (this should be text mode only), enter this command:
```
sudo dpkg-reconfigure xserver-xorg
```
Once that's done, restart GDM:
```
sudo /etc/init.d/gdm start
```
That should bring your graphical login back up. Log in and see if everything seems to work. Assuming it all works, restart your computer and see if the issue still exists at boot time.

---

### Post by ovid9 on 2009-12-13
hmm, it all seemed to be going fine til the final command to restart the GUI.  It didn't come back up.

Restarted, didn't come back up.
Restarted, went to recovery mode, clicked "fix xserver" works now.

I think I'll just try going with Ubuntu.  GNOME is supposed to not be quite as lightweight as xfce i think, but, if it works each time that'd be nice.  

Thanks!

---

### Post by leprkhn on 2009-12-13
I think that trying Ububtu is a good idea. GNOME isn't *that* bloated, it should work fine in a Celeron@2Ghz with 1G of RAM.

If it doesn't and you find yourself wanting for something more lightweight, you migfht consider stepping outside of the immediate (ubuntu) family and taking a look at CrunchBang ( [http://crunchbanglinux.org/](http://crunchbanglinux.org/) ).
it's Ubuntu, but with the OpenBox Window Manager and a few custom tools. Very lightweight.

---

### Post by ovid9 on 2009-12-13
If Ubuntu doesn't work well, and I think it will, I might look into that.  This is my wife's laptop, and basically I'm just trying to get it running well enough so she can play her facebook games on it easily.

I really like the look of xubuntu, it just hasn't been playing well with this computer and I'm not anywhere near well versed enough to fiddle with it.  

Thanks again for your input!

---

