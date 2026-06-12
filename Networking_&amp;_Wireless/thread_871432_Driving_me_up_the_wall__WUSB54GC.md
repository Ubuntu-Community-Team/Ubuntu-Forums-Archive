---
title: "Driving me up the wall  WUSB54GC"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by Syndicated on 2008-07-26
Hi,

I have the Linksys  WUSB54GC, and for some odd reason it was working fine with Hardy Heron 8.04 until I updated today. I have done numerous searches and have found that Ndiswrapper and RTX or Rail is supposed to work. I am still new to Ubuntu and find that you need to compile the drivers? I was hoping someone out there has a good tutorial or step by step walkthrough on how to overcome this problem. Any help is appreciated.


-Syndicated

---

### Post by hajk on 2008-07-27
This device should be supported by the rt73usb kernel module, at least it is with the version of the WUSB54GC that I have:```

$ sudo lsusb -v |grep Linksys
Bus 001 Device 008: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]
  idVendor           0x13b1 Linksys
  iManufacturer           1 Cisco-Linksys
```Check with```

$ lsmod |grep rt73
```whether the module is loaded, if not load it with```

$ sudo modprobe rt73usb
```and also add it to /etc/modules.
 
One more thought: this module is still considered to be in beta testing, so you could consider upgrading the Hardy 2.6.24 kernel to 2.6.25 from backports (when and if available). Possible benefits: improved speed.

---

### Post by deianaera on 2008-08-08
> and also add it to /etc/modules.

Um...hajk, how do I do this?  I think I understand everything else you listed above, but this part.

---

### Post by hajk on 2008-08-09
You may not need to list rt73usb in /etc/modules, on my own system this module gets loaded automatically whenever I use the wireless adapter.

But, just in case, you have to edit the /etc/modules file. You can do this in a terminal by giving the command```

sudo nano /etc/modules
```
(or use any other command line editor that you fancy); you have to do this with administrative privileges. Then just add the driver name "rt73usb" on a line by itself, save and you're done.

---

