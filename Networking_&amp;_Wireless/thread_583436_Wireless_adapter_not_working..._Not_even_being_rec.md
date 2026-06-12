---
title: "Wireless adapter not working... Not even being recognized."
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by JLR is me on 2007-10-20
Yes, I've looked at the sticky, and all of the other thread (I know their are a million of them) but my problem seems... Different to everyone elses. I'm using the WUSB54Gv4, and using the windows driver using ndiswrapper. Ndiswrapper recognizes the driver and everything, I've blacklisted the original driver, but it doesn't even recognize a wireless device now. Out of the box Gutsy Gibbon would identify the SSID of my network, and just not be able to connect. Now, I'd assume it should be working fine, but it's even worse then before.

Any help? I'm pretty nubby with Linux, I'm an avid Windows user and know a good bit about macs, but I'm somewhat clueless when it comes to Linux. 

Thanks!

Oh, and this is what ndiswrapper says...

ndiswrapper -l
rt2500usb : driver installed
device (13B1:000D) present (alternate driver: rt2500usb)

---

### Post by JLR is me on 2007-10-20
:(

---

### Post by dingansich on 2007-10-20
I am having the same problem.  ndiswrapper  lists the rt2500usb driver as installed correctly (as per the instructions in the sticky), but according to the Ubuntu network manager I don't even have a wireless interface (Linksys WUSB54G v4) - which I do, and used to at least register before I tinkered with ndiswrapper.  Anyhow, I tried to back out of my tinkering - commented out the additions to my blacklist and interfaces files, even uninstalled ndiswrapper (common and utils) - but that didn't improve anything - my interface still doesn't even register.  Since then I've tried to reinstall ndiswrapper again, but it didn't make a difference.  At one time I could at least see my non-functional adapter ... now I can't even do that.  I am totally at a loss.  Any help is much appreciated as Ubuntu has basically become useless to me.

---

### Post by JLR is me on 2007-10-20
Ok, status update. I got annoyed and went to 7.04, assuming it's just a Gutsy Gibbon error. I redid everything, and at first glance it appeared to work perfectly. I connect into the network (Says that I am connected to the wireless network) but I can't connect to the internet. Any ideas? I'm pretty brainless right now after tinkering with this for so long, it's definately one of the more annoying things I've done in my IT experience.

---

