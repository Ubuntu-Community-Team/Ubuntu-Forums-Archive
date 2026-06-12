---
title: "Wireless Hardware Switch Disables USB Wireless Devices"
date: 2014-08-04
forum: Networking &amp; Wireless
---

### Post by Blasman on 2014-08-04
I recently upgraded from Xubuntu 13.10 to 14.04.1 and have encountered a problem that does not exist for me in Xubuntu 13.10 or Windows 7.

Using xubuntu 14.04.1 on my MSI Wind U100 netbook, disabling the internal wifi via the hardware (FN key) also disables my wifi USB dongle.  Therefor, I am forced to keep the internal wifi enabled in order to use the USB device.  This wastes battery life as the internal wifi is unused (I don't use it because it has *extremely *poor range).

How can I keep the internal wifi disabled with the hardware switch and still be able to use the wireless USB device?  Thanks.

---

### Post by praseodym on 2014-08-04
You can blacklist the kernel module of the internal card. Lets check:
```

lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by Blasman on 2014-08-04
> **praseodym said:**
> You can blacklist the kernel module of the internal card. Lets check:
```

lspci -nnk | grep -iA2 net
lsmod
```

Thanks for the quick reply.  Would disabling the kernel module have the same effect as disabling the hardware switch for that device?  In other words, will the internal wireless still be using 0% of the battery life?  Blacklisting it seems like more of a "work around" than an actual solution.  Is there any way to just have it function like it does in Windows and Xubuntu 13.10?  If blacklisting is the only solution, I have done the following commands as per suggested.  I am not sure what exactly I should be blacklisting, and *there are some  times where I still want to use the internal wireless* (when I'm closer  to my router). 

I can't seem to copy and paste the info here with proper formatting, so I put the results on [pastebin here]("http://pastebin.com/raw.php?i=FiiddDDA").

---

