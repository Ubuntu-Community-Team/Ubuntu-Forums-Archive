---
title: "Two graphics cards in Ubuntu 9.10?"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by zukzuk on 2010-03-18
Hello… Ubuntu recent user here.  Got a problem.

Computer: Dell Optiplex GX240.  Old, I know.
RAM: Upgraded to 1gb.  Works fine.
HD 0: 20gb OEM.  Windows XP Pro.  Completely disconnected now.
HD 1: New 40gb, same as OEM.  Ubuntu 9.10.  Connected as HD 0.

TWO graphics cards, with NVIDIA card installed by commercial computer tech:
	Old OEM ATI RAGE 128 PRO Ultra GL in AGP using Ubuntu drivers
	New NVIDIA GeForce 8400 GS in PCI; no drivers installed for Ubuntu HD, but were installed to Windows HD

TWO monitors:
	Envision 9110 22" connected to the ATI
	OEM Dell 1707FPT 17" connected to the NVIDIA

Currently, nearly everything works.  I browse and print wirelessly, I have access to BIOS SETUP, and I have a decent desktop (but no desktop effects - ATI card is not capable).  Video appears on the Envision monitor only.  The old Dell monitor is blank, as you would expect, since the NVIDIA card is not yet active.

Here's the problem:
I'd like to install the proprietary drivers for the PCI NVIDIA card to make it work, get better resolution, and achieve desktop effects, BUT my prior experience when I had the Windows HD connected tell me that ONLY the ATI card can access the Dell splash screen and BIOS SETUP for some reason, and after the Windows boot only the NVIDIA card displays a workable desktop with icons.  So I need the ATI card and it's drivers for Ubuntu.  But if I use System > Administration > Hardware to install the NVIDIA drivers, it will automatically disable the ATI card drivers, leaving me no way to access BIOS SETUP.

I know the NVIDIA card works with the Dell computer, since I've installed the drivers on the Windows HD and adjusted the monitor resolution there.  I know both monitors work, since I can swap them onto the ATI card.  But the BIOS SETUP could never be made to appear on the monitor connected to the NVIDIA card with the Windows HD connected.

This is my second install of Ubuntu on this 40gb HD.  I screwed up the first time and disabled the ATI with BIOS wacky, then couldn't boot Ubuntu or access BIOS SETUP to enable the NVIDIA card as PCI.  BIOS was confused, and resetting BIOS didn't fix it.  The commercial computer tech gained access somehow.

So… in Ubuntu 9.10, how can I either:
	a) install NVIDIA drivers WITHOUT disabling the ATI card, or
	b) install NVIDIA drivers AND access BIOS SETUP with only the NVIDIA card activated?

Searching the forum and googling has yielded nothing appropriate.  Please, no terminal work, unless very explicitly explained as to a total newb.  I've not yet learned the sudo commands.  I'm squirrely now, and only want to try something I completely understand.

Previous forum members have been very helpful.  Thank you in advance.

---

### Post by zukzuk on 2010-03-20
Okay, I got no replies to my previous post, although quite a few people viewed it.  This suggests to me that I'm asking a solution to an unreasonable request.  Allow me to change the question, then.

Question: If I enable the NVIDIA by installing driver 185 (recommended) using System > Administration > Hardware, and therefore can no longer access BIOS SETUP although I can (I hope!) view the desktop, icons, and have enhanced desktop effects, can I later disable the PCI NVIDIA card under System > Administration > Hardware to automatically re-enable the AGP ATI card using Ubuntu drivers to access BIOS SETUP, which I cannot get, for some reason, using the PCI NVIDIA card?

TIA.

---

### Post by zukzuk on 2010-03-21
Okay, I've given up on the NVIDIA PCI card entirely.  I've removed it, and I'm running KK with just the Dell's old ATI AGP 16mb graphics card and the Envision monitor.  I have everything at this point: BIOS SETUP, the Ubuntu desktop (but no effects), and wireless browsing and printing.  I cannot play youtube videos, because the site says I have either javascript disabled (I don't) or I don't have the latest version of Adobe Flash Player (I do).  But my16mb graphics card apparently doesn't meet the minimum 128mb requirement for Flash Player 10.  I know how to fix that.

I've ordered a Dell/ATI Radeon 9200TX VGA AGP 4x graphics card.  This should be a direct plug-in replacement for my ATI RAGE card now installed.  It should allow me to run a 1920x1080 monitor, and it should permit viewing of youtube videos with Adobe Flash Player.  And I won't experience the conflicts I've seen with the NVIDIA PCI card.  Hope springs eternal.

By the way, I learned my Dell GX240 doesn't have on-board graphics.

---

### Post by rwong48 on 2010-03-30
Sorry to see that no one responded.. :)

I just recently got 2x PCI 8400GS with 1DVI+1VGA output each. 1 card 2 outputs is easy with nvidia restricted driver + twinview but 2 cards seems a bit hard. And I've been using Ubuntu/Linux for 3+ years.

If your 8400gs has 2 outputs I would recommend ditching the old ATI entirely and use the NVidia in TwinView like I do (did).

The BIOS/boot process go through your ATI card because the machine decides to put preference on the AGP device, I suppose.

Asking for nvidia and ATI drivers to run at the same time is a bit of a strange request :P most people would recommend avoiding that.

---

### Post by rwong48 on 2010-03-30
double post, server database error - sorry!

---

### Post by 3rdalbum on 2010-03-30
Sorry, I've only just seen your post for the first time.

Why can't you remove the ATI card and just use the Nvidia card? Should have two graphics outputs; if one is DVI and you need VGA for both monitors, just get an adapter and the card will output analog signals out of the DVI.

Trust me, you don't want to use an X9200 or an ATI Rage on Linux. With the ATI card removed, you should see everything, including the BIOS setup screen, through the Nvidia card.

If you really need an ATI card and don't mind having a lesser Linux experience because of it, then PowerColor makes modern ATI cards in AGP. ATI doesn't support the card you said you're going to buy. You'd need a Radeon HD 2600 or above to get official ATI drivers for it.

---

