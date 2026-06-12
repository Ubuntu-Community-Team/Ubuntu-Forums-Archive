---
title: "Help installing new video card - N00B question"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by jondcoleman on 2009-10-20
Hello Everyone,

I am a first time Ubuntu user.  I installed 9.04 Jaunty on a 4 year old dell.  I just purchased a new ATI Radeon 9200 Video Card and have had zero luck in installing it.  If I just put it in and boot, I get nothing.  It doesn't even sound like the pc is booting although the video card fan is spinning so I know it is getting power.  I have spent four hours or more searching to try to figure this out.  Could someone please give me the step by step (beginner level) approach to get this working?  If you need more info please let me know.

Thanks in advance.

Jon

---

### Post by Mike_IronFist on 2009-10-20
> **jondcoleman said:**
> Hello Everyone,

I am a first time Ubuntu user.  I installed 9.04 Jaunty on a 4 year old dell.  I just purchased a new ATI Radeon 9200 Video Card and have had zero luck in installing it.  If I just put it in and boot, I get nothing.  It doesn't even sound like the pc is booting although the video card fan is spinning so I know it is getting power.  I have spent four hours or more searching to try to figure this out.  Could someone please give me the step by step (beginner level) approach to get this working?  If you need more info please let me know.

Thanks in advance.

Jon

This sounds like a hardware issue and not an Ubuntu-related issue. You're better off going to an ATI help forum rather than asking for help here.

If your computer doesn't seem like it's even booting, (i.e., you don't see any BIOS screens, or anything like that) then Ubuntu's got nothing to do with it.

I hope my response was helpful.

---

### Post by Mark Phelps on 2009-10-21
First off, even though you just purchased that card, there are no restricted ATI drivers that will work with it in Ubuntu 9.04 or newer.  So, don't go to the ATI site (or any other) to download or install drivers -- they won't work.

Second, I'm guessing that you had onboard video before on the Dell and (maybe) you didn't disable that when you plugged in the ATI card.  Check in the BIOS to ensure that if there is onboard video, it is disabled.

---

### Post by Mike_IronFist on 2009-10-21
> **Mark Phelps said:**
> First off, even though you just purchased that card, there are no restricted ATI drivers that will work with it in Ubuntu 9.04 or newer.  So, don't go to the ATI site (or any other) to download or install drivers -- they won't work.

Second, I'm guessing that you had onboard video before on the Dell and (maybe) you didn't disable that when you plugged in the ATI card.  Check in the BIOS to ensure that if there is onboard video, it is disabled.

Oh yes, just to clarify what I said, I'm referring to HARDWARE issues, not software (which includes drivers).

Mark, the big issue here is that he can't even tell if his computer is booting or not because he's getting no display - it suggests a physical problem with the hardware, not a driver issue.

So, like I said, as for the PHYSICAL, actual installation (nuts and bolts, wires and plugs, etc) of the card, check out an ATI forum. Come back when you can actually get your computer on and displaying.

---

### Post by Mark Phelps on 2009-10-21
> **Mike_IronFist said:**
> Mark, the big issue here is that he can't even tell if his computer is booting or not because he's getting no display - it suggests a physical problem with the hardware, not a driver issue.

Strange as it may seem, we don't have an argument here!

If the Dell came with onboard video, and the OP simply inserted a card, and then connected the video cable from the monitor to the card, there's a possibility (not sure, since I don't have a Dell to check this out), that if the onboard video is still enabled in the BIOS, it will not allow video signals to go to the card.

IN THAT CASE, he would see no video at all, including during POST and initial boot.

A way to check that, presuming the Dell has onboard video, would be to plug the cable into the onboard video jack and boot the machine, and then go into the BIOS.  If there is a selection for onboard vs (AGP, PCI, etc) and the onboard is checked, change that to the selection for the video card and reboot -- with the cable then connected to the card.

---

