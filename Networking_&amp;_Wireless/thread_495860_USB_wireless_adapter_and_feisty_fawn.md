---
title: "USB wireless adapter and feisty fawn"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by justind on 2007-07-08
I am trying to get me ashton digital usb adapter to work in feisty. When I go into the network it seems to think that my wlan0 in a wired connection. And when I type in iwconfig it says no wireless extensions by it. I am using the computer with the eth0 wired adapter and it works fine.

---

### Post by justind on 2007-07-08
Ok, I think I have ndiswrapper installed along with ndisgtk. When I type ndiswrapper -v in the terminal this is what it shows:
```
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 
```

---

### Post by fredj on 2007-07-09
You have the defective version of ndiswrapper that may work with some older drivers but won't work 
with others. The only way to be sure that ndiswrapper will work is to download the latest source files
and compile them.
In the meantime open a terminal type 'sudo lshw -class network' (without the quote marks) and post
the output from that here.

---

