---
title: "Not a good start - Ubuntu freezes"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by bhallett71 on 2009-12-08
This is my first crack at converting from Windows to Ubuntu. I kinda jumped in with both feet.  Popped in the Live CD and did a clean install...gotta cut the cord.  Everything was going smooth until the first update.  Problems started with a frozen mouse and keyboard.  I would turn off the PC and start over, kinda annoying but no big deal.  Now I am getting the frozen mouse every time I start up.  

Every 5th or 6th time it seems like during the boot, I don't quite make it to the color Ubuntu screen.  I get a terminal looking window that asks for an Ubuntu selection.  There are three options and for every option there is a "recovery mode" option.  I cannot make a selection because my mouse and keyboard do not respond.   I also cannot reboot past this screen.  I have been able to boot from the Live CD, then when I take the CD out, I can again boot all the way and get to the desktop without making any settings changes from the Live CD session.  

What is going on?  I Googled Ubuntu 9.10 freezing, and there were a ton of threads about compix and certain graphics cards not being compatible with Ubuntu 9.10 and that this was a recorded "bug".  Does that mean I should just keep rebooting and using the Live CD as a workaround until a real fix is determined?  

I really like the look and feel of Ubuntu...it drives nice.  Please help if possible.

---

### Post by mikewhatever on 2009-12-08
Have you verified the downloaded iso file for errors and burnt it a lowest speed possible? Can you provide info about you computer.

---

### Post by bhallett71 on 2009-12-09
Sort of... I used a Live CD that several co-workers have used.  The ISO seems to have worked for everyone as far as the install goes.  
 
The PC is pretty old (2000).  It was custom built at a local computer store when I was in college (Kent State University) to take adavantage of all the cheap student edition MS software.
 
I know I have  512MB RAM, AMD XP 1.6 GHZ sinlge core processor.  I have installed generic USB 2.0 card, ethernet card, CD burner, etc.  I have no idea what graphics or sound cards are installed.  Not familar with the terminal window commands.  I need to get a Linux book, or something Ubuntu specific to figure out the commands.   Can anyone give me a few commands to help figure out what the guts of my PC actually are?

---

### Post by ukripper on 2009-12-09
can you try disabling compiz and see if that makes any difference. 

open System-->Preferences-->appearence and then click on Visual Effects tab and check it to "None" and close.

Let us know if it still freezes then we go in details.

and in terminal type below command post output here ```
lspci
```

---

### Post by bhallett71 on 2009-12-09
Thanks for the idea, but my Visual Effects were already set to NONE.  

Here is the output from the terminal window:

hallett@hallett-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0a.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
00:14.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice Modem (Worldwide) (rev 08)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

One other interesting tid-bit is that when I get stuck at the GNU GRUB screen that asks me to select a system I have no response from my keyboard to select recovery mode.  I also cannot select a language or use the function commands at the menu screen for the LIVE CD.  It seems my Keyboard and Mouse do not become functional until I am completely booted up.

---

### Post by coffeecat on 2009-12-09
> **bhallett71 said:**
> 
One other interesting tid-bit is that when I get stuck at the GNU GRUB screen that asks me to select a system I have no response from my keyboard to select recovery mode.  I also cannot select a language or use the function commands at the menu screen for the LIVE CD.  It seems my Keyboard and Mouse do not become functional until I am completely booted up.

Are you using a USB mouse and keyboard? If so, for a machine of that vintage, you need to go into the BIOS and enable USB support to get USB input devices working with grub. Trouble is, you'll need a PS2 keyboard to get into the BIOS in the first place. :wink:

---

### Post by sandyd on 2009-12-09
> **coffeecat said:**
> Are you using a USB mouse and keyboard? If so, for a machine of that vintage, you need to go into the BIOS and enable USB support to get USB input devices working with grub. Trouble is, you'll need a PS2 keyboard to get into the BIOS in the first place. :wink:
the option should be called "legacy usb"
or at least it was called that on my old dell xps

---

### Post by bhallett71 on 2009-12-09
how does one get to the Bios to make that change?

---

### Post by coffeecat on 2009-12-09
> **bhallett71 said:**
> how does one get to the Bios to make that change?

First - plug in a PS2 keyboard!

Second, when the POST screen displays, you have to press a key. Trouble is, the key varies. Sometimes ESC, sometimes DEL, sometimes F2, quite often something else. It might be displayed on screen, something like 'Press *whatever* for setup'. If it's not, you'll have to find out what the motherboard is and do a bit of googling. And, as carlee quite rightly pointed out, the thing you want to enable in BIOS is probably 'legacy USB' support.

---

### Post by bhallett71 on 2009-12-09
Plug in a PS2 keyboard.....brilliant!!!

Thanks to coffeecat, carlee, ukripper, and mikewhatever for all the advice.  As you can tell, I am not much of a hacker when it comes to the PC.  I had a freeze/lock-up on the Ubuntu boot screen with the color graphics today...i don't know what that means.

I am thinking about starting over with V. 9.04 since I am only 2 weeks into this, and all my files are still on an external hard drive.  I guess that will verify whether I am susceptible to the bug I have read about in some other threads.  Unless there is a work around that is known.  The other thread was dated 11/18 and mentioned 22,000 complaints of the bug that freezes the display, mouse, and keyboard.

Note:  I did disable the compiz like ukripper suggested.  No change.

---

### Post by ukripper on 2009-12-10
> **bhallett71 said:**
> Plug in a PS2 keyboard.....brilliant!!!

Thanks to coffeecat, carlee, ukripper, and mikewhatever for all the advice.  As you can tell, I am not much of a hacker when it comes to the PC.  I had a freeze/lock-up on the Ubuntu boot screen with the color graphics today...i don't know what that means.

I am thinking about starting over with V. 9.04 since I am only 2 weeks into this, and all my files are still on an external hard drive.  I guess that will verify whether I am susceptible to the bug I have read about in some other threads.  Unless there is a work around that is known.  The other thread was dated 11/18 and mentioned 22,000 complaints of the bug that freezes the display, mouse, and keyboard.

Note:  I did disable the compiz like ukripper suggested.  No change.

TBH, there had been several bug reported for this kind of freezes where users were using usb based keyboard/mice. One solution was to update BIOS or use usb hub and plug your usb keyboard/mouse in it.

---

