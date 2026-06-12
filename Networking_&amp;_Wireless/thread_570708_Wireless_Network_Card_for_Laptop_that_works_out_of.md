---
title: "Wireless Network Card for Laptop that works out of Box"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by dicecca112 on 2007-10-08
[FONT=Arial][SIZE=2]Is there any [/SIZE][/FONT][FONT=arial][SIZE=2]PCI-Express Mini Network Adapter that works out of the box with no muss or fuss with Ubuntu?  I've done some research and can't seem to find much.  I don't want to have to use a USB slot either.
[/SIZE][/FONT]

---

### Post by stalker145 on 2007-10-08
> **dicecca112 said:**
> [FONT=Arial][SIZE=2]Is there any [/SIZE][/FONT][FONT=arial][SIZE=2]PCI-Express Mini Network Adapter that works out of the box with no muss or fuss with Ubuntu?  I've done some research and can't seem to find much.  I don't want to have to use a USB slot either.
[/SIZE][/FONT]

I've personally found all three Atheros chipped cards I've put into laptops to work flawlessly. I can't tell you name brands since I've bought all of my cards open-box.

---

### Post by dicecca112 on 2007-10-08
even though you can't provide me brands, I might be able to located something with that chipset, thanks for the input

---

### Post by Lambert on 2007-10-08
WM3945ABG mini-pcie card has support in 7.04 and next upcoming release.

If you want to search before hand, search for ipw3945. That's the driver for devices with this chipset. You can read others experience as with any device, there are some that have problems.

---

### Post by stalker145 on 2007-10-08
> **dicecca112 said:**
> even though you can't provide me brands, I might be able to located something with that chipset, thanks for the input

No problem. FYI, my last one was bought for $16. Nice deal if you ask me ;)

---

### Post by kevdog on 2007-10-08
The specific atheros chipsets (not all of them) that are mentioned on the madwifi website work out of the box via the restricted-drivers-package.

Some realteks may work out of the box, but they are buggy.

ipw's also work, but alas, there are problems with these too!

Again I would go for some atheros chipset, but you need to crossreference whatever you choose with the specific model #'s listed on the madwifi website.

---

