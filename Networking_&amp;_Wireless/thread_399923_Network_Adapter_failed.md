---
title: "Network Adapter failed"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by markd0618 on 2007-04-02
I'm teaching an introductory operating system class and decided to use the Ubuntu Live CD to let the students check out Linux. Everything went well loading Ubuntu. All the hardware on the Dell desktop PCs was supported. After rebooting the machines to Windows XP, the network adapters (VIA Rhine II Fast Ethernet adapters built into the motherboard) all failed to work. Windows does not recognize the adapter hardware at all. Rebooting with the Ubuntu Live CD is no help - the network still doesn't work. Any idea what happened?

---

### Post by digital_sabotage on 2007-04-03
...just a thought ...perhaps check your bios settings?  ...i have one comp that seems to glitch with ubuntu ...if i do a restart the sound card gets disabled in bios and i have to re-enable ...if i do a full shutdown and then power back on the card stays enabled in bios

...anyhow  ...i'm dual boot and if i don't have it enabled in bios the hardware isn't detected by either os

...good luck with it:-)

---

### Post by markd0618 on 2007-04-03
Thnaks... I went into the BIOS and selected "optomize settings"... no luck. I'll take a closer look at it in the morning.

---

### Post by markd0618 on 2007-04-03
Well, I took a closer look at the BIOS on the machines that failed and compared it to the still working machines that we did not load Ubuntu on. Apparently, Ubuntu corrupted the BIOS. There is no longer an entry in the BIOS for a network adapter card at all. Therefore, neither Windows nor Ubuntu detect the on-board network adapter when booting. In the BIOS, the adapter is not disabled, it's simply not there at all. Will try reflashing the BIOS...

---

### Post by markd0618 on 2007-04-03
By the way, I misquoted in my original post. This problem is NOT on a Dell PC. It's a homebrew PC using a P4M800PRO-M motherboard (?) with AMI v02.59 BIOS.

---

### Post by markd0618 on 2007-04-03
Resetting CMOS by moving the jumper on the motherboard fixed the problem.

---

### Post by digital_sabotage on 2007-04-04
...must be a relief  ...i suppose one or both of us should file a bug report

---

