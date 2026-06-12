---
title: "Could disabling ACPI/ALPCI impact overall system performance/speed?"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by diablo75 on 2010-10-03
A few months ago I managed to talk one of my regular customers into trying a dual-boot configuration on their Toshiba A105 laptop.  Install well smoothly and they've liked the operating system very much.  But, as with most Toshiba laptops, there were a few odd glitches.  Specifically the wireless adapter would suddenly disconnect from the network and seemingly never want to reconnect to anything; it was as if the adapter had been shut off, only coming back after rebooting.  The same was true for just about anything plugged into a USB port; a mouse (wired or wireless) would suddenly stop working.  Replacing the plug in a different port didn't help either so again, a full system restart was required.

This was annoying.  So I decided to try an experiment based on a couple of experiences I had heard and read about from other Toshiba users.  People have found that ACPI support on Toshiba laptops have a reputation for being buggy due to the proprietary nature of the hardware and lack of support for the Linux community from Toshiba.  Often times disabling ACPI seemed to solve a lot of hardware related problems, with the least expense being an increased energy consumption, which would result in somewhat shorter battery life on a single charge.

Anyway, I did this to the above mentioned A105 laptop and while the user said all their problems with hardware have now gone away, they feel the system runs a bit slow.  I was wondering if disabling ACPI might possibly have some sort of negative impact on overall system performance?  I would think that it would actually be ever so slightly the opposite because the system isn't busy trying to manage power usage across separate components.  But that's just conjecture on my part; I don't really know for sure.  So I'm asking here.

---

### Post by P4man on 2010-10-03
disabling ACPI is the nuclear bomb option IMHO. Its an essential part of modern PCs, many will even not work with it disabled. It could cause all sorts of side effects; to name just a few: disable CPU scaling. So your users might be stuck at the lowest CPU speed. It could also disable fans and will certainly ruin battery life.

Disabling ACPI was a good shot at finding the cause, but its not a solution I would find acceptable. If you cant find a solution on the web, have some fun experimenting with boot option. There is a gazillion to try:
[http://redsymbol.net/linux_boot_parameters/](http://redsymbol.net/linux_boot_parameters/)

noapic and nolapic would be on the top of my list (note these also get disabled when you disable acpi).

---

### Post by diablo75 on 2010-10-03
Well perhaps you might be able to provide some insight about how to trouble shoot these weird issues that occurred before disabling ACPI?

I started a separate thread a few days ago, it didn't get any replies although I haven't attempted to bump it.  It contains a portion of the laptops debug log that was recorded at the moment the wireless adapter failed.

That thread can be found here:

[http://ubuntuforums.org/showthread.php?t=1585732](http://ubuntuforums.org/showthread.php?t=1585732)

---

