---
title: "Alternating between Wired and Wireless"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by Tahi_Kiwi on 2007-06-12
How do I configure Ubuntu 7.0.4 for wireless internet connection when wired is already set up? (Wired connection was set up automatically during Ubuntu installation.)

Ubuntu runs wired connections OK, but when I move my PC to another location, such as where there is a wireless setup, Ubuntu isn't configured for that because when I set it up, I was using a wired connection. Curiously, when I try to connect wirelessly through Ubuntu, I get a message that the wired connection is connected even though there are no Ethernet cables attached to the PC.

I know that my wireless connection is correct, because my Windows XP Pro session works. XP works seemlessly with either wired or wireless connection. We cannot have that!

---

### Post by crazy_vyper on 2007-06-13
you can, have you installed and tried setting up "ndiswrapper" ?

if you don't use ndiswrapper, and your device doesn't supply 'nix drivers, then your not going anywhere fast :P

however if i misunderstood, then you should be able to disable wired networking, then enable wireless. If your using the default theme for 7.04 Feisty, then if you check the two computer icon with either a single left or right click, you can enable of disable wired networking, and wireless when you have ndiswrapper installed/modprobe(d)

---

