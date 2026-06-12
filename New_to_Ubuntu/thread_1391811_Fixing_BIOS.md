---
title: "Fixing BIOS"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-01-27
My last thread had evolved to this topic, and since it was locked for discussion about passwords, I thought I'd begin this new one.

I have 2 computers, they are basically the same.  I somehow messed up something in the BIOS and now cannot detect my hard drive.

My question is:  If I go into both and make the faulty one match the working one should that work?

The good one is probably partitioned for this Jaunty OS.  

I'm thinking I should go into both and see where they are different -- not change anything -- then come back and ask you.

---

### Post by Psumi on 2010-01-27
Reset to factory defaults for BIOS?

That's what I always do.

---

### Post by Chris Edgell on 2010-01-27
How DO you DO that?

Thanks

Oh but then again, I should say, on the test computer, I can only boot up by a live CD...
otherwise all I have is the BIOS screen.

---

### Post by bkratz on 2010-01-27
> **Chris Edgell said:**
> My last thread had evolved to this topic, and since it was locked for discussion about passwords, I thought I'd begin this new one.

I have 2 computers, they are basically the same.  I somehow messed up something in the BIOS and now cannot detect my hard drive.

My question is:  If I go into both and make the faulty one match the working one should that work?

The good one is probably partitioned for this Jaunty OS.  

I'm thinking I should go into both and see where they are different -- not change anything -- then come back and ask you.

Sounds like a good plan since they are pretty much the same machines. You might look at the date of manufacture since one may have a later bios revision than the other (should be a rev number showing for that). Could be a lengthy process though!

---

### Post by Psumi on 2010-01-27
> **Chris Edgell said:**
> How DO you DO that?

Thanks

Oh but then again, I should say, on the test computer, I can only boot up by a live CD...
otherwise all I have is the BIOS screen.

In the BIOS Screen, SOMEWHERE there is a list of what keys do what on-screen (No BIOS should come without these on-screen instructions nowadays.) One of the keys will say Reset to Defaults or Factory Default Settings, etc.

However, you need to be careful, if it says "Reset to Defaults" and you've saved the settings as default, there's nothing you can do. (It's always a good idea NEVER to save over the default settings, so that you can reset to them later if anything goes wrong.)

---

### Post by Chris Edgell on 2010-01-27
I have found a place where it says, "PXE BIS Default Policy"....Deny
But if I change it I can get, accept, or reset.  Could this be the reset you're referring to, Psumi?

It is listed under "Security Systems".

---

### Post by mcduck on 2010-01-27
> **Chris Edgell said:**
> How DO you DO that?

Thanks

Oh but then again, I should say, on the test computer, I can only boot up by a live CD...
otherwise all I have is the BIOS screen.

If you can get into BIOS, there will be an option to reset to defaults.

If not, you'll find a reset button or a jumper on your motherboard, but you'll probably have to check the motherboard's manual for detailed instructions. If even that fails, unplugging the computer from wall and removing the CMOS battery from the motherborad for about 15 minutes will reset all BIOS settings to defaults.

---

### Post by bkratz on 2010-01-27
> **Chris Edgell said:**
> I have found a place where it says, "PXE BIS Default Policy"....Deny
But if I change it I can get, accept, or reset.  Could this be the reset you're referring to, Psumi?

It is listed under "Security Systems".

That is not what you want. Here is a description of PXE
[http://www.tech-forums.net/archive/topic/47349.html](http://www.tech-forums.net/archive/topic/47349.html)

---

### Post by Chris Edgell on 2010-01-27
Hey, mcduck, hi,

WOULD that be the PXE BIS Default Policy, under the System Security?

---

### Post by Psumi on 2010-01-27
Oh, I know.

Hit the Save settings key see if a dialog comes up that allows you to reset to defaults.

---

### Post by Chris Edgell on 2010-01-27
You know what??!!

I again have to thank Sir Jasper, who showed me "How to google" tutorial.
I just googled that PXE BIS (etc) and got to Dell support that listed all the defaults and now I detect the hard drive.  Thank you both.

---

### Post by Hospadar on 2010-01-27
the PXE thing is not what you are looking for

PXE is a network protocol to allow administrators to boot machines off a network.  A lot of big IT shops use it to allow operating systems to be installed without disks on any machine connected to the network.

On every modern motherboard I've ever used there is a [jumper ]("http://en.wikipedia.org/wiki/Jumper_%28computing%29")which resets the bios to factory settings.  If you look at your motherboard, you'll probably see that near the bios chip (which if you don't know usually looks like [this]("http://en.wikipedia.org/wiki/File:Phoenix_bios.jpg") there will usually be a quarter-sized watch-type battery with some exposed prongs nearby (which could be connected by a jumper).  Typically connecting (or disconnecting if they are already connected) these prongs (usually this is easiest to do with just a flat-head screwdriver) for a couple seconds will reset the bios.  Do this while the machine is powered off.

If you arn't sure about this, you should google around for the manual for your motherboard, or if the machine was built by someone else (like dell or HP for example) try poking around their website or contacting them to try and get a motherboard manual.  The motherboard manual will have precise instructions on this.

Look around the board for instructions or pin labels.  Often the two jumper pins that need to be connected will be labled somehow (though possibly in a cryptic fasion).  Something like "BIOS rst" might be suggestive of what you want.

And be careful to leave the hardware in the same state you found it, if you connect two previously unconnected pins, make sure you disconnect them later.

worst case scenario you can usually pop the bios chip out and send it in to get re-programmed.

---

