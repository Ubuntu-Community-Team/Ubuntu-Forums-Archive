---
title: "New Laptop - rt73 wifi - no connection!"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by TheOldFellow on 2007-08-09
On my suggestion a friend bought his wife a new (windows-free) laptop (Uniwill L51II3, branded Novatech Revo-Max) for her birthday next week.  We can't get the WiFi working and I need help.  There is TOO MUCH information, and none of it seems to apply.

The WiFi  appears in lsusb as 0db0:6877 which is a MSI build ralink using rt73.  Ubuntu fiesty has loaded the rt73usb driver which appears to be correct.

My friend's wifi router is detected correctly and a request comes up for a WEP.  The router is currently configuered for WEP, the WEP is a 26 character hex number.  We select WEP Hex type the key. Now watching iwevent or dmesg shows the system trying for a while, and then it times out.

Is this a driver problem?  Since the driver correctly ID's the network it doesn't look like it.  What else can I try?  I don't much like the try this approach there ought to be systematic way of doing this.
Thanks in advance.

---

