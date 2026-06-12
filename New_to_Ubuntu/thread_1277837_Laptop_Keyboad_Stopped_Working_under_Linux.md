---
title: "Laptop Keyboad Stopped Working under Linux"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by imaginal on 2009-09-28
My laptop keyboard no longer works in Ubuntu 9.04. It has been working for months under this distribution, and I've never had problems with it under other releases. It also is nonresponsive with every live CD I've tried, including 7.04 and 8.10. These used to work too.

In GRUB and the Bios, the keyboard works. It also works under (dual-booted) Windows 7.

A USB keyboard works fine, and is how I'm typing this. The build-in keyboard does not.

The only change I've made to my system was resizing my linux partition (shrinking it by 20gb. There was over 35gb free). Could this be a swap partition thing? I am lost as to why even my live cds can't make the keyboard work.

Any ideas on how to get this back? Thanks everyone!

---

### Post by humphreybc on 2009-09-28
This is really weird! So it doesn't work under LiveCDs either? Hmm... does it work in the recovery mode console?

ie, boot up to GRUB and press escape, then choose your latest kernel (recovery mode), then drop down to a root shell.

If it works in there, type these two commands:

lspci
lsusb

and then find your listing for keyboard... I think it should be there in one of those commands. If not, well, at least it's working in virtual terminal so we can start looking at the GUI/X/Gnome as the problem...

... and if it doesn't work in the terminal... wtf!

---

### Post by imaginal on 2009-09-29
No, the keyboard would not work in recovery console. The second I started any form of linux, the keyboard would become nonresponsive. This includes hitting the caps lock button and having the light come on.

In Windows 7, the keyboard works, but I noticed the caps button still wouldn't turn on. After hitting it a few times, it would make my mouse move.

So I turned my laptop up-side-down and shook it in a fit of anger. Like magic, the caps light comes on, and my keyboard works in Linux again. :confused:

I hear a rattling screw, and blame this weird hardware problem on the monkeys at BestBuy, whom I gave my laptop to to fix a loose bearing in a fan 7 weeks ago. They returned it after 3 with a new keyboard (?) and forgot to plug in my touchpad. I returned it, waited 3 more weeks, and here I am.

My best guess is a partially plugged in keyboard, but to keep from voiding my warranty, I can't check it. When I take it in, they recommend I return the system to factory settings (vista) or download new touchpad drivers from hp.com... Maybe voiding my warranty would be an upgrade.

I will post again if this turns up again and has anything to do with linux. I doubt it does, and bet it comes up again.

---

### Post by humphreybc on 2009-09-29
Yeah hardware problem. Just unscrew your laptop carefully and have a look to see if you can fix it. Warranty's are a pain in the bum, they try to find ANY reason they can to not fix it under warranty... including installing another OS.

Good Luck!

---

