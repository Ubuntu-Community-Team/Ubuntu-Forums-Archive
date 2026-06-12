---
title: "Multimedia Keys not working, neither is acpi_listen"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by athoma13 on 2010-05-28
Hi,

I am an absolute beginner on Ubuntu 10.04.
Recently installed it and using a DiNovo Mini wireless keyboard with it.

Now, the multimedia keys don't work.
I have followed the steps described [here]("https://wiki.ubuntu.com/Hotkeys/Troubleshooting") to no avail...
xev doesn't register any of the multimedia keypress (except for FN+Prev (|<<) which registers a hangul-hanja keypress).

The step I am stuck on is the acpi_listen which is meant to listen to input events. I use terminal window to run it, but that does NOTHING for me. I.e.

arnaud@Mediabox:~$ acpi_listen
jdfksjdbkvsdbkb
^C
arnaud@Mediabox:~$ 

Running the command still allows me to type rubbish to the console and doesn't exit until I CTRL-C out of it...
Reading other forums and things, this is not what acpi_listen is supposed to do...
I was expecting to see keycodes or scancodes (something else than my own typing anyway)
What am I doing wrong?

BTW: My diNovo works with windows machines multimedia keys and all.

---

### Post by athoma13 on 2010-06-01
Yay! worked it out...

I am using the usb dongle provided for the diNovo mini. 

I moved it to another port and re-paired the devices, and it worked itself out. Volume up, down, mute, play, stop all work! Not sure if it was the moving the dongle to another usb or re-pairing that fixed it (or a combination of both). I have moved the usb dongle back to it's original usb slot without issues.

---

