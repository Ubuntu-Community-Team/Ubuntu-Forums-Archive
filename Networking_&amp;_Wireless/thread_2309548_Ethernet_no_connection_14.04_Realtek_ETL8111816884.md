---
title: "Ethernet no connection 14.04 Realtek ETL8111/8168/8411"
date: 2016-01-11
forum: Networking &amp; Wireless
---

### Post by UniqueActive on 2016-01-11
**Hey there!**

I am having trouble getting Ubuntu to recognize my Ethernet. When executing "lspci", it lists my Ethernet controller as

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. ETL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

(It's not an actual PCI Card, it's in my motherboard but seems to work through a PCI lane.)

 After repeatedly telling me that it's disconnected, it just shuts off. After some time, but only in some cases, it showed me that it's connected but when trying to load anything up, after 5 minutes of loading it would become clear that that was not true, and when clicking on "Wired Connection 1" again, it goes back to telling me that it isn't connected. (Works perfectly fine on win.) I obviously can't just install updates or get packages, because I don't have internet connection on the computer, so I would really appreciate your help! I can try posting some returns to commands but because I don't have a camera at hand and I can't copy it directly, doing it manually would just take way too long, sorry. I can do that on demand though, if it helps you help me. Thanks in advance!

UniqueActive

---

### Post by UniqueActive on 2016-01-12
Please guys, I need you to help me get my system going, this is the only system I have and I need it for work. I only need internet access so I can do anything at all and at this point, I am willing to do everything for that purpose.

---

### Post by UniqueActive on 2016-01-21
Alright, I found the solution.
I own the Gigabyte GA-970A-UD3P motherboard for socket AM3+ with my AMD FX-6300 and it turned out that just a simple change in BIOS settings solved everything.
In the Peripherals menu, you should find an option to enable IOMMU, which is disabled by default. Windows seems to figure that out on its own but I had to manually change it to "Enabled" to get my USB 2.0 and Ethernet ports to work.

---

### Post by Deiphobus on 2016-01-29
Yes! Yes! Thank you so much UniqueActive! I have the same set up as you, Gigabyte GA-970A-UD3P Motherboard and AMD FX-6300. I also had the same issue where the Ethernet would try to connect over and over again with no success even though it works fine when I boot windows. Your solution works!

---

### Post by Johnathan_Simpson on 2016-01-31
> **UniqueActive said:**
> Alright, I found the solution.
I own the Gigabyte GA-970A-UD3P motherboard for socket AM3+ with my AMD FX-6300 and it turned out that just a simple change in BIOS settings solved everything.
In the Peripherals menu, you should find an option to enable IOMMU, which is disabled by default. Windows seems to figure that out on its own but I had to manually change it to "Enabled" to get my USB 2.0 and Ethernet ports to work.

YOU ARE THE MAN UniqueActive. same issue with the 990fxa-ud5 rev 3.0 with fx-4350. got a bunch bus errors with squash errors. toggled that seting and done boots just fine.

---

### Post by marconator on 2016-02-18
On a Samsung NP900X3A with the same Ethernet-Chipset I changed something similar in the BIOS after Ubuntu 14.04 LTS refused to connect to wired connections. I had to activate the function to boot up by "PXE" (Power over Ethernet Protocol) in the BIOS. 
it worked! Thanks for the lead!

---

