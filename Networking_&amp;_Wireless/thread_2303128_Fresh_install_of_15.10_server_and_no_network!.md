---
title: "Fresh install of 15.10 server and no network!"
date: 2015-11-16
forum: Networking &amp; Wireless
---

### Post by faroutliving on 2015-11-16
I installed this originally with no network available. When it couldn't detect the network I just choose "skip it", or whatever the dialog choice was. But now that I have the network back it won't recognize any network interfaces! The file /etc/udev/rules.d/70-persistent-net.rules is empty! I've tried forcing the generation of the file using 
/lib/udev/write_net_rules all_interfaces

and

udevadm trigger --action=add

and

udevadm trigger --action=changed

and nothing seems to work. Still no /etc/udev/rules.d/70-persistent-net.rules

I am presuming that some basic step got skipped, what I am hoping is I can finish that step by hand/trigger it without having to reinstall.

Thanks for any clues,

Deron

---

### Post by TheFu on 2015-11-16
**sudo lshw -C network**
please.

---

