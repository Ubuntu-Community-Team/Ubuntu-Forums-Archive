---
title: "Canon camera photo problems"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by rlj399 on 2009-06-26
When i try to download pix from my camera to my computer i get this error:
[[IMG]http://img140.imageshack.us/img140/3651/photoerrormessage.th.png[/IMG]](http://img140.imageshack.us/i/photoerrormessage.png/)

anyone know what's wrong??

---

### Post by saj0577 on 2009-06-26
What program you using to try transfer them?

How they connect SD CARD? USB plugged into camera?

Saj

---

### Post by tgalati4 on 2009-06-27
In a terminal post the output of:

dmesg | tail -50

---

### Post by rlj399 on 2009-06-27
im using a usb cable and fspot photo manager

ok thanks i tried putting the command in and this is what i got

[   11.494111] type=1505 audit(1246123635.339:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2176
[   11.537249] type=1505 audit(1246123635.383:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2180
[   11.537357] type=1505 audit(1246123635.383:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2180
[   11.537399] type=1505 audit(1246123635.383:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2180
[   11.537442] type=1505 audit(1246123635.383:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2180
[   11.656518] type=1505 audit(1246123635.503:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2185
[   11.656675] type=1505 audit(1246123635.503:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2185
[   11.683439] type=1505 audit(1246123635.527:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2189
[   14.789532] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.789535] Bluetooth: BNEP filters: protocol multicast
[   14.802593] Bridge firewalling registered
[   16.313345] ppdev: user-space parallel port driver
[   17.210317] [drm] Initialized drm 1.1.0 20060810
[   17.216229] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.216234] pci 0000:00:02.0: setting latency timer to 64
[   17.216528] pci 0000:00:02.0: irq 2296 for MSI/MSI-X
[   17.217021] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   17.229799] [drm:i915_setparam] *ERROR* unknown parameter 4
[   20.156125] sky2 eth0: enabling interface
[   20.156993] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.157748] iwlagn 0000:05:00.0: firmware: requesting iwlwifi-5000-1.ucode
[   20.651532] Registered led device: iwl-phy0:radio
[   20.652348] Registered led device: iwl-phy0:assoc
[   20.652375] Registered led device: iwl-phy0:RX
[   20.652391] Registered led device: iwl-phy0:TX
[   21.838763] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   21.850070] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.866061] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.288543] eth0: no IPv6 routers present
[   33.607137] CPU0 attaching NULL sched-domain.
[   33.607142] CPU1 attaching NULL sched-domain.
[   33.624597] CPU0 attaching sched-domain:
[   33.624601]  domain 0: span 0-1 level MC
[   33.624604]   groups: 0 1
[   33.624608]   domain 1: span 0-1 level CPU
[   33.624611]    groups: 0-1
[   33.624615] CPU1 attaching sched-domain:
[   33.624617]  domain 0: span 0-1 level MC
[   33.624619]   groups: 1 0
[   33.624622]   domain 1: span 0-1 level CPU
[   33.624625]    groups: 0-1
[   73.537775] CPU0 attaching NULL sched-domain.
[   73.537780] CPU1 attaching NULL sched-domain.
[   73.552086] CPU0 attaching sched-domain:
[   73.552089]  domain 0: span 0-1 level MC
[   73.552091]   groups: 0 1
[   73.552095] CPU1 attaching sched-domain:
[   73.552097]  domain 0: span 0-1 level MC
[   73.552098]   groups: 1 0
[  416.170502] npviewer.bin[3704]: segfault at ff9bea2c ip 00000000ff9bea2c sp 00000000ff969d2c error 14

---

### Post by tgalati4 on 2009-06-27
Well, at 416 seconds since bootup, you experienced a segfault (crash) of the program npviewer.bin.

From your posted screenshot, it looks like you are using FSpot.  Perhaps try a different photo application and watch dmesg for errors.  

Plug the flash card into a reader and watch for dmesg errors.  You want to make sure the card doesn't have errors without the camera.  If the card has errors, then it's not clear how the camera or FSpot will handle them.

---

### Post by rlj399 on 2009-06-28
I tried putting the memory card directly in without the camera and i still get an error message, does this mean im screwed??

---

### Post by tgalati4 on 2009-06-28
sudo apt-get install testdisk
man photorec

---

### Post by tgalati4 on 2009-06-28
sudo apt-get install testdisk
man photorec

---

### Post by rlj399 on 2009-06-29
whats that do?

---

### Post by alphacrucis2 on 2009-06-29
> **rlj399 said:**
> whats that do?

I have no idea why they recommended that. Testdisk/photorec is a program for recovering data from a corrupt disk drive. Doesn't appear to have anything to do with your camera problem.

---

### Post by alphacrucis2 on 2009-06-29
A quick google suggests that npviewer.bin has something to do with adobe flash player. Looks like it crashed with a seg fault. Probably nothing to do with your camera problem though. You may want to make sure you have an up to date version of the Firefox Flash plugin.

Back to the camera problem. It appears that it tried to retrieve a photo from the camera called img_1019.jpg to /home/roberto but could not locate the file on the camera memory card. So maybe testdisk/photorec does become useful if there is a problem with the file system on the SD card. What happens if you try to view that photo using the camera's own viewer?

---

### Post by tgalati4 on 2009-06-29
The OP says the error happens with the flash card alone (without the camera).  Photorec can pull images off of the card using a low-level technique that does not rely on the file system.

Grab the pictures off of the card.

Reformat the card in the camera.

Take some test pictures and see if fspot works ok.

---

### Post by rlj399 on 2009-06-30
the pix were viewable through the camera viewer
ok everythings working now guys, thanks, not sure if it was because of that command or not though

---

