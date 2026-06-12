---
title: "Wireless Experience"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by Boyo on 2007-01-01
I have used Ubuntu since the days of 5.10 and had wireless working successfully since upgrading to 6.06 and also in 6.10.

About a month ago, while sitting on the sofa surfing the Internet Ubuntu lost all networking abilities, both wireless and wired.  Did I Install anything, change any config files or add any new hardware?  No!  Despite several restarts I was unable to restore any network connections.

As I had recently backed everything up to external HD, I was quite happy to flatten the disk and reinstall Ubuntu 6.10 with the live CD.

Installation went smoothly, and I was soon up and running with a fresh install and downloading the 100meg or so of updates.  My problem started with getting the wireless drivers to install.  I have a Dell Inspiron 9100 laptop, with a broadcom 1450 Minipci wireless card.  Both the Broadcom driver and Ndiswrapper failed to start the wireless card so I dived into the forums and Google to see if I can find some answers; I installed both the latest version of fw-cutter and Ndiswrapper - perhaps I should add here that I didn't try to install both the drivers simultaneously; at least one was blacklisted at anyone time.

Not knowing what else I could try, I reinstalled Ubuntu again; and again; and again, sometimes trying to install the wireless card before downloading the updates and other times after the updates.

Rolling back to Ubuntu 6.06 didn't provide any progress.  Out of desperation I installed XP just to ensure that I had both the correct wireless driver for fw-cutter and Ndiswrapper and that the wireless card does in fact work!  At this point I really did think that I should stay with Windows!!

Additionally, over the weeks I had problems with the wireless card I tried to upgrade to Fesity on two separate occasions - both of which failed to upgrade properly; despite removing the package dependence conflict in Openoffice.  The updates download and install, however, after logging back into Ubuntu gnome does not start properly instead it just hangs with the orange background screen.

In an old laptop I had a 3com Wireless PCMCIA card, I tried a fresh install of 6.10 with the Dell wireless switched off in Bios.  The 3com card worked fine, however, despite trying the native prism54 driver and Ndiswrapper with the latest driver downloaded from 3com I was unable to get WPA encryption working and I was not prepared to to settle for WEP.

I have another dell laptop with a Truemobile 1300 wireless card.  I took the card out of this laptop and put it into my problematic laptop.  A fresh install of Ubuntu 6.10; install and config of Ndiswrapper 1.8 followed by Network Manager and I was up and running Wireless and WPA!  The double whammy is that when I put the problematic wireless card into my other laptop it worked with no problems!

I guess perseverance really does pay off . . . just wish there was some logic to it:)

---

