---
title: "Need Higher Resolution with SIS 661/741/760 PCI/AGP or 662/761Gx"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by aimwin on 2010-05-03
Conclusion, from ordinary user, not expert, but it works for my system.
**********
I found Ubuntu's and other Linux's SIS VGA drivers can produce as high resolutions as MS Windows.
But they are not as smart in detecting monitors.
------------------------------------------------
Ubuntu and may be all Linux?, at least Fedora 12 too,
have routine to check the monitor, while it is loading, almost every time.

If it failed to detect that monitor to be suitable for their best VGA drivers,

It will load the resolution that it think it will work best for your monitor,
which may be wrong, and that is why you get lower resolution.

=============================== How to == start here == This is for Desktop only == ============================
OS Ubuntu 10.04 30/04/2010 "fresh installed", as well as Ubuntu 9.04

This is not a fixed solution to Ubuntu 10.04 nor Ubuntu 9.04
But Method 1.2 is permanent fix for 10.04 for my system.

Just offer another way to get your higher resolution you want.
============================================================
My system is

Asus MOTHERBOARD P4S800-MX SE desktop which has
Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
PCI bridge(s) Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)

I used "good OLD" Pacard Bell monitor
other brands of monitors may be applied?, hopefully, please let us know your experience too.

I cannot get better resolution than 960 X 600
==================================================

Problems solved with
*********************

Method 1.1
**********
(permanent work around) with out doing anything to Ubuntu 10.04 and 9.04
***********************
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/530554/comments/10](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/530554/comments/10)

I change my monitor, to Samsung SyncMaster 913v

Then everything work perfect, 
the maximum resolution is 1280x1024(5:4)

You should try other brand of monitors and see if it works better.
==================================================================
If you don't have other free monitors available,
then this is not a good solution,
but just to let people know another easier work around it.
==============================================================


Method 1.2 --- If your case is the same as mine in Ubuntu 10.04 Lucid 29/4/2010
*********************************************************************
Permanent fix for me 
on Packard Bell with 1280 x 1024 but with 0 HZ though.
----------
But you have to modify Ubuntu 10.04
**********
I found that there is no /etc/X11/xorg.conf

But there is /etc/X11/xorg.conf.failsafe

I created the /etc/X11/xorg.conf from /etc/X11/xorg.conf.failsafe,
using the following ways.

open Terminal,
To open Terminal you click on Application> Accessories > Terminal
---------------------
and copy and paste the following command in the Terminal
------------------
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
---------------------------
after press enter you will be asked for your login password
Key in your pass word and the file should be copy automatically.
--------------------------------
just reboot your computer you should have higher resolution.
-----------

My copy of my xorg.conf is at the end of this section,

Please notice,"Driver" is "vesa" by defualt in /etc/X11/xorg.conf.failsafe

I try to change to "sis", I found I got even higher resolution than "vesa"
as high as my XP (my dual boot with very high resolution)
But after reboot the second time it will go back to low resolution as before(900 X 600).

So I change it back to "vesa" and it work fine.
----------------------------
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

==============================================================


Method 2.1  -- no modification of Ubuntu, only work around.
**********

1. After power up. At GNU GRUB menu, 
       choose "recovery mode" choice, (the one under the normal defualt boot).

2. Wait until it load the new menu, 
    scroll down to pick the choice load with "FailsafeX", don't press enter yet, go to step 3.
----- some of my ubuntu computers will not have this choice 
----if you do not have "FailsafeX" then go to Method 2.2-----
 
3. >>>> very important >>>> turn your monitor's POWER "off",
(why having motitor POWER off- this force OS not to detect monitor,
so it will use default high resolution of the SIS VGA card)
(your monitor must be that high resolution too, otherwise you got garbage)
==> and many times it works with out turning off monitors at this stage.

4. then press enter key, and wait for two minutes or so.
5. turn on the monitor, hopefully you should see the mouse pointer smaller than before (means higher resolution).
 
6. just press "ok" to accept "Low graphic Mode"
7. then next screen, choose "reconfigure graphic",then "OK".
8. choose "create new configuration", then "OK"
9. when if flick back to old screen, this time, choose "cancel".
10. choose "restartX" and "OK"

Ubuntu should start in higher resolution.

11. When you want to power on ubuntu next time

>>>> "I HAVE TO LEAVE MONITOR POWER OFF" 
until Ubuntu has fully loaded 2-4 minutes depend on your hardware, then turn on your monitor.

TODAY I have high resolution every time, when I turn on my computer WITH POWER OFF MONITOR, at begining. 
--------------------------------------------------------------------------------------------
If you failed to do so, start step 1 again. 
(It happened to me every time when I forget to turn monitor's power off at the begining.)
--------------------------------------------------------------------------------------------------------

Method 2.2 ---- only when you first install from Live CD.---
**********
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/530554/comments/9](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/530554/comments/9)

Used only Live CD 
and have your monitor turn off while it is loading.
----------------------
I load LiveCD ubuntu 10.04 release 29/04/2010
with MONITOR turning OFF.
After it stop (no blinking on any led) I turn on the monitor,
choose "Try Ubuntu without installation"
>>>> then imediatly turn off MONITOR'S POWER.
WAIT TILL all LED stop blinking, which mean IT fully loaded.

Turn on the monitor, then I got high resolution, I hope you got it too.
-----------------------------------------------------------------------
Then choose installation to Harddisk. When finished, remove your Live CD,
Then shut down.
---------------
===> Power on to boot from installed harddisk Ubuntu,
While leave your "MONITOR POWER OFF".
(why having motitor POWER off - forcing OS not to detect monitor,
so it will use default high resolution of the SIS VGA card)

After it finished loading 2-4 minutes.
Turn on the monitor, you should get high resolution.

I lost high resolution if I left my monitor's power on when power on the computer.

So I have to do Method 2.1 to get back high resolution.
======================================================

---

