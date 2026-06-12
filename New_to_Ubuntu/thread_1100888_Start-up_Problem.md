---
title: "Start-up Problem"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by sidewinder12s on 2009-03-19
Im New to Ubuntu and i just installed 8.10 on my laptop running Dual-boot with XP. When i get to the Log-in Screen i enter my User and Pass and then it goes to an Orange Screen and just sits there. i dont have any idea what its doing. Any help would be great.

---

### Post by mocoloco on 2009-03-19
When you see the login screen click on the options at the bottom, and select "Session". Choose "Failsafe gnome" I think it's called.  See if you can get in that way. If that works, you probably need to install video card drivers, under System -> Hardware Drivers.

---

### Post by sidewinder12s on 2009-03-19
Ive tried that and it seems to do the same....

---

### Post by cwsnyder on 2009-03-19
A couple of recommendations:
a) Try Ubuntu in the Live mode (try before installing, from the boot menu of your install disk) to make sure that it operates without problems in this mode before installing to HD.
b) Press the <Esc> key during the orange screen, to follow the complete listing of what happens during the boot process to find out where the boot process is stalling out.

---

### Post by sidewinder12s on 2009-03-19
Ok, im trying Live right now since i never did that, but even during the Orange screen i hit esc. and it did nothing.

---

### Post by sidewinder12s on 2009-03-19
Ok, it gave me 2 firmware Errors on the Live CD but i couldnt make them out. and now in the Live the screen is off

---

### Post by cwsnyder on 2009-03-20
It sounds like your graphics system is not fully compatible with the kernel of Intrepid Ibex.  You may need to change your video card.  ATI, nVidia, and Intel based video cards seem to work the best with GNU/Linux systems.

If you cannot get the Live session to work, you will almost be guaranteed to have problems getting any install to work.  You may need to switch distributions to PCLinuxOS, OpenSUSE, Mandriva, or Fedora (for example) to get a Linux which will work with your computer.

---

### Post by blandman3 on 2009-03-20
hey man i am/was having the same trouble.

I am very new to this myself, but I think I figured out how you can do it:

run the live cd

when you get to the screen that has options on installation and stuff stop there

hit F6 and type:

hw-detect/start_pcmcia=false netcfg/disable_dchp=true xforcevesa

hit F6 again and check (by pressing enter) the following:

acpi=off noapic nolapic

press esc, and then press enter

this i found by trial and error (took me a couple of days) and I got my Live CD to run at last!

---

