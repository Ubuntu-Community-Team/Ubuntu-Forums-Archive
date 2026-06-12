---
title: "Having various problems w/ install"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by Psyael on 2010-12-07
First, my specs
Mainboard: Gigabyte GA-E7AUM-DS2H
CPU: Intel dual-core
Video: nVidia 9400 (onboard)
Audio: Realtek ALC889A (onboard)
Display: Old Sony CRT HDTV, hooked up via HDMI/DVI

This system has been running Windows Vista/7 with Media Center as an HTPC reliably since 2008. I am confident that there is no busted memory or other bad components in the case.

This failure happens with **both** Ubuntu and Mythbuntu, 10.10 i386 version.

I downloaded the Live CD and tried to boot to it. Got an error message: "image checksum failed, sorry." Checked md5, it matched. Tried burning again, this time as slow as possible. Same error. On a whim, tossed CD into another PC that has successfully installed Ubuntu in the past and saw installers. The problem seemed not to be on the disc itself but related to hardware.

I decided the best thing to do would be to skip the CD install completely. Took a USB flash, formatted it, and made a startup drive off the ISO using Startup Disk Creator. Booted from USB and this time I got past the checksum error but the screen went to garbage.

I'm thinking that since I'm using an old-fashioned CRT that doesn't transmit data on it's own capabilities like most modern HDTVs with digital outs do, Ubuntu boots into some resolution or other display option that the TV doesn't support.

I'm not sure if anyone has any advice for me on this one? My next plan is to try and install Mythbuntu to an external HDD on another computer, configure it with nVidia's drivers, and then try to boot to it on my HTPC. nVidia's drivers work just fine via Windows, so I think if I can set it up ahead of time to use the commercial drivers instead of the free defaults, I should be in the clear.

---

