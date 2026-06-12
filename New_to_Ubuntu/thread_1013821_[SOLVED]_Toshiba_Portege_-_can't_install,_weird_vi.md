---
title: "[SOLVED] Toshiba Portege - can't install, weird video issue - I think!"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Sour Mash on 2008-12-17
First post and jumping in with a difficult to explain thing.

Little back ground - new to Linux, installed Ubuntu on an IBM T40 Laptop, like it a lot and thought Linux would be good to resurrect some old hardware and give it to the kids as all they want to do it a bit of email, web surfing and music playing.

The IBM laptop experience was 100% easy, no issues whatsoever and Ubuntu even recognised onboard wifi that Windows XP never recognised!

So I jump in with my old Toshiba Portege 7140 with 192 MB of RAM (the max apparently). Now this machine runs XP, a little slow but it runs.

Install of ubuntu, xubuntu, kubuntu does not go well (yep I don't really know what I'm doing but what's to lose?)

I noticed a BIOS message so I upgraded to the BIOS to the most up to date (didn't make a difference, still see the BIOS message - BIOS is too old)

The Live CD seems to start up OK and I select language etc. I've tried several distros and tried installing it through Windows (strangely this got me the furthest)

Essentially the install either hangs with a blank screen and a flashing cursor (you can't type anything that appears though) or with xubuntu I actually get further and arrive at a scrambles screen, one half is black with fleck and the other is white with flecks - it's like the view you get when you change screen resolution to something the display can't handle on a windows machine.

All I'm looking to do is to get something running that will be able to work OK on the hardware.

Am I trying to do the impossible or use the wrong flavour of Linux? What else can I tell you to help?

Thanks

---

### Post by Sam Lars on 2008-12-17
You should try the Alternate install CD from [here]("http://www.ubuntu.com/getubuntu/downloadmirrors").
Do you see the screen with the logo and the progress bar?  Do you get to where you have a mouse pointer or the install window?  How far does it go?

---

### Post by Michael.Godawski on 2008-12-17
hey, 

ubuntu needs 384 MB of system memory (ram) to run the live cd, the very minimum is 64 MB with the alternate text-based installation.

The requirements for Xubuntu are:

Xubuntu 				
[LIST]
[*]Minimum
[LIST]
[*]166 MHz processor
[*]64 MB of system memory (RAM)
[*]At least 1.5 GB of disk space
[*]VGA graphics card
[/LIST]
 						
[*]Recommended
[LIST]
[*]300 MHz processor
[*]256 MB of system memory (RAM)
[*]8 GB of disk space
[*]Graphics card capable of 800x600 resolution
[/LIST]
[/LIST]
so I would try the alternate Xubuntu installer.

---

### Post by Sour Mash on 2008-12-20
> **Sam Lars said:**
> You should try the Alternate install CD from [here]("http://www.ubuntu.com/getubuntu/downloadmirrors").
Do you see the screen with the logo and the progress bar?  Do you get to where you have a mouse pointer or the install window?  How far does it go?

Been away for a few days, thanks for the suggestions, I'm downloading the alternative now and we'll see where it takes me :-)

---

### Post by Sour Mash on 2008-12-20
Well I have acquired the alternative iso, burnt a CD and it's installing now - seems to be going OK, no weirdness, screen shows "sensible" activity :-)

---

### Post by gn2 on 2008-12-20
I recently retired a similar spec Portege 3440CT, with 192mb RAM Ubuntu is just too much, Xubuntu was better.

Zenwalk is also well worth a try.

---

### Post by Sour Mash on 2008-12-20
> **gn2 said:**
> I recently retired a similar spec Portege 3440CT, with 192mb RAM Ubuntu is just too much, Xubuntu was better.

Zenwalk is also well worth a try.

I tried Xubuntu with no different result :-( Granted I didn't try an "alternative" as I have with ubuntu but as that install has just completed and is no better, I may try Xubuntu again!

Updat on the ubuntu alternative install - it all went really well until the very end when it all hung on setting the time server (sorry can't remember the exact point it stalled) one reboot later and it appears to load up ok then screen goes black, blinking cursor and nothing more - system just hangs there!

What distro should I try with Xubuntu please?

---

### Post by Sour Mash on 2008-12-21
OK, here we go this morning with Xubuntu and the Alternative install.

I'm not sure if it makes a difference and if it does I'm not sure what to do anyway but all these attempts at installing come up with an early warning about an old BIOS and "ACPI" requiring "ACPI = FORCE" command. There's no opportunity to put a command in at this point and I have no idea (yet) what ACPI is let along why I need to coerce it into something it doesn't want to do voluntarily. Whilst I let this laptop churn it's way through another install routine is there anything I should know about ACPI and it's reluctance to play?

Thanks

---

### Post by gn2 on 2008-12-21
[This should explain ACPI]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface").

If Xubuntu has been installed, press e at the Grub screen when the laptop starts and append ```
acpi=force
``` to the boot entry by typing it in.

If it hasn't been installed yet, when the CD gives the initial list of options press F6 and enter ```
acpi=force
``` then start the installer.

There are a variety of these additional boot parameters to try, irqpoll, noapic, nolapic, vga=###, xforcevesa, etc.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Sour Mash on 2008-12-21
Thanks for that, quite technical but I get the gist of what it is and why it might be an issue :-)

The Xubuntu alt install is going slowly but so far so good!

---

### Post by Sour Mash on 2008-12-21
OK, here's the latest from Sour Mash HQ - it doesn't work :-( During the install I get an error message "Installation Step Failed" this is the select and install software stage.

I feel like I'm stumbling around in the dark and getting nowhere, any words of comfort available?


Update - also fails at "Build LTSP chroot" - I think it may be time to give up with Xubuntu alternative and try something else :-(

---

### Post by Sour Mash on 2008-12-22
Not sure if you've lost interest in my quest yet but here's the latest.
In an idle moment I thought I would check the integrity of the CDs I've been using, guess what? Both the Xubuntu CDs I'd burnt failed the check :-( So I deleted those iso's and downloaded again from a different source, I've burnt a new one and it's passed the check (I'm also trying the 8.04.1 Xubuntu alt desktop version).

So, I start the install and press F6 as suggested, I add "acpi=force" at the end of the text that pops up but then the next thing that appears on the screen is the same warning that the BIOS fails the date cutoff and acpi=force is required - is this right?

---

### Post by Sour Mash on 2008-12-22
This is pretty soul destroying - I've been through it all again from scratch, downloaded, burnt and verified a new iso, installed and completed all steps with no errors but when it completes and reboots all I get after the xubuntu splash screen is a blank screen and a blinking cursor. No feedback, no hints at what might be wrong or what to try, just a blank screen :-(

This machine was running Windows XP OK, slow but useable, I would have thought an xubuntu install should have gone smoothly ](*,)

I've tried appending acpi=force and whilst I've found the command line and where to enter the command, once I've gone past that the screen still displays the warning (like it did before) and I get nothing but the same old blank screen and blinking cursor :confused:

---

### Post by Sam Lars on 2008-12-22
If you do Ctrl+Alt+F1, does it take you to a prompt where you can log in?

---

### Post by Sour Mash on 2008-12-23
> **Sam Lars said:**
> If you do Ctrl+Alt+F1, does it take you to a prompt where you can log in?

Don't think I tried that - I did try the "usual" windows key combos like ctrl+alt+del, Esc, alt and everything :-) but nothing worked.

I kinda gave up with ubuntu and tried a few other distros like Puppy (worked but oh so techy) and Gentoo (sort of worked but again far too involved for me). Then put in openSUSE and that installed without drama, all came up running and working fine. Connected to my wired network OK and I started to tick off the features the laptop must have to be handed over to my daughter. 

The only thing I can't get working is the wireless PC Card but there sem to be a few fixes around for that - again very techy which scares the bites out of me. Not because I will break anything just because I don't understand it and I wrestle with my need to understand versus the fact that I feel I shouldn't need to understand in order to just use it - if you follow me!

I think now I have got this far I should complete the task with openSUSE and then keep trying with xubuntu because of all the flavours I've tried so far it is by far the most straight forward and "easiest" until things go wrong then you get nothing!

---

### Post by Sour Mash on 2008-12-23
After much wailing and gnashing of teeth, a brief dalliance with Fedora involving 3 CD downloads, 2 installs and each time it asks for a password and rejects it even though I used the simplest possible, I have returned to xubuntu and got something working!!!

I can hardly believe it but I did the install and all went well up to re-boot, they the black screen of bewilderment and the flashing, taunting cursor appeared. I was all set the throw the thing out of the window when I remember the key sequence suggested in this thread - OK so that didn't work BUT it did prompt me to start pressing keys to see if anything would shift it. Well pressing the screen print key did just that, up pops a log in box and away we go, we're in and running xubuntu.

So, now I'm off out for the evening but I have left it doing all the installs it likes, LAN connection worked straight away (no sign of a wireless connection but that will come with time). Then once I get up the courage I may just reboot it and see if I can get passed this black screen of bewilderment.

Other things besides the all important WiFi that will need sorting - the display, it is far too small for the screen - I need to find the xubuntu equivalent of display properties as it seems I could use a different resolution - I suspect it's because I didn't know what to select during install and have used too small a display.
Then it's test out the music playing capabilities and see if I can get it to access my Vista desktop via the network.

Oh what a relief that it's actually running xubuntu!

:P

---

