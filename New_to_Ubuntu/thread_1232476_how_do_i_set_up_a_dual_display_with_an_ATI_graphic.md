---
title: "how do i set up a dual display with an ATI graphics card"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by super kim on 2009-08-05
hi i have an [COLOR=Navy]ATI graphics card [/COLOR]and i am trying to get the display to either [COLOR=Navy]clone[/COLOR] or have a [COLOR=Navy]dual display[/COLOR]. Currently i have got no where, i have previously had an nvidia card and that was pretty simple.
here is some information about my graphics card, 

$ lspci -v

01:00.0 VGA compatible controller: ATI Technologies Inc R300 AD [Radeon 9500 Pro]
    Subsystem: ATI Technologies Inc Device 0002
    Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 12
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at a000 [size=256]
    Memory at e9000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at e8000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon, radeonfb

01:00.1 Display controller: ATI Technologies Inc R300 AD [Radeon 9500 Pro] (Secondary)
    Subsystem: ATI Technologies Inc Device 0003
    Flags: stepping, 66MHz, medium devsel
    Memory at e0000000 (32-bit, prefetchable) [disabled] [size=128M]
    Memory at e9010000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: <access denied>



:confused:thanks in advance:confused:

---

### Post by halitech on 2009-08-05
the radeon 9500 has been dropped for driver support so you won't be able to use the ATI catalyst drivers and I don't know if the opensource drivers will do dual display or not.

---

### Post by super kim on 2009-08-05
i found out earlier that the catalyst drivers wouldn't work, the display comes up on the tv when the computer is booting, is there really no way to get even a cloned output???

---

### Post by super kim on 2009-08-05
ok so how about switching the display device? if i unplug my vga monitor and just have the svhs plugged in, would ubuntu detect that and use it? ideally there would be a way to switch the display with some sort of hotkey combination.
how does ubuntu select its diplay output? and more importantly how can i change it?
some-one has to have these answers and even if it's impossible i'd still like to try it.

---

### Post by halitech on 2009-08-05
Is it a laptop? I know on mine I have a F key I can press (don't remember at the moment though) Not sure if a desktop would have the same option or not.

I guess you could try disconnecting the vga and output to the tv only and see what happens on boot up.

---

### Post by super kim on 2009-08-06
no, i'm not using a laptop. i have tried removing the vga lead before a boot and the grub will use the svhs output but then ubuntu uses the vga regardless of the fact the is nothing connected. i know this as i waited sveeral minuetes then plugged in my crt, and the log in screen was present. the only difference is that since ubuntu couldnt see which display device i was using when booting the screen size was a little out of place, this of course reset itself after another reboot.

if i'm using an old ati card then does the xorg.config file determine the display output? if so then i could try changing that.

---

