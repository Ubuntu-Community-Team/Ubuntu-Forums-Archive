---
title: "smb packet too large"
date: 2005-11-17
forum: Networking &amp; Wireless
---

### Post by bryanl on 2005-11-17
When I try to mount a share that resides on an OS/2 machine it goes OK until I try to get something from the share. Then it times out. dmesg indicates a 'packet size too large 4257 > 4096'

This appears to be something new with the 2.6 kernels and the smbfs as smbmount in RH9 with a 2.4 kernel works just fine. I have seen a similar error in other distributions with the 2.6 kernel as well. I have found several inqiries here and there that tell me others have had the same problem. But I haven't seen any workaround, fix, or solution other than to go back to an older kernel.

One of these days I'll retire the OS/2 machine when I figure out how to get a multi line fax system on a Linux machine going. In the meantime, I need to access data on its shares. It is wide open with no domain controllers or other such stuff. Any ideas about what is causing this problem?

---

