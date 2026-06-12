---
title: "WPA2 Enterprise Wi-Fi problems"
date: 2015-10-22
forum: Networking &amp; Wireless
---

### Post by victor66 on 2015-10-22
[COLOR=#000000][FONT=arial black]Hi all

I am having trouble with the wi-fi on my desktop. I am able to connect to my school network for about a minute, but then the connection dies and I am unable to connect again until I restart. The wifi worked fine at my house. Could anybody help me figure out what exactly is wrong?

I am using a NetGear WNA3100 WiFi USB adapter

Thanks

edit* Forgot to mention, the wifi is still shown as connected, however my internet won't work[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2015-10-24
Hi and welcome.

You're using an unsupported hardware with some sort of "emulator" (not really, but can be constructed as such, in layman terms) plus Windows drivers.
There's no point in troubleshooting what's doomed to fail, completely or only partially, sooner than latter. A new, much better and supported WiFi dongle cost $10 or less.

---

### Post by kurt18947 on 2015-10-25
It's certainly possible that Vladlennin is correct, especially if you're using NDISwrapper to make your WNA3100 work. Another possibility is that your school's wifi system uses hardware or software that only works with Windows & Mac. There have been reports of that on this board. The fact that you're able to connect at all makes that seem unlikely but then I've never dealt with WPA2 enterprise authentication systems. Do you know of any other students that are connecting successfully using a non Windows/Mac machine?  I'd probably get a 'works-out-of-the-box' adapter as suggested and try that - remove one layer of complexity. If that doesn't work, is your school's IT support friendly or hostile toward linux users?

---

### Post by praseodym on 2015-10-25
All of the above is true! You may want to change the router mode to b/g only if you have access to do so. Alternatively, try *this* driver with Ndiswrapper:

[https://media-cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)

---

