---
title: "Belkin F5D7000 / Dapper Drake 6.06 Success"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by PeterHoward on 2007-01-06
I have just got this PCI wireless networking card working with
Ubuntu 6.06 (Dapper Drake) using a very simple recipe (link below),
but only after some detective work and problems.

        So, I hope these notes will save other people some time...

        My machine is a Dell (Pentium D820), dual-booted with WindowsXP
        and Ubuntu. The network card works fine in Windows, so the first
        set up I tried was to use Ndiswrapper
        ( [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) ) . This is a tool that
        provides a Linux kernel module that allows Windows wireless card
        drivers to be used. I first tried it with the Windows drivers
        that came with the card, because I knew they worked fine in Windows.
        That didn't work.

        Nb. At this point I didn't know which chipset the card used and
        didn't know how to find out either. The driver filename didn'd help -
        it was "oem31.sys".

        The Ndiswrapper site links to drivers you can download to work with it,
        and tells you how to work out systematically
 which one to choose (
        [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) ).

        This is when I learned, as a side-effect, that the chipset was
        "Ralink RT61" I downloaded and tried the recommended driver with
        Ndiswrapper, but still without success.

        Then came the breakthrough. I found this ubunto forum thread by
        searching the forums for 'rt61'

        [http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

        It was a breakthrough because I discovered here that Dapper Drake /
        6.06 ships with the rt61 driver already installed in the kernel! -
        avoiding all that fiddling about with source code, make etc.

        I didn't know it, but here was a very simple and easy solution
        right under my nose. You still have to download a few files and
        put them in the right place - but it's a relatively simple
        solution.

        Detailed instructions are given in the link above. Hope it helps you
        like it helped me.

---

### Post by alecjw on 2007-01-07
Cool. What version of the card is this?

---

