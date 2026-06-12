---
title: "Hardware Recognition Issue (9.04)"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by augen on 2009-10-22
Hello All,

Let me say firstly that I am absolutely a Linux noob, and the sort of computer user for whom the GUI was intended. Recently I offered to take away a Sony Vaio desktop (model # VGC-RA710G) that was destined for recycling due to apparently unfixable stability problems under XPMCE, its original OS. I thought it would be interesting to try to see if I could get it working well with XP again (not sure that it ever really did); wanted to try Win7 RC on it; and was very curious to try Ubuntu for the first time. The basic harware specs are: P4 3.2 GHz, 250GB PATA, 2GB PC3200, DVD burner and DVD ROM, FDD, Multi-card reader, some kind of TV tuner thingy related to media center usage, and a typical assortment of USB, firewire, ethernet ports. The computer dates from approximately 2004.

I was pleased to find that Jaunty installed quite nicely. It failed to "see" the TV tuner card (part of Sony's multi-media harware for MCE), but that is of no consequence to me. I'd just as well prefer to remove it to make way for a wireless adapter.

When doing a driver check, Ubuntu indicated that a proprietary driver from NVIDIA for the FX5200 video card was available, which did install perfectly and allows the usual configuration options. So far so good.

Other bits and pieces such as the two opticals, the FDD, and various integrated mobo stuff all seem to work normally. The one hitch, however, is the multi-card reader, which has four slots for several different card formats. Internally, this reader is connected to a mobo USB header. When I open "Computer" I see HDD partitions, the FDD, both opticals, and four separate "**USB Drive**" entries. There are** four slots** on the multi-card reader, and so I assume that is why Jaunty shows the four USB Drives in Computer. However, the card reader slots don't appear to be functional--inserting my camera's SD card results in nothing happening.

I'm guessing that it is nothing more than an issue of proprietary hardware for which Linux has no driver, but I am interested about Jaunty's ability to "see" four "USB" drives in place of the four card-specific slots. Does anyone know if there is a workaround for this kind of thing?

Diclaimer: I really am the ultimate noob, so if anything can be done, I'd need very explicit instructions, and very much more so with regard to working in the Terminal.

Thanks in advance for any help offered.

P.S. Ubuntu easily recognized my D40 when plugged into a front USB slot, so I can certainly read its SD card that way. It's just that I'd like to know if the card reader can be made to function.

---

### Post by LewRockwell on 2009-10-25
We will be starting a dedicated thread in the Absolute Beginner Talk area regarding flash media but thought you could start with this:

[http://wiki.laptop.org/go/How_to_Damage_a_FLASH_Storage_Device](http://wiki.laptop.org/go/How_to_Damage_a_FLASH_Storage_Device)

[http://elm-chan.org/docs/mmc/mmc_e.html](http://elm-chan.org/docs/mmc/mmc_e.html)

[http://en.wikipedia.org/wiki/Secure_Digital](http://en.wikipedia.org/wiki/Secure_Digital)



Not sure yet what title and tag combination will produce the most effective search results but we'll probably use a tag of mmcblk0 at least

Here's the new thread:

[http://ubuntuforums.org/showthread.php?t=1300716](http://ubuntuforums.org/showthread.php?t=1300716)

.

---

