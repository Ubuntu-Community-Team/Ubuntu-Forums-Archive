---
title: "WUSB54G Linksys USB Wifi dongle Driver Help"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by iomr on 2008-08-19
Hello,

I'm basically a huge noob to ubuntu and linux, but I am trying to find my way around. Just installed the OS on a secondary computer and am trying to figure out how to access my wireless network.

I have tried using ndisgtk to install the .inf driver files (I have downloaded several versions from the Linksys website, as well as the .inf straight off of the installation CD that came with the product) and receive an "Invalid Driver!" message in ndsigtk. Any ideas on an alternate way to install this product so I will be able to access my wireless network?

Thanks in advance.

---

### Post by Skofo on 2008-08-20
There are different WUSB54G models. v1, v2 and v4, I think. Check if your driver corresponds to the one you're using.

Identify your adapter with 'lspci' and [check with which of these corresponds with your adapter's ID.]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/#l")

---

