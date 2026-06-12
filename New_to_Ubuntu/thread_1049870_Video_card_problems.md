---
title: "Video card problems"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by bc003 on 2009-01-25
I'm having problems getting basic video function. When I start the computer the bios screen comes up just fine, but as soon as the splash screen should come up I lose video and the monitor shuts down. About 30 sec. later the monitor comes back on but is black. When I remove the card the onboard video works fine. I'm running 64bit ubuntu 8.10, on intel, with an nVidia NVS 290 x1 PCIe. I've already tried the (Option "UseDisplayDevice" "DFP") In xconf. Makes no diff. I do notice that I get a blinking curser on a black screen if I try to enter bios setup. But the curser does nothing. I don't know if it makes a diff. but this machine is a dell poweredge 830 server. Thnx in addvance Bill

---

### Post by scarf on 2009-01-25
> **bc003 said:**
> I do notice that I get a blinking curser on a black screen if I try to enter bios setup. But the curser does nothing.

this sounds like an bios setting.  mosts bios's have an option to use onboard video or pci-e video, does yours?  try setting it to pci-e if it does.

> I don't know if it makes a diff. but this machine is a dell poweredge 830 server.

yes that is important, and thank you for sharing, because if the above suggestion didn't help i might suggest to reset your bios by following the system's instructions (usually there is a jumper, or the power and system battery need to be removed...).  since this is a server i would take extra precautions when resetting the bios, especially if there is a RAID array defined....

if that doesn't help i would try another video card.

---

