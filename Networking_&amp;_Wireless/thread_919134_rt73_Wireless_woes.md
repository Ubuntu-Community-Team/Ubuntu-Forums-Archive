---
title: "rt73 Wireless woes"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by SpongeBob SquarePants on 2008-09-13
Evening all.

Generally my inbuilt cheapo wireless card works out of the box with Ubuntu. At least it did. Until I installed Hardy. It's a bit shabby now. Slow connection speed, often grinding to a half, before spluttering into life again. A bit crap really.

Anyway, I thought I'd give ndiswrapper a chance. So I installed ndiswrapper from the repos, before installing my rt73.INF driver using ndisgtk. Everything seemed to be okay. Running "ndiswrapper -l" shows that the driver to be installed. Running "lshw -C Network" shows everything as it should be.

Changed the driver in Wicd from wext to ndiswrapper and rebooted. No connection. Uninstalled ndiswrapper and built a newer version from source. Re installed driver. Rebooted. Same. Won't connect at all.

Any idea on what to try next?

Few things to mention. Both lspci and lsusb show up nothing. I had to identify my card through dmesg, where it shows up as rt73usb. The rt73.INF file has worked for me in the past using ndiswrapper (in Mepis), so I assume it's good.

Thanks.

---

### Post by SpongeBob SquarePants on 2008-09-15
bump

---

### Post by Ayuthia on 2008-09-16
If rt73usb is showing up instead of ndiswrapper, you might try to blacklist the module.  Before doing that though, you could try to see if this method would fix it:
```
sudo modprobe -r rt73usb ndiswrapper
sudo modprobe ndiswrapper
```Then check if your wireless works.  If it does, then you can try the following:
```
echo blacklist rt73usb | sudo tee -a /etc/modprobe.d/blacklist
```

By the way, can you post your lspci and lshw -C network?  If lshw -C network shows your card, lspci should show it also.

---

