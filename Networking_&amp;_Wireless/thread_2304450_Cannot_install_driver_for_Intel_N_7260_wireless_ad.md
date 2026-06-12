---
title: "Cannot install driver for Intel N 7260 wireless adapter"
date: 2015-11-26
forum: Networking &amp; Wireless
---

### Post by dylan48 on 2015-11-26
Hi,
Please if anyone can help me with this, I have been trying to find a workable solution for over a month.
I recently bought a new computer containing an Intel PROSet Wireless-N 7260 adapter.
I have Windows 7 and Ubuntu dual boot setup. The adapter works fine in Windows.

I have followed numerous online articles and forum posts suggesting different ways to install the driver, but none work, and the adapter remains non-functional in Linux.

The three general approaches (although I have tried several variations based on different forum posts) that I have tried are:

1) Download the driver from Intel website, and copy it into /lib/firmware                            (this is the approach suggested by Intel)
2) Install mod kernel in order to load the driver                                                                (shouldnt be necessary as I have linux kernel 3.19 running, but tried it anyway, to no avail)
3) Download windows wireless driver loader, and extract windows driver for device, then add to the program. In this case the application does not recognise the driver/hardware  /  says incompatible

I am really at a loss here, so any help would be greatly appreciated. Detailed instructions of the best way to fix this would be greatly appreciated, as I am not an advanced user.
Alternatively, could anyone recomend a wireless adapter that is known to work under ubuntu 14.04, that fits the ngff/m2 socket?

Many thanks

---

### Post by westie457 on 2015-11-26
Have you tried the driver from here? [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi)

The section of interest to you is about half-way down the page.

Hope this helps.

---

### Post by jeremy31 on 2015-11-26
Too many possibilities, please see [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and post the wireless-info.txt file, you can also paste the contents of the file at paste.ubuntu.com and post the URL

---

