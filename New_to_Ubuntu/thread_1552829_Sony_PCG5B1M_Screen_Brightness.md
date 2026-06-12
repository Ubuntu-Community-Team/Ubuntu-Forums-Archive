---
title: "Sony PCG5B1M Screen Brightness"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by Moriarty123456 on 2010-08-14
Hi Ubuntu Pals,

I'm fairly new to Ubuntu and I have an issue with screen brightness. Not a big issue, but one of those that chips away at my soul, time after time, weakening my vital spirit.

I have a Sony PCG5B1M (aka the VGN-B1VP), in a fashionable off black. In 9.10 the screen starts off dim, but I can adjust via Fn + F6. Not a big issue, but you have to do it over and over again, each time, over and over, over and over, over and over, over and over, over and over, over and over - get the picture?

I'm looking for a way to have the screen set to full brightness on start-up. I've found that the backlight functions are at:

/sys/devices/virtual/backlight/sony

where there are files with :
actual_brightness 7
bl_power 8
brightness 7
max-brightness 7
as well as folders power, subsystem, and a file called uevent.

When I adjust the brightness with the function keys, the brightness and actual brightness changes - so these, i presume are the variables I need. It's at zero on start-up. So how do I set the brightness to 7 as a default setting at start-up?

Many thanks. 

P.s. in 10.04 - which I tried and would love to upgrade to - the function keys are disabled in the live CD. If I knew how to change brightness in 9.10, would it be the same in 10.04?

P.P.S also I should've mentioned that one of the reasons I stumbled upon Ubuntu is that the screen was so dark (and computer so slow) when I was running windows, that I thought, to hell with it, let's sacrifice some virgins and try Linux. To my delight (but not of the virgins, obviously) the screen brightness now 'worked', making my computer usable again. Huzzah!

---

### Post by Moriarty123456 on 2010-08-14
P.P.S. I've also tried playing with PuppyLinux, and Peppermint and the screen's dull with those too. If I found the solution for 9.10 would it work across all Linux Distros?

---

### Post by Moriarty123456 on 2010-08-14
Quick update:

I've 'solved' it - somehow! Just in case anyone else is having the same issues I went to the boot menu (F2 on start-up) and restored the defaults there, evidently these had been messed up somehow, sometime, because hey presto the screen's bright again at startup. 

In case this doesn't work for you, perhaps try investigating 'xbacklight' which is some sort of Linux add-in, that has good write-ups. It would've been my next move...

---

