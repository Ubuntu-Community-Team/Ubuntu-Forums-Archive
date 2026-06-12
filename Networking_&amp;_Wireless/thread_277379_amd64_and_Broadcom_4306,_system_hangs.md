---
title: "amd64 and Broadcom 4306, system hangs"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by brunom9 on 2006-10-14
Well, seems there's more of us having problems with ubuntu 64 and broadcom wireless chips.

Here's my experience.

Installed ubuntu amd64-k8 on a fakeraid setup. Not an easy task, not an impossible one. Configured the entire system (wide monitor, DELL 2007WFP, not all the resolutions recognized, which is a another task to configure). Got wired network, boot sequence right, etc.

Extracted the firmware from wl_apsta.o (prefer the native linux approach rather than going the windows XP driver with ndiswrapper), went ok. Launched the network-manager applet, BUM! system hangs! Rebooted, system hanged after logon.

Went into recovery mode, uninstalled bcm43xx-fwcutter and the firmware, system back online. Tried the install again, same thing. System hangs on the network-manager. Once again, recovered the system and tried to install the card, but now extracting the firmware using bcm43xx-fwcutter on the broadcom 64-bit driver. System hanged again on the network-manager.

Did the recovery, then tried something else: boot up the liveCD. Installed bcm43xx-fwcutter on the system running from the liveCD (ver amd64 6.06), extracted the firmware from wl_apsta.o, fine. Went into System->Administration->Network, found my card listed, went into properties, gave my ESSID, ok. Turned on the card, system hangs!

Then did the same sequence, trying this time with the ndiswrapper approach using the Broadcom 64-bit drivers. Installed ok, blacklisted, card is online and hardware detected. However, cannot scan for any network, card doesn't even get listed on System->Administration->Network. Installed the network-manager, no luck, no wireless support.

Went back to the installation board, fakeraid install of 32-bit ubuntu, went ok. Got to the wireless connection, once again with the linux drivers and bcm43xx-fwcutter. Works great!

From this experience:

1) There are problems with ubuntu 64-bit and the broadcom driver.
2) The problem arises as the card is being detected or connecting to the network (network-manager hangs, system hangs on activating).
3) Broadcom 64-bit driver has no support for the card/chipset using ndiswrapper.

FYI, the card I'm installing is a Belkin F5D7001, reported form lspci as:

Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Hope next ubuntu 64-bit release has fakeraid support and Belkin or Broadcom finally gives users a 64-bit driver.

Cheers from Mexico another open-source lover,

Bruno

---

### Post by scalofrio on 2006-11-08
Anything new about Broadcom Corporation BCM4306 on Ubuntu 6.10 amd64???

---

### Post by hms_dread0 on 2006-11-13
This issue is still present in 6.10.  Went through the same song and dance in the 64 bit version with similar results.  ](*,)

---

