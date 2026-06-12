---
title: "usb modem does not work in virtual box"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by aby_fulcrum on 2008-11-24
I have xp guest in virtual box where airtel usb modem Huawei Technologies Co., Ltd. E620 USB Modem is installed without any difficulty. However when I click on connect, I get a message that says 'device not connected or is not available'. how do I solve this?

---

### Post by theluddite on 2008-11-30
Here's how I did it with Virtualbox GTK.  While selecting my VM in the left pane on VirtualBox, I clicked on the "Devices Tab" in the right pane, then changed NIC to "NAT", selected the first NIC device and ensured the "Cable connected" box was checked.

Then in my XP guest I set up the internet connection using the Wizard as per normal.

Hope this helps!

---

