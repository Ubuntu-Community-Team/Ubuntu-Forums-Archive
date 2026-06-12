---
title: "removing wireless drivers"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by TreeFinger on 2008-08-26
[http://ubuntuforums.org/showthread.php?t=267698](http://ubuntuforums.org/showthread.php?t=267698)

I want do do the same thing as the poster of that thread, above.

My friend has ubuntu 8.04, which I set up for him, on a laptop. I never was able to get the wireless working for him correctly and tomorrow I plan on doing so. When I set up the laptop for him I didn't have access to a wireless connection.

I believe I understand how to install the Ndiswrapper but I am wondering how I can remove all previous wireless card drivers?

Here is the output from lspci | grep Ethernet

```

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

When he first took the laptop home and tried to get on his wireless it was not working so I told him to try the usb wifi adapter he had laying around. that worked for a little but now he is going to be taking the laptop to campus and doesn't want to have to worry about losing the usb wifi adapter so I would like to get the laptop in proper working order.

Could someone please help find or explain the way to properly remove drivers? I'll have to remember to bring a linux distro on a cd when I get his computer.

Thank you, in advance.

---

### Post by TreeFinger on 2008-08-27
bump.

---

