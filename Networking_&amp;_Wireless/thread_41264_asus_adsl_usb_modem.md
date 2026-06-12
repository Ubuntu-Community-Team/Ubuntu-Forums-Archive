---
title: "asus adsl usb modem"
date: 2005-06-12
forum: Networking &amp; Wireless
---

### Post by dwarfy on 2005-06-12
Hi everybody !
I've just installed that superb distribution :)
nice !

Well I've a problem with asus adsl usb modem ..
The installer didn't recognize it ..
That's a bit normal as no existing linux distro ever managed to install it automatically
In fact I had to work for a week or so in order to make it work on my last linux ..

The fact is that I'm not here to ask any help to install it
(I've done it allready once so ...)

I'm here to ask HOW it works in ubuntu , How is the hardware support managed
I'd like to make a kind of hardware package or whatever you call it that could support my modem .. (So I won't have to reinstall a third time, and people in the world can enjoy !!)

So if anybody here does know where I have to look, what I've to do ... in order to make ubuntu asus-adsl-usb-modem ready ... that would be nice.

I can post the exact model and other infos if necessary ...

thanks in advance
dwarfy

---

### Post by bernardfrancois on 2005-10-31
[QUOTE=dwarfy]Hi everybody !
The fact is that I'm not here to ask any help to install it
(I've done it allready once so ...)
[/QUOTE]

Can you please post how you managed to make it work? I'm not asking for a list of the commands you had to type, but just a brief description of how you did it (which drivers you had to load and so).

I'm configuring a dual boot system on my girlfriend's pc now, and if I can't get the internet working it will be 2x m$...

[edit]
Never mind, I just read at [http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/) that it is supported by EciAdsl at [http://eciadsl.flashtux.org/](http://eciadsl.flashtux.org/). If I'm not able to make it work I might post here again, but for now you don't need to reply.
[/edit]

[edit2]
It doesn't seem so easy to install it. I needed to have libc 2.3.5, but I didn't find the right package, so I tried to install from source. But that didn't work... The configure had to be run from  build directory, but when I wanted to run the make file, it didn't find the right makefile (allthough the configure succeeded).
So I tried to install an older version of EciAdsl (0.10, which doesnt require that libc version), but it still didn't work because I didn't have the pppoe package...
I got tired of rebooting to windows all the time (to download the required packages/source) so I gave up. Maybe later I'll try again, or with a distro that has the right packages included...
[/edit2]

---

