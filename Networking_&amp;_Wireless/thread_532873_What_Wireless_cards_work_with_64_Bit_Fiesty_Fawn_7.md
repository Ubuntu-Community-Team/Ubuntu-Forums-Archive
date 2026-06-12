---
title: "What Wireless cards work with 64 Bit Fiesty Fawn 7.04 and how?"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by tobyh on 2007-08-23
I have tried to set up my Belkin F5D7000uk using NDISWRAPPER and Linuxant to no avail.  I have tried the 64 Bit drivers that came on CD but no good.

So my question is who is using Fiesty 64 bit and has a wireless card that works on that distro?  Also what is the card and how did you do it because I'll dump the Belkin and buy another - by the way I have tried the HCLs - Yes, Belkin F5D7000uk is there but I reckon that is for 32 Bit not 64 Bit hence my problem!

Any help on this would be gratefully received!

Thanks

Toby

---

### Post by tgm4883 on 2007-08-23
> **tobyh said:**
> I have tried to set up my Belkin F5D7000uk using NDISWRAPPER and Linuxant to no avail.  I have tried the 64 Bit drivers that came on CD but no good.

So my question is who is using Fiesty 64 bit and has a wireless card that works on that distro?  Also what is the card and how did you do it because I'll dump the Belkin and buy another - by the way I have tried the HCLs - Yes, Belkin F5D7000uk is there but I reckon that is for 32 Bit not 64 Bit hence my problem!

Any help on this would be gratefully received!

Thanks

Toby

You might want to point out that your looking for a desktop wireless card.

Otherwise I would recommend the intel 3945 which works OOB in feisty.

But since you have a desktop (after looking up the wireless card that doesn't work) I would recommend a router that can perform as a wireless client.  Buffalo one perhaps

---

### Post by kevdog on 2007-08-23
Are you fairly certain you cant get your configuration to work?  Ive gotten ndiswrapper to work with 64 bit WinXP drivers (not Vista) to work in the past.  What errors are you getting?

---

### Post by tobyh on 2007-08-23
Thanks for your replies.  Yes, sorry it was a desktop card I am trying to install.  With regard to error messages I will let you know when I run it again using the XP driver as suggested.

Will let you know how I get on!

Toby

---

### Post by tobyh on 2007-08-23
Well I've tried the XP 64  drivers for my Belkin desktop card and it hasn't worked both on NDIS and Linuxant.  With regard to error messages that is what is so frustrating - there are no specific errors - although Linuxant tells me that the device may not be plugged in (Well, it is!) or the drivers don't work with the kernel.  It intalls the driver and when I get ndis to list the device - there it is "driver present" - "Hardware present".  Do iwconfig and it says "no wireless extensions"! 

When I get a list of PCIs on the list it sees a Belkin device but little else.  I really just want someone to say look - here is the card I used and these are the drivers I loaded and I'll toddle off and buy the card.  

Thanks for your help on this!

---

