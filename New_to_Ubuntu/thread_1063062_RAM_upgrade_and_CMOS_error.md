---
title: "RAM upgrade and CMOS error"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Bearly Able on 2009-02-07
Hi,

An elderly friend has been given an old Windows XP desktop - her first ever computer.  All she wants to do with it is e-mail relatives abroad and write the odd letter.  To save her from the hassle and expense of anti-virus software, and all the other problems of Windows, we thought it would be useful to convert it to Ubuntu.

I tried running it from a live CD, to test that the hardware would work with Ubuntu, but it only had 112MB RAM, so that wasn't an option.  I've installed Ubuntu 8.04 from the alternative CD, as a dual-boot with XP, and it runs, although very slowly - as does XP.  (I'm still trying to configure the dial-up modem, but that's another story.)

I managed to get hold of the same kind of RAM (second-hand) and have added another 128MB.  I have also replaced the original 128MB, as I assumed - probably incorrectly - that it must be faulty as the system only reports it as 112MB.  When I booted up after this, I got an error message about the CMOS settings being incorrect.  Is this because I've replaced the original RAM, and how do I correct this?  Windows is still reporting 112MB RAM and I confess I don't know how to check this under Linux.

I knew this machine under its previous owner, and it has always had a problem with the date and time, which do not update when the machine's turned off.  I believe this is also something to do with CMOS, but my understanding beyond that is hazy, to say the least.

Is there a way I can get the machine to recognise the new RAM?  I agree with all the folk itching to tell me to ditch it and get a new one, but the whole point of this exercise is to save our friend money!

Thanks for any help you can offer.

Lesley

---

### Post by halitech on 2009-02-07
> **Lesley Lutomski said:**
> Hi,

An elderly friend has been given an old Windows XP desktop - her first ever computer.  All she wants to do with it is e-mail relatives abroad and write the odd letter.  To save her from the hassle and expense of anti-virus software, and all the other problems of Windows, we thought it would be useful to convert it to Ubuntu.

I tried running it from a live CD, to test that the hardware would work with Ubuntu, but it only had 112MB RAM, so that wasn't an option.  I've installed Ubuntu 8.04 from the alternative CD, as a dual-boot with XP, and it runs, although very slowly - as does XP.  (I'm still trying to configure the dial-up modem, but that's another story.)

I managed to get hold of the same kind of RAM (second-hand) and have added another 128MB.  I have also replaced the original 128MB, as I assumed - probably incorrectly - that it must be faulty as the system only reports it as 112MB.  When I booted up after this, I got an error message about the CMOS settings being incorrect.  Is this because I've replaced the original RAM, and how do I correct this?  Windows is still reporting 112MB RAM and I confess I don't know how to check this under Linux.

does the machine have a built in video card? if it does (I'm suspecting it does) then it probably has been assigned 16meg of ram for the video so it is showing the correct amount. I would probably suggest using Xubuntu instead of Ubuntu, has lower requirements the Ubuntu.

> I knew this machine under its previous owner, and it has always had a problem with the date and time, which do not update when the machine's turned off.  I believe this is also something to do with CMOS, but my understanding beyond that is hazy, to say the least.

probably the cmos battery is dead and needs to be replaced. normally easy to do and it looks like a big watch battery on the motherboard.

> Is there a way I can get the machine to recognise the new RAM?  I agree with all the folk itching to tell me to ditch it and get a new one, but the whole point of this exercise is to save our friend money!

you problably need to go into the BIOS and allow it to update the amount of ram

> Thanks for any help you can offer.

Lesley

welcome and post back if you have any problems :)

---

### Post by Bearly Able on 2009-02-07
Hi Guys,

Thanks for the suggestions.  I'm at home at the moment, but I'll go round in the morning and try them out.  

Shipshape: both RAM cards (not sure that's the right word) are 128MB, as was the original, so the order isn't an issue here - right?  (I know some systems need the largest card first, etc.)  I did try searching on the internet, but I can't trace either the system or the motherboard, so no joy.  In the end, I read the number off the installed RAM and searched for the same thing, so it should be OK.

Thanks again guys.

Lesley

---

### Post by halitech on 2009-02-07
did you install both sticks of ram and still only have 112 showing? if so, might be a bad ram slot if 1 slot shows 112 no matter which one is installed.

---

### Post by kestrel1 on 2009-02-07
Sounds like there is onboard graphics taking some of the RAM (16MB)
If the date & time are wrong then I would imagine that the CMOS battery is dead or on the way out. CMOS batteries are normally button type (CR2032), but it is best to check first. I would also suggest installing Xubuntu on a system with a low spec.

---

### Post by Bearly Able on 2009-02-07
Yes, I installed both sticks - that's why I was surprised there was no change.  (We added extra RAM to our own PC system a while back and it just appeared without me having to configure anything.)  There are only two RAM slots on the motherboard, so I'm a bit stymied if one of them isn't working.

---

### Post by kestrel1 on 2009-02-07
You may need to check in the BIOS to see if you need to set the RAM up. Older systems didn't always see the RAM automatically & had to be told.

---

### Post by boof1988 on 2009-02-07
One thing you may want to check is the maximum RAM the system allows.

If possible, maybe check out the manual (either print version or online) and see if it indicates the maximum amount of RAM allowed.

I don't know what computer you have so this may be unnecessary... Just a thought...

---

### Post by kestrel1 on 2009-02-07
If you have been unable to determine the what the motherboard is, you may want to take a trip [HERE]("http://www.motherboards.org/tools/moboidtools.html")
If you enter the BIOS string that appears at the bottom of the initial boot screen, you may be able to find out what the mobo is.

---

### Post by the.phantom on 2009-02-07
think you are going to be operating at the min limits of ram for 
standard ubuntu?

might want to try a different version  say xubuntu?

[http://www.xubuntu.org/](http://www.xubuntu.org/)

it is not as hard on graphics and such so might be better?

i have ubuntu running on a 400mhx pent with 384 and it is very slow !

if you are going dilaup it can be hard to get it up and working
i gave up and got a external serial one and worked great ( best data 56K)
and it even says it works on linux !

hope this helps a bit?

---

### Post by Bearly Able on 2009-02-08
Hi Guys,

Thanks for all the suggestions - your help is much appreciated.  I didn't get the CMOS error message when I booted up this morning (and the computer still thinks it's yesterday), but I haven't made much progress, either.  (I will get a replacement battery, but I'll need to ask a friend on the mainland to post me one - no computer shops here.)

Still no joy with the RAM - I tried the BIOS, but couldn't find an option that would let me reset it.  Not being too sure what I was after, I tried every possible menu, but found nothing I could recognise as the right thing.

Kestrel1: Thanks for the suggestion, but there is no BIOS string shown.  The opening screen displays a background NEC logo, with the message "Press F2 to enter BIOS" etc., then goes straight to the GRUB menu.  The initial screen is visible so briefly it took me two attempts to read which key I needed to enter BIOS, and a third attempt to actually get there.  (Heaven help me if I ever want to enter Setup.)

The PC is an NEC PowerMate, but the specs as I know them don't match any model of PowerMate I've been able to find.  Following a suggestion from a friend, I did a scan of the computer system at Crucial.com.  (I could get online with the internal modem under Windows.)  It couldn't find a system model for the PC, but reported the motherboard was an MSI, model MS-6511.  I couldn't find this online, either.  It reported the maximum memory capacity as 512MB, but then it said there was 256MB installed, when there's actually only 128MB.  (Thanks, Halitech and Kestrel1 for explaining about the video card.)

Better news with the modem, in that I seem to have managed to configure it following the instructions in the Wiki.  Unfortunately, I can't get it to dial out, so I'm back home to use my broadband to try and find where I've gone wrong!  Thanks for the tip about external modems, the.phantom.  I have a problem getting hold of one - no computer shop, and most online retailers have a £20+ surcharge to ship to the Highlands and Islands.  If anyone can suggest a current model that works, I can send a friend in Glasgow to hunt for it.

Finally, I've taken everybody's advice and am burning an Xubuntu alternate CD as I type.  I probably won't get it installed until tomorrow, as Scotland play Wales in the Six Nations this afternoon, and kick-off is in under two hours time...

Thanks again everyone.

Lesley

---

### Post by kestrel1 on 2009-02-08
Often manufacturers get motherboards that are cheap to purchase & are not normally put out for general public purchase. I have found these are often MSI mobo's. Nothing wrong with them, just that they are lacking in manuals etc. I had a Tiny PC years ago & that had an MSI mobo, it went on for years.
When you are unable to see the BIOS string because there is a manufacturers splash screen, you should only need to disable the splash screen from the BIOS, but it looks like you found out what mobo you have via Crucial. Good job Crucial.
I think Xubuntu will work well on the system.

---

### Post by Bearly Able on 2009-02-10
Hi again,

Quick update for anyone who's interested.

I swapped the RAM sticks about and discovered it was one of the replacements that was faulty, not the second RAM slot, so now we have 233MB - jings, what a difference!  It was a whole new machine, even before I installed Xubuntu and things really got going.  New battery should arrive in tomorrow's post and everything will be hunky-dory.

Thanks again to everyone who took the trouble to help.

Lesley

---

### Post by kestrel1 on 2009-02-10
Isn't it typical. You get something only to find that it's faulty.
I suppose that is luck, or lack of :lolflag:

---

