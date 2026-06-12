---
title: "[SOLVED] Intel 4965 iwlwifi wireless with 802.11a?"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by jblackthorne on 2008-02-20
There are a number of older threads out there regarding the Intel 4965 iwlwifi driver.  Thankfully, I installed Gutsy 7.10 64bit , ran the updates, and the current kernel, 2.6.22-14-generic, already includes the iwlwifi drivers.  Hence, my HP dv6700t had wireless 802.11g working flawlessly right out of the box.  The only issue is that I am not able to see any 802.11a networks.

For example, running “iwlist wlan0 scanning”, shows 802.11g networks in the area, but none of the 2 802.11a, including mine.  To simplify and rule on out WPA issues, I disabled all authentication on the 802.11a network.  Still, the 802.11a band is not visible in iwlist or nm-applet.  Next, I booted to the default W$ndows partition on the same exact laptop and the 802.11a connects just fine.  This tells me that all hardware is good, but there is some issue with the iwlwifi config or driver.  

Has any one had any luck with 802.11a?  If so, any ideas as to what might be wrong with the iwlwifi diver?

---

### Post by jblackthorne on 2008-02-25
I solved my own question.  The problem is that the Intel 4965 drivers currently does not properly support older access points, Wi-Fi certified or not.  I tested with:

* Most current Linux releaes 1.2.25
* Most current Vista drivers too

Here are more details if any one is interested:

[http://ubuntuforums.org/showthread.php?t=702593](http://ubuntuforums.org/showthread.php?t=702593)

---

