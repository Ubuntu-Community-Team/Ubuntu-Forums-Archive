---
title: "DWL-G510 random problems"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by Caleb9849 on 2007-01-22
I recently installed a D-Link DWL-G510 (Atheros chipset) into my Edgy system.  Initially, there was a hardware conflict which I resolved by switching a jumper on my mobo which disabled an integrated network adapter (I hate that integrated garbage :p ).  Anyway, I got the card working perfectly.  However, I am now experiencing random problems, including, but most likely not limited to:

--Random total crashes (no input responds at all, including ctrl+alt+backspace) (These crashes are almost inevitable when running dpkg or apt-get to install/configure software packages)

--Fonts going haywire (all characters replaced by the little boxes with numbers in them for unknown characters)

--Excessively frequent application crashes, primarily noted in Firefox and Gaim.

It has to be a hardware problem, because I decided to reinstall Ubuntu freshly, and it took me several tries to get it installed without a lockup during installation.  However, installing the wifi card and changing that jumper is all I've done as of late.  Does anybody have any insight as to what could be causing the problem or how to fix it?  Before anyone says, "get a new network card," this is actually my dad's network that I'm on, and he ran out and spent a bunch of money to switch to wifi because he doesn't like to have cables on the floor (yeah, real nice expenditure of time, money, and effort, there).  So it would be his hassle, not mine, and I'd prefer to find a way to diagnose and repair the problem, if possible.  Thanks in advance.

---

### Post by mindwarp on 2007-01-22
This is a hardware issue, and from the sound of it heat related.  Check for dusty or old fans, and that any heat syncs are correctly fixed to their corresponding chips.

---

### Post by Caleb9849 on 2007-01-22
I am now running temporarily on my old wired ethernet card, to see if the wifi card is actually the culprit.  So far, everything seems to be working great :-\.  But everywhere I've searched on the internet says that this card with MadWiFi works just fine.  What could be the problem?  Defective card, any chance?  And perhaps that initial hardware conflict was really the card's fault and not the integrated adapter?  I don't know :-\ what do you think?

---

### Post by Caleb9849 on 2007-01-23
Update:  I switched this network with my dad's (same model / chipset), and it gives me the exact same crap :-\ I thought this card was supposed to work fine, like it says all over the internet :-P.

---

### Post by bowkay on 2007-01-23
I use the same card in my setup...

Three things to look for...

1. Does your D-Link DWL-G510 work in your dad's machine without any problems? (double checks that it isn't the card)

2. If it does could the PCI connector be damaged in any way (dust, dry solder etc).

3. Double check the jumpers to the in-built network port and make sure they're set right and that you aren't shorting anything out with them.

If you want to use the card here's how I got mine working without a problem:
[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

---

### Post by Caleb9849 on 2007-01-23
That guide doesn't really work for me.  This particular card was released under different revisions with the same model name, but totally different chipsets.  Your guide is for the one with the RT61 chipset, whereas mine has an Atheros, so it uses the Madwifi driver.  Anyhow, both cards cause problems in my machine, and no problem in my dad's machine.  Perhaps it is a bad PCI slot....I'll try switching it to a different one.

---

### Post by Caleb9849 on 2007-01-23
Update: I changed PCI slots, and am still having the same problem.  So far, I've tried all three of these with little or no improvement:

1. Changing driver version
2. Changing card unit (same model though)
3. Changing PCI slot

It's really baffling to me since this card is supposed to work fine.  Could it be for some reason that my system's physical configuration just doesn't get along with this model in general for some reason?

---

### Post by bowkay on 2007-01-23
The only thing that I can think of is that the mother board bus from the PCI slot(s) has a fault, the cards don't play well with that mother board or the gremlins have decided that they need some entertainment and have decided that you're it. :)

Have you looked at the BIOS settings and and POST messages at boot time to see if there is anything of use? 

What does #> dmesg say about the card.

-- there is a reason why they call it *MAD*wifi

---

