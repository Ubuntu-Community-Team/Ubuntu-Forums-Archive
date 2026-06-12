---
title: "x server configure HELP!!"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Spitz13 on 2008-12-18
so i installed mandriva 09, but it didn't really work, it wouldn't load the desktop, it would just give me some weird colors, and all i could do was input commands (being really new to linux, i don't know any commands), so i had a really old ubuntu 5.10 cd, and i decided to give that a try to see if it was a mandriva issue, i installed ubuntu, to find out it wouldn't load the desktop either, it gave me an x server error, that said it was not configured correctly, and it said to restart x server once it was configured correctly, i tried configuring it and it didn't work.. this is the detailed error report:

```
(==) Using cofig file "/etc/xil/xorg.conf"
Skipping

"/usr/irg/lib/modules/extensions/lib Glcore.a:mdebug_clip.o"
no symbols found
skipping

"/usr/irg/lib/modules/extensions/lib Glcore.a:mdebug_norm.o"
no symbols found
skipping

"/usr/irg/lib/modules/extensions/lib Glcore.a:mdebug_xform.o"
no symbols found
skipping

(EE) no devices detected

Fatal server error:
no screens found

```

aproximately, something like that, i tried configuring x server about 3 times, maybee i did it wrong or something,
by the way, i also downloaded ubuntu 8.10, ran the live cd version, and it didn't wotk (i got an eternal black screen) and then i tried installing it, and i got a bunch of colors flashing.. before it even got to install..

i really don't know what to do and i would really appreciate any help

thanks.

---

### Post by shifty_powers on 2008-12-18
would be helpful to know the specs of your pc....

---

### Post by Spitz13 on 2008-12-18
oh sorry :P

its an HP Pavilion dv9008nr:
Processor:1.6 GHz AMD Turion™ 64 X2 Dual-Core
Ram: 1gb DDR2
Video: NVIDIA GeForce Go 6150 (UMA)

---

### Post by shifty_powers on 2008-12-18
so is this a laptop then i'm guessing, from your posted specs?

---

### Post by Spitz13 on 2008-12-18
yeah, although the screen doesn't work, and its connected to an external plug in and play monitor, if that makes a difference..

---

### Post by Spitz13 on 2008-12-18
i don't know if bumping is allowed on this forum, but i really need help and i would really like to be able to get a desktop on my ubuntu :(:(:(

---

### Post by fistfullofroses on 2008-12-18
This is an easy enough problem to fix.

First:
type this into your terminal window "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old && X -configure"

Second:
Reboot your machine

Third:
If the above does not work -
"cat /etc/X11/xorg.conf > XorgTerminalPrintOut.txt"
then post the contents of XorgTerminalPrintOut.txt to this thread.

---

### Post by Spitz13 on 2008-12-18
> **fistfullofroses said:**
> This is an easy enough problem to fix.

First:
type this into your terminal window "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old && X -configure"

Second:
Reboot your machine

Third:
If the above does not work -
"cat /etc/X11/xorg.conf > XorgTerminalPrintOut.txt"
then post the contents of XorgTerminalPrintOut.txt to this thread.

i just realized what the problem is, my laptob's screen, doesn't work, it sends very scattered signals, that are really hard to make out, so i use an external plug in and play monitor. when i booted to ubuntu just now, and i pressed cntrl+alf+f7, i got the "weird colors" on my external monitor, BUT after trying to make out what was going on on my laptob's screen, i realized it was indeed, the ubuntu desktop.. how can i make the ubuntu desktop come out on my external monitor instead of on the laptob screen?

EDIT: this was on the live cd of ubuntu 8.10. on the ubuntu i have installed, i don't get flashing colors, i just get the x server error. just thought i would clear that up, sounded kind of confusing to me..

---

### Post by fistfullofroses on 2008-12-18
Well, with using an external monitor, you ought to some function keys on your laptop keyboard that will switch to using an external monitor only. On mine it's fn+f4

---

### Post by Spitz13 on 2008-12-18
> **fistfullofroses said:**
> Well, with using an external monitor, you ought to some function keys on your laptop keyboard that will switch to using an external monitor only. On mine it's fn+f4

i tried that, it only switched between the external monitor showing the flashing colors and the external monitor being off, but the desktop would always be on the laptob's messed up screen :confused:

---

### Post by fistfullofroses on 2008-12-18
Ok, so go ahead and as soon as it starts displaying funky colors you need to press ctrl+alt+f2
then you need to type "sudo killall gdm"
then refer to my first post.

---

### Post by Spitz13 on 2008-12-18
> **fistfullofroses said:**
> Ok, so go ahead and as soon as it starts displaying funky colors you need to press ctrl+alt+f2
then you need to type "sudo killall gdm"
then refer to my first post.


it said that the 'configure' option can only be used by root.

how do i use a command as root?

---

### Post by fistfullofroses on 2008-12-18
sudo X -configure

---

