---
title: "USB Installation wont appear."
date: 2011-04-16
forum: New to Ubuntu
---

### Post by Intrebute on 2011-04-16
I am really sorry if this has been asked before, but I just can't seem to find this question asked. Ok, I am absolutely new to Ubuntu and Linux in general. This is what I have done,

I followed the instructions on the [download page]("http://www.ubuntu.com/netbook/get-ubuntu/download").

I created the USB Drive, I restarted the computer, nothing. I restarted again, and changed the BIOS settings. I put the USB drive on the top of the list, and when I restart again, "Ubuntu 10.10" appear on screen, with the four blinking dots in the bottom. Thing is, the image is scaled and centered in the screen, that's good. A few seconds, it resizes and the loading image shrinks to the top-left. After that, some blurry background appears, and then, nothing. ABSOLUTELY NOTHING. I suspect it is something graphical, as in, the whole thing is scaled or shifted and I just can't see anything. If I press the power button, a small prompt appears, asking to shut down, restart or suspend. The mouse is not visible, but I can move and the options would highlight. At this point I am stumped, so I ask here.

Any options?

---

### Post by Hippytaff on 2011-04-16
Hi and welcome

Do you know what graphics card you have? you might want to try this.

boot to the usb as you have done but just after you turn the computer on hold down shif. You should be presented with a menu (grub menu). Highlight ubuntu (by default the top one) then press e. then change the words 'quite splash' to 'nomodeset' and press CTRL+X to boot.

If you manage to get to the desktop see if there are any drivers available in system > administration > additional drivers...or system > administration > hardware drivers.

Failing that try downloading the iso again and use [unetbootin]("http://unetbootin.sourceforge.net/") to make a bootable usb:-) It could be that the iso is corrupt, also make sure you format the usb

---

