---
title: "blank screen on startup"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by fredfelter on 2009-04-18
I'm ticked!
I upgraded from Hardy to Intrepid a few days ago on my Thinkpad T22. At first things seemed ok but then I began to experience startup problems where on boot-up, after the logo finished loading, the screen would go black and nothing could be done except reboot, sometimes several times. After a google search it became obvious this is a common problem that has been going on for months and, as often happens, there is no consensus as to what can be done. I removed Compiz which seemed to work for a while but now the problem is back. For me this is a show stopper on the use of Ubuntu. Something this serious and prevalent should not be left hanging for so long and for so many users as has been done and the upgrade should not have been offered on the update screen unless it was a stable version. I should never have upgraded as Hardy was working fine. Thank goodness I don't have these kinds of problems with Windows.

---

### Post by Eisenwinter on 2009-04-18
Did you do just an upgrade, or a completely fresh install?

---

### Post by fredfelter on 2009-04-18
> **Eisenwinter said:**
> Did you do just an upgrade, or a completely fresh install?

I did the upgrade as it appeared as an item on the page of the usual update recos.

---

### Post by OneMixDJ on 2009-05-21
Hi Everyone,

I'm having the same problem that fredfelter is experiencing, also with a T22.

I replaced XP on my daughters' laptop with a fresh install of 8.10 (Ibex) and it works great.

However, after the Ubuntu load bar completes, it's a 50/50 chance that the GUI will load. If it doesn't load, then the only way I can get a successful boot is to keep restarting it until if comes around.

Once it's up, everything is perfectly fine.

I first thought that it could possibly be related to a hibernation or power setting, but even after changing settings to never hibernate or power down, that appears to be unrelated.

So, I sure would like to know how to resolve this issue as well...

---

### Post by anewguy on 2009-05-21
When the GUI doesn't come up, try holding down ctrl and alt then pressing F1 and see if a terminal window logon appears.  If so, log on using your normal userid and password.  Once logged on, type:

lspci <press enter>

and

lsusb <press enter>

and copy/paste the output of each back here in a reply.  That way we can see what chipset you are using and if the graphics are integrated in the chipset or you have a separate video adapter.


I know that in 9.04 there are problems with some Intel integrated graphics processors and so far the only help has been to go back to 8.04 or maybe 8.10

Dave :)

---

### Post by OneMixDJ on 2009-05-26
> **anewguy said:**
> When the GUI doesn't come up, try holding down ctrl and alt then pressing F1 and see if a terminal window logon appears.  If so, log on using your normal userid and password.  Once logged on, type:

lspci <press enter>

and

lsusb <press enter>

and copy/paste the output of each back here in a reply.  That way we can see what chipset you are using and if the graphics are integrated in the chipset or you have a separate video adapter.


I know that in 9.04 there are problems with some Intel integrated graphics processors and so far the only help has been to go back to 8.04 or maybe 8.10

Dave :)

Hi anewguy,

I tried your suggestion but nothing happens.

If I had to describe it, it seems that the T22 somehow "freezes" when the GUI is supposedly initializing. Again it takes a reboot or two for me to get the GUI. When the blank screen happens, I have no other alternative but to reboot.

Once rebooted, I ran the "lspci" and "lsusb" commands. Below are the outputs:

administrator@girls:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)
00:03.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 20)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
administrator@girls:~$ lsusb
Bus 001 Device 002: ID 062a:0003 Creative Labs 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
administrator@girls:~$ 

Let me know if you see anything funky. ;)

Thanks!

---

