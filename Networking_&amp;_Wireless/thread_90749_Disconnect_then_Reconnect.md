---
title: "Disconnect then Reconnect"
date: 2005-11-15
forum: Networking &amp; Wireless
---

### Post by Eyebolt on 2005-11-15
So I got my DWL-G510 going...it's detected as ath0.

The problem I'm having now is it constantly disconnects and then a second or two later reconnects according to the network monitor. According gtkwifi it modulates between like 50% signal and 0% at the same interval.

Any idea what's going on? I'm pretty well new to this, so any help would be great.

Thanks

---

### Post by mlomker on 2005-11-15
I'd look in **dmesg** to see if there are errors.  Are there other wireless devices or access points in your area?  Interference can cause that issue...there are so many cordless phones, TV senders, and access points on those frequencies now that it can be tough...maybe try a different channel on your access point?

---

### Post by Eyebolt on 2005-11-15
Well...I do have a laptop...and 2.4GHz phone...but...it works fine in windows. So I would doubt that it's a hardware/interference issue.

---

### Post by PaganHippie on 2005-11-15
Get rid of 'network monitor.' I had the same problem & it went away when I uninstalled the interloping layer of software. Drove me nuts for an evening until I figured out what was going on.... Apparently 'network monitor' keeps resetting the network settings looking to improve throughput. Unfortunately, in cases like yours and mine, it just ends up turning WiFi off after a few seconds.

---

### Post by Eyebolt on 2005-11-18
Well...I tried that...no luck.

---

### Post by Lambert on 2005-11-18
Try this. It will definitely rule out interference.

First find the address of your router xx:xx:xx:xx:xx

You can do this with iwconfig when you're connected. or sudo iwlist ath0 scan

Then type

sudo iwconfig ath0 ap xx:xx:xx:xx:xx commit

After testing this and if no results then...

Secondly, when you run iwconfig what is your power management status say. 
If it doesn't say off then try it with power off and see if it helps

sudo iwconfig ath0 power off

---

