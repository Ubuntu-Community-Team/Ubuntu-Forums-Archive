---
title: "Gigabyte Z390 I AORUS PRO board ethernet not working with 16.04 after install"
date: 2019-05-20
forum: Networking &amp; Wireless
---

### Post by doktorOblivion on 2019-05-20
I have a new z390 board with the i7 installed and when I install xubuntu 16.04 the ethernet does not work.  The same happened with Win10 Pro, but the drivers shipped with the CD fixed it.  Is there a driver or new xubuntu version that fixes this?

---

### Post by Autodave on 2019-05-20
First off, 18.04 is the newest LTS version and quite possibly will correct the problem that you are experiencing.  I would suggest trying that first. In fact, you could make an installation medium and boot off of that. When prompted to either try or install, choose the TRY and see if you ethernet works. If it does, then proceed to install it.

---

### Post by doktorOblivion on 2019-05-20
yeah, was thinking of that. Will download the latest iso give it a shot. Let you know.

---

### Post by doktorOblivion on 2019-05-21
Okay, I have tried the latest 18.04 LTS 64amd download installer and ran into two separate issues, neither of which have anything to do with this problem (I guess I should post these on the separate general installer forum?)

1. There appears to be a problem with the installer payload, is it actually missing the file indicated in the message below? Is it some kind of UEFI issue or related to my BIOS version, etc?  I have tried installing the bootloader on other partitions, same issue.
[ATTACH=CONFIG]283296[/ATTACH]
2. There appears to be a problem with the installer, aside from the issue above, when I click on the "Close" button after it has gone "casters up", nothing happens, it does not end, nothing. I would have expected it to restart the system or just give me a new dialog saying the installation has ended in error, etc...
[ATTACH=CONFIG]283298[/ATTACH]

The funny thing is the Xubuntu 16.04 completed successfully, but that has the downlevel ethernet support and does not work so is non-operational. Any help appreciated on how to proceed.

---

### Post by Dennis N on 2019-05-21
Xubuntu 18.04.2 is available with a newer kernel - 4.18. Possibly some updated drivers. You might try this release.

---

### Post by doktorOblivion on 2019-05-21
> **Dennis N said:**
> Xubuntu 18.04.2 is available with a newer kernel - 4.18. Possibly some updated drivers. You might try this release.

This did in fact fix the issue. Of coarse there are other issue like post-installing the nvidia drivers, etc... but those are separate (I guess no one expects xubuntu to install clean on the first go around).

---

