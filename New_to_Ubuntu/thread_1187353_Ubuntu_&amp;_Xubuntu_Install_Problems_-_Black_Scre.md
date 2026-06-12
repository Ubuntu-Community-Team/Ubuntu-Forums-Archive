---
title: "Ubuntu &amp; Xubuntu Install Problems - Black Screen"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by Johan-Steyn on 2009-06-14
Hi All,

I have an Intel P3 desktop pc with 1 GHz processor and 512 mb RAM.

The system previously had Windows XP installed.

I successfully installed Jaunty inside Windows using Wubi. However, it failed to boot every time. Black screen after boot.

The Intel Boot Agent gave me problems, until I figured out to press and hold F1 during POST to get the real boot menu and set the boot priority.

Jaunty 9.04 booted from the livecd but froze to black screen immediately after the initial boot and flash screen loaded.

Xubuntu 8.10 alternate install cd booted correctly and managed to load successfully.

However, after a successful install, THE SAME THING! Boots up load to the splash screen and then the cursor blinking twice and the system freezes up. Black screen only.

I suspect it's a video problem (on-board).

Please help!

Thanks,

JS

---

### Post by gradinaruvasile on 2009-06-14
What are your specs?

In a terminal:

```
lspci
```

Post the output.

---

### Post by Johan-Steyn on 2009-06-14
Hi gradinaruvasile,

I am posting from my laptop. I am currently reinstalling Xubuntu on the mentioned P3 desktop. Will run lspci and post the specs as soon as it is reinstalled (approx 30 min).

*EDIT = Also the PC has an integrated (on board) video. It is set at 1mb (shared) would increasing the aperture size to 8mb or 16mb help??  

Regards,

JS

---

### Post by Johan-Steyn on 2009-06-14
Hi All,

No, unfortunately the Xubuntu re-install did not work.

Initial splash screen with logo and then nothing. Frozen computer, no keyboard lights, no HDD activity, NOTHING!

I have no terminal; nothing! Xubuntu alternate install disk has no recovery options - it just wants to install.

I have been at it all day and I don't know anymore.

Please Help!

Thanks,

JS

---

### Post by gradinaruvasile on 2009-06-14
What model is your mainboard? Or at least what onboard vid card does it have?
U may try booting the live cd with different bios settings for your video card. Maybe u find one that works.

Edit:
Do u should have access to recovery mode booting options? before ubuntu loads.

Press esc while rebooting, the boot menu should appear. Select recovery mode.
If it boots, u will have a list of choices, select root prompt.
type:
```
dpkg-reconfigure -phigh xserver-xorg
nano /etc/X11/xorg.conf
```

find the "device" section
insert the red line:

```
Section "Device"
    Identifier     "wnateverisyourdevice"
    [COLOR="Red"]Driver         "vesa"[/COLOR]

```

ctrl-o
ctrl-x
ctrl-d
resume boot

...

---

### Post by halitech on 2009-06-14
I would probably bump it up to at least 8 meg. Since you are having issues getting Ubuntu to install, boot into windows and give us the info from there on the video card.

---

### Post by Johan-Steyn on 2009-06-14
Hi,

The only installer that will boot is Xubuntu alternate (Jaunty and Intrepid live-cd's only shows the flash screen (logo) and the flashing cursor - nothing else.

I don't have a terminal or any intelligible input option.

Xubuntu alternate will boot, but no recovery choices - just install options.

Short of opening up the box - i don't have any other options.

Regards,

JS

---

### Post by gradinaruvasile on 2009-06-14
> **Johan-Steyn said:**
> Hi,

The only installer that will boot is Xubuntu alternate (Jaunty and Intrepid live-cd's only shows the flash screen (logo) and the flashing cursor - nothing else.

I don't have a terminal or any intelligible input option.

Xubuntu alternate will boot, but no recovery choices - just install options.

Short of opening up the box - i don't have any other options.

Regards,

JS

Can u actually install it from the beginning to the end?
Because after that u may try the recovery options i said earlier...

---

### Post by Johan-Steyn on 2009-06-14
Hi halitech,

Appreciate the reply.

Will do, (windows suggestion) but it will take a while - as I need to reinstall WINDOZE first, see :( - bummer)

Will post back!

Regards,

JS

---

### Post by halitech on 2009-06-14
ok, thought you were doing a dual boot with it. Is it a home built system or from a company like dell?

---

### Post by gradinaruvasile on 2009-06-14
If u can, install that version of ubuntu that worked before (u said u installedit) and boot with a recovery option.

---

### Post by Johan-Steyn on 2009-06-14
Hi All,

halitech

> ok, thought you were doing a dual boot with it. Is it a home built system or from a company like dell?It's an intel p3 bought at Matrix Warehouse (SA computer supplier), store bought but probably custom assembled. I am reinstalling windows as we speak and will do a system information check and post that info.

gradinaruvasile

> If u can, install that version of ubuntu that worked before (u said u installed it) and boot with a recovery option.Xubuntu does initially boot and install (text based installer) but does not actually run - just a black screen - nothing else. The alternate install cd when booted does not have any recovery options - just an install menu.

No joy from Intrepid or Jaunty live cd - unless you count the brief wubi joy I had when I ran it inside windows.

Regards,

JS

---

### Post by gradinaruvasile on 2009-06-14
Ok... 
So u install from the text based installer. Works. 
When u reboot the computer after that (removed the cd), u should have 3 choices in the boot menu:
normal (not named like this, but thats the idea)
recovery
memtest

Correct?

---

### Post by Johan-Steyn on 2009-06-14
Hi gradinaruvasile,

Thanks for the response.

> Ok... 
So u install from the text based installer. Works. 
When u reboot the computer after that (removed the cd), u should have 3 choices in the boot menu:
normal (not named like this, but thats the idea)
recovery
memtest

Correct?

I  have actually commenced with windows XP reinstall. As soon as it's done, I will reattempt to dual boot with Xubuntu.

Will check and post back.

Regards,

JS

---

### Post by Johan-Steyn on 2009-06-14
Hi All,

Attached please find the print screen (in XP) of the computer specs.

It has an Intel 82815 Graphics (on-board) installed.

Are there any known issues with this controller resulting in the black screen of death, after the install?

Your assistance is highly appreciated.

Regards,


JS

---

### Post by halitech on 2009-06-14
look here after you get ubuntu re-installed. Alot of people have had trouble with the intel chipset (I was guessing between intel and sis). It is instructions for a sony laptop but will work the same for you on your desktop.

[http://ubuntuforums.org/showthread.php?t=998642#postmenu_6489466](http://ubuntuforums.org/showthread.php?t=998642#postmenu_6489466)

---

### Post by Johan-Steyn on 2009-06-14
Hi halitech,

Thanks for the reply and the thread post.

Unfortunately my problem is worse that low screen resolutions. I have no interface to type anything. After Xubuntu log and flash screen, I have a frozen black screen. No ability to type any code.

I saw at least one other post in the forums with a similar problem.

[http://ubuntuforums.org/showthread.php?t=1141597](http://ubuntuforums.org/showthread.php?t=1141597)

This is from maclinux

>  				 				**Black screen right after loading** 			
 			 			 		   		 		 		Video Adapter Intel(R) 82815 Graphics Controller (Microsoft Corporation) (32 MB)
3D Accelerator Intel i752 

Intrepid or Jaunty.

I was able to upgrade from 8.04 to 8.1 and to 9.04. It was a pain. Why? Because the live cd wont mount the video. It loads up and goes straight into a black screen with no prompt or nothing else.

I even tried to install via the alternate CD but with similar lack or results, which tells me it is a conflict with the onboard video, which never happened with previous versions of ubuntu, the latest 8.04.

I've posted similar situations before, but the help I got was assuming that I would get a pitch black monitor with a prompt. It is not the case. It just hides after loading, period. Something just does not mount. It happens with the live CD which is symptomatic that something is lacking.

I would like some help on this one.  Trust me, if I have to reinstall ubuntu again I rather do it straight from the jaunty CD.

By the way, even though I cannot mount the video card with the latest kernel 2.6.28-11, it works with 2.6.24-23.


Video Adapter Intel(R) 82815 Graphics Controller (Microsoft Corporation) (32 MB)
3D Accelerator Intel i752


I really am stuck.

Thanks,

JS

---

### Post by halitech on 2009-06-15
try hitting CTRL + ALT + F1 and see if you can get to a text login screen. if you can then try ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` hopefully that will reset the xserver and then you can do the manual configuration.

---

### Post by gradinaruvasile on 2009-06-15
Dont think that would help. It does the same thing that ubuntu did configuring at first time...

---

### Post by Johan-Steyn on 2009-06-15
Hi halitech,

I did as you suggested and hit ctrl + alt + F1 as soon as the splash screen loaded and lo-and-behold the text login screen.

I watched the different loaders running followed by an OK.

And as soon as it got to **Loading** **ubiquity** ....... Crash! System lockup and freeze.

Any ideas?

*EDIT: PS. I installed a spare Nvidia 64mb AGp graphics card and selected it as primary video in BIOS. Same result. Crashes gloriously as soon as it loads!

Regards,

JS

---

### Post by Johan-Steyn on 2009-06-16
Hi All,

Finally! Solved!

Managed to get Ubuntu Jaunty installed!

It was hardware issues. Installed Nvidia 64 mb AGP graphics card. Pulled out the HDD and slotted in another one, and viola!  Ubuntu installer not only runs - but installs flawlessly!

Also, apparently windows XP has no qualms about formatting a faulty HDD (with hidden flaws) with NTFS and install on it - data integrity issues aside.

Also although Ubuntu minimum graphical requirements is VGA it is preferential to have something larger than a 1mb on board graphics card.

Thanks to gradinaruvasile and halitech for your sound advice!

Kind Regards,

Johan Steyn

---

