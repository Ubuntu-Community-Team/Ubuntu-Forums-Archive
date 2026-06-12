---
title: "Gpart unmounting from /?"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Garthhh on 2009-11-28
trying to do a dual boot with a desk top & minimal install [8.04]
I'm trying to repartition the drive to do this
I follow the help file for resizing, but can't unmount error:

[B]Could not unmount /dev/sda1

The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.

[/B]I don't know what that means[B]?
[/B]or how to resolve

---

### Post by nothingspecial on 2009-11-28
Do it from the live cd.

You cannot unmount a partition you are using.

---

### Post by Garthhh on 2009-11-28
ok that makes sense.
run cd & do what?
A little more direction please:p

I have a couple more threads going,my actual problem is. no sound
[http://ubuntuforums.org/showthread.php?t=1340343](http://ubuntuforums.org/showthread.php?t=1340343)
related thread
[http://ubuntuforums.org/showthread.php?p=8402899#post8402899](http://ubuntuforums.org/showthread.php?p=8402899#post8402899)

---

### Post by nothingspecial on 2009-11-28
You need to run the live cd and choose system > administration > partition editor.

Then do your partitioning from there.

---

### Post by Bartender on 2009-11-28
Yeah, Garth, pop the CD in the tray, reboot the PC, choose "run Ubuntu without making any changes", wait for the desktop, then go into Admin like nothingspecial describes.  If you want to move or delete or resize the swap partition you'll have to right click on it and choose "swapoff".

---

### Post by Garthhh on 2009-11-28
That worked
thanks for the detail
Gotta figure out the next part now LOL

---

### Post by Bartender on 2009-11-29
What's the next part?

Just describe what it is that you want to do, or think you want to do.

---

### Post by Garthhh on 2009-11-29
Long range
learn some stuff & be able to leave the windows world....

I want to be able to convert more lp - mp3 [already have 10k songs].  I have a seagate go 250g external HDD with the music files on it.

use this machine to be the server for my home network

share files with 2 windows laptops [1 XP, 1vista] also on the network.  I can see them from here, but they can't see this machine or the ex HDD...

occasionally print a page or two[already works]

I've done a couple of installs [both full & minimal].
I think I can try stuff on the partition [new] & keep the 8.04 full install until I find something that works better.

I'm unemployed & don't have very many blank disc's [cd's] left.  I'm hoping I can install on the blank partition without burning cd's
& then boot to it for trials

If I could fix my sound problems that would be fine.

Here's some back ground
 				 				**No sound on new install 8.04** 			
 			 			 		   		 		 		Old Dell 
optiplex
GX1, service tag eymu4
intel 440Bx PIIx4e [chipset]
crystal semiconductor cs4236
500mb ram
40g HDD
I did a search tried the tweaks
basically install all Gstreamer & alsa files I could find

the speaker icon has an X next to it & spits out:

[B]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.[/B]

Here  are the active threads I already have going:
[http://ubuntuforums.org/showthread.php?t=1340343](http://ubuntuforums.org/showthread.php?t=1340343)
[http://ubuntuforums.org/showthread.php?t=1337336](http://ubuntuforums.org/showthread.php?t=1337336)
[http://ubuntuforums.org/showthread.php?t=1334490](http://ubuntuforums.org/showthread.php?t=1334490)

I'm not attached to 8.04, but I also need some level of stability, I don't really want to have to update every 6 months...
& I like good red wine :p

Well you asked

---

### Post by Bartender on 2009-11-29
I like a good red wine too but usually settle for mediocre. 

Reminds me of when my wife was describing how she makes her steak marinade.  She described pouring in a splash of wine.  Someone asked what kind.  She said "box wine".

Wow, Intel 440BX motherboard chipset, that is old.  That's like Pentium II or thereabouts.  Is the sound onboard?  Do you have any available PCI slots?

Where do you live?  I could send you a Creative Sound Blaster card that I know works in Ubuntu.  You'd need an open PCI slot, though, not ISA.  ISA is the really long, usually white, bus with the big coarse contacts where the card slots in.  PCI has much finer contacts. 

Come to think of it, I just dismantled a Pentium III 600 MHz PC with 512 MB RAM that a guy gave me.  I installed Ubuntu, hooked up an old HP 1350 printer to it and it was barely able to print a test page.  So I kind of gave up on it, but I'm guessing it'd be a lot faster than what you've got.

In a few days I'll know whether something comes thru.  If it does, I'll have another PC or two to play with and could send you a Pentium III 1GHz instead.  It runs a lot faster than the 600.

PM me, let's see how far away you live and how much it'd cost me to send you a box of goodies.  If I do send you a motherboard, it'll be a bare board that you'll have to fit into your case, OK?

---

### Post by Garthhh on 2009-11-29
Yes the sound is onboard
& it has both ISA, PCI slots
I see a choice for sound blaster in bios, so this is to enable a sound card running through an expansion card[PCI]?

I also have a custom built, which kept locking up mid boot
microstar 6368 version 5 MOBO
celeron 3 processor
500mb ram
maxtor 40g diamond plus8 HDD
tigerpro PSU
Award bios v6,00pg

The chassis [all metal] & fan set up are much nicer than the dell

I think the tigerproPSU died.
I had the custom up and running after jumping the enable bit, every time I did a restart I would have to reset or cycle the power 5-10 times, finally wouldn't come on at all so i threw the HDD in the dell & away I go
 the original plan was to use the dell PSU in the custom
The tigerpro & the dell both have 20 pin connectors, but they aren't arranged the same.  I don't have that particular pin extractor & was trying to avoid cut & splice or soldering.

---

### Post by Bartender on 2009-11-29
OK, it's a good thing you knew about the Dell pin-outs.  What Dell did, spec'ing different pinouts on their motherboards and power supplies, was truly evil.  

I have very low regard for Dell.  There are several reasons for that but what they did with their ATX wiring really stands out in my mind.

I'm not sure what that means if you're seeing Sound Blaster in BIOS.  I don't think the onboard sound chipset is Creative's (?)

On a PC running Ubuntu, assuming you have an open PCI slot, all you'd do is turn it off, unplug the power cable from the PSU, open it up, and insert the PCI card.  Close it back up, at boot you might want to check the BIOS to see if there's a setting to use a discrete sound card but I'm guessing that it would be picked up automagically by Ubuntu and you should have sound.

Oh, hey, in BIOS also check to see if "Plug and Play OS" is unchecked.  I'm under the impression that was a popular setting way back in the Windows 98 days but pretty sure things work better with that set to "disabled" or "off".

So let me know if you want me to send you that sound card, OK?  Unless you're too far away.  

I'll PM you.  Do you know how to get to your Private Messages?  Up in the right hand corner?  That way we can talk about maybe sending you some other parts if those used PC's come my way.

EDIT:  Locking up mid-boot.  Hmmm.  I wonder if the CMOS battery on the motherboard is dead?  Or maybe the CPU heatsink isn't working at all and it's heating up really fast.  If you've never replaced the CMOS battery I'd start there.

---

### Post by Garthhh on 2009-11-29
the sound stuff came from dell's support site...
the check box for SB in bios, probably to enable the slot
I need to come up with a usb card, this thing only has 2 USB's

I haven't come up with a source of junk [parts] yet

the speed of the dell running 8.04, compares favorably to the pentium 4, 1.2g ram gateway laptop running XP.

The micro star MOBO has a fan mounted right on the heatsink for the processor & advanced bios didn't show any unusual heat readings...  I see some stuff in the manual about flashing the cmos & other stuff, got nothing to lose, if I can get the PSU to start LOL

---

### Post by Bartender on 2009-11-30
Generally speaking, the CMOS battery will last about four or five years.  I'm under the impression that they'll die more quickly if the PC is used infrequently.  Flashing the BIOS is a whole different deal and you don't want to mess with that unless you're pretty sure a newer BIOS has a feature you need.  If you pop the CMOS battery out and replace it with a new one, all that'll happen is any changes made in BIOS will be lost as BIOS resets itself to default.  Not a big deal.  Just go back into BIOS and change whatever needs to be changed.

The sound card I want to send you is a full-height card.  Looks like this
[http://www.recycledgoods.com/zoom_s_p_16031_1.jpg.ashx](http://www.recycledgoods.com/zoom_s_p_16031_1.jpg.ashx)
The bracket fits into a standard-sized case, not a compact case.  Is your Dell a standard tower or mid-tower?

I did a quick Google Image search for "optiplex GX1".  Some of the cases are your typical full-width case, like in this picture
[http://www.tsunamiwake.com/products/dellgx1.jpg](http://www.tsunamiwake.com/products/dellgx1.jpg)
That would work with the sound card I have.

Other Optiplexes such as this one are questionable.. 
[http://www.pcarenahungary.com/pricelist/oriaskep/dell_optiplex_gx110-298.jpg](http://www.pcarenahungary.com/pricelist/oriaskep/dell_optiplex_gx110-298.jpg)
I'm not absolutely sure but that looks like it's too narrow for standard size cards.

So let me know what kind you've got, OK?

There's got to be a source in town for old 20 pin ATX power supplies.  Know any geeks?  Maybe at the local PC shop, or garage sales, etc.  Problem is it's often the PSU that dies in older PC's so any scrounged up PC might be suffering from a failing PSU...

---

### Post by Garthhh on 2009-11-30
it's a regular tower plenty of room for fullsized cards.
I think the switch on the back of the TigerproPSU is bad gonna jump it out in the morning.  Clear the  cmos & give it another shot.
Unbuntu is already on the HDD, boots right up in either machine

---

### Post by Bartender on 2009-11-30
Be careful sticking your fingers inside a PSU.  The caps can hold a charge for a coupla days.

---

### Post by Garthhh on 2009-11-30
I'm not imtimidated by Hardware, I worked on PLC's [process computers].
I'm not as familiar with regular stuff, only been on the net since 06, part of the reason for my project is to gain a hands on deeper understanding:D

---

### Post by Garthhh on 2009-11-30
Got the microstar based custom working.
Jumped the power switch on the PSU & found loose connection for the enable bit on MOBO

I still need the SB card as the input side of the onboard sound clicks & pops even after running a ground from input device [receiver] to case of PC

I 'll work on some of the other issues before I start a new thread...

---

### Post by Bartender on 2009-12-01
Check's - er, I mean card's in the mail.

---

