---
title: "Problems installing Ubuntu 10.10 on an old Dell 2350 machine."
date: 2011-02-14
forum: New to Ubuntu
---

### Post by NewLinuxUser2 on 2011-02-14
[COLOR=black][FONT=Verdana]Dell [/FONT][/COLOR][FONT=Verdana]**[COLOR=#ff0000]Dimension[/COLOR]**[/FONT][COLOR=black][FONT=Verdana] [/FONT][/COLOR][FONT=Verdana][COLOR=#ff0000]**2350**[/COLOR][/FONT]
[FONT=Verdana][COLOR=#ff0000]**1gig of Ram**[/COLOR][/FONT]
[FONT=Verdana][COLOR=#ff0000]**1.8 Ghz P4**[/COLOR][/FONT]
[FONT=Verdana][COLOR=#ff0000]**40gb H.D.**[/COLOR][/FONT]
[FONT=Verdana]**[COLOR=#ff0000]Nvidia GeForce4 MX 4000 128mb PCI [/COLOR]**[/FONT][COLOR=black][FONT=Verdana]

I have been running Windows XP on them for years with no problem. Trying to run Ubuntu 10.04 LTS. –Extremely new to Linux – [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]
With the graphics card installed the system will not boot to the Ubuntu 10.10 CD, the system hangs when displaying the Ubuntu logo with the colour-changing dots. I was able to install Ubuntu through Windows. However on reboot it boots into BusyBox.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I tried disabling the graphics cards in BIOS to no avail and then succeeded with the install by removing the card completely. I was then able to install Ubuntu 10.04 using the onboard video. I shutdown and re-installed the graphics card and Ubuntu again will not boot.  So I have stopped trying to use the card, even though this card has Linux drivers.  Without the card Ubuntu boots both from the CD and the H.D. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Then I installed an Encore ENLWI-G 802.11g PCI wireless card with the Realtek chipset. This card is supposed to have native drivers in Ubuntu.  Ubuntu will not boot with this card installed. The PC boots to the Ubuntu splash screen which then turns a solid green and after several minutes the PC powers down.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Both this wireless card and the graphics card work fine on the Windows XP side. I have run hardware diagnostics and get no errors.  As said XP works fine other than slower than cold molasses.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have since added both of these cards to on old Gateway select 1100 with a Athlon 1.1 and 384 mb of ram. Ubuntu installed perfectly and was able to immediately use both cards.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]However, I’d really like to get this working on the Dimension to take advantage of the 1 gig of ram and the P4.

Any advice on how to get Ubuntu working on a Dimension 2350 would be welcome.[/FONT][/COLOR]**[COLOR=red][FONT=Verdana][/FONT][/COLOR]**

---

### Post by cariboo on 2011-02-14
When you are at the inital Live CD boot screen press the space bar to get to the menu, select your language, then press F6, select nomodeset from the menu and press esc, the press enter to continue. This will start the live CD in safe graphics mode, which should allow you to complete the installation.

---

