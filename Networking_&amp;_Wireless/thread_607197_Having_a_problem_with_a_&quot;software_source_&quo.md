---
title: "Having a problem with a &quot;software source &quot; for a package."
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by JoeyM on 2007-11-08
I have an HP pavilion zv5000 laptop with a built-in wireless card. At the moment, the wireless card is "DISABLED". There is a wireless button the laptop, pressing it does absolutely nothing. 

Well, in the Restricted Drivers window, there is a thing called 

"Firmware for Broadcom 43xx chipset family"

I need to enable this driver but when I click to enable it I get 

"The software source for the package

bcm43xx-fwcutter

is not enabled."

**How do I enable that software source thing?**

---

### Post by Lometari on 2007-11-11
Just go to System -> Administration -> Synaptis

Once there select Settings -> Repositories. On the first tab you'lll see 5 checkboxes under the title of Downloadable from the internet.  Check the first four and hit the Close button. Back on the main window hit Reload. You'll see the items there have changed.

Once you've done that you'll be able to download the driver just like you described.

Oh, one more thing: it will prompt you to choose between a location on your hdd and a url, which will be already written on the textbox. Choose the url and you're done!

Hope that helps :KS

---

