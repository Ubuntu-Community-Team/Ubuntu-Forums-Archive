---
title: "Dlink dwl-g122 A2 and rebooting?"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by asousa on 2007-09-30
Hi everyone...

very new to ubuntu...  after spending a few hours digging online I have finally got ndiswrapper installed with my dlink dwl g122 usb wireless.  

What is not working for me though is when I reboot it doesn't start on its on.   I have to manually run 

```
sudo modprobe ndiswrapper
```

I added ndiswrapper to my /etc/modules file, i even added blacklist prism54usb to the /etc/modules.d/blacklist file.

Any other thoughts?

---

