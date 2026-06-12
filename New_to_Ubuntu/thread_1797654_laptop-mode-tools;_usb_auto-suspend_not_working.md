---
title: "laptop-mode-tools; usb auto-suspend not working"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by microraptor on 2011-07-05
Hi everybody!
This is my first post on this forum :).
I'm having trouble with laptop-mode-tools, which I initially installed because my computer doesn't  suspend/hibernate when battery levels are low (even though this is set in "power management"). However it brought me two new problems! First, ethernet wasn't working, but I managed to fix it in                                   /etc/laptop-mode/conf.d/ethernet.conf:D. But also, my mouse freezes after being inactive some seconds, which is really irritating. This probably have to do with the usb-auto suspend setting, there are other people having problem with this as well, seems to be a bug ([https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/469517](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/469517)) In /etc/laptop-mode/conf.d/usb-autosuspend.conf, I set CONTROL_USB_AUTOSUSPEND=1 to CONTROL_USB_AUTOSUSPEND=0, to disable it, but it didn't help.:( Again, other people seems to have encountered it ([https://bugs.archlinux.org/task/22909](https://bugs.archlinux.org/task/22909)) On the same page;
"I had the same problem, it was not possible to connect usb, usb ports were 
suspended. 
I had to add the USB ID to the list AUTOSUSPEND_USBID_BLACKLIST."


Now I wonder, how do I find out the USB ID to my mouse? I tried lsusb, but I can't make very much out of it because I'm not very into this stuff...  
In the file, it says
# The list of USB IDs that should not use autosuspend. Use lsusb to find out the
# IDs of your USB devices.
# Example: AUTOSUSPEND_USBID_BLACKLIST="046d:c025 0123:abcd"
AUTOSUSPEND_USBID_BLACKLIST=""



Or, alternatively, is there any other way to fix it (other than disable laptop-mode-tools altogether, that is)?


(Sorry for this really long post...)

---

