---
title: "Linksys WMP54GS not recognized"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by polymath on 2009-08-24
I'm installing ubuntu on a friends computer and he uses a Linksys WMP54GS wireless card. the sys->admin->hardware drivers does not detect the card, so i dug deeper. Long story short, the card is not detected by either the lspci or the sudo lshw -C network techniques. Everything is intel, intel intel. nothing linksys at all. not even any other wireless company.the only non-intel line is the modem. i assume that ndiswrapper won't work if ubuntu doesn't even know a device is there. i can't post the exact output of the above commands as said computer has no internet connection and i'm posting from my own comp (though if need be i can download drivers and such and place them on a flash).

Long story short, can i get help setting up my wireless card? Distro being 9.04 std x86

---

### Post by cariboo on 2009-08-26
Try pulling the adapter out and reinserting it in the slot. It may not be seated correctly.

---

