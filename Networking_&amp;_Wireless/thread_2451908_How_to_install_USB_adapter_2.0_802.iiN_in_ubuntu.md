---
title: "How to install USB adapter 2.0 802.iiN in ubuntu"
date: 2020-10-13
forum: Networking &amp; Wireless
---

### Post by ainahjeanbalela on 2020-10-13
Hi,
I buy usb wireless adapter but its not working on my desktop. I Have Ubuntu 16.04.

Someone help me with this. 
Thank you.

---

### Post by TheFu on 2020-10-13
[LIST=1]
[*]Return it ASAP and get your money back.
[*]Upgrade to 20.04. Newer kernels have support for newer wifi devices.
[*]Lookup which adapters are completely plug-n-play with Linux/Ubuntu and buy one of those. 
[/LIST]

Buying random hardware only leads to major hassles on Linux. Pick your hardware carefully.  Very seldom will a no-name, cheap, device, be the one you need. Sorry.

If you want to fight with it, first, it will be hard with 16.04. Those kernels don't support newer wifi USB devices and never will without huge hassles.  Can you compile C programs?  That will be needed if you don't just buy a device that is supported automatically.  Someone else trying to get wifi working: [https://www.linux.org/threads/installing-a-usb-wifi-unit-in-ubuntu-20-04.29202/](https://www.linux.org/threads/installing-a-usb-wifi-unit-in-ubuntu-20-04.29202/)
I did a web search for usb wifi ubuntu and found a number of lists.  "Works on Ubuntu" isn't the same as "is plug-n-play on Ubuntu" - we want plug-in-play hardware, so there aren't any driver hassles.

If you confirm you want to fight this battle for the next year+ with the current device, then run **lsusb** and determine the USB device ID, xxxx:xxxx. Use that to search for steps to make it work. If nothing is found, there isn't much that a normal user can do.

Regardless, 16.04 support ends in about 6 months. It has been a good ride, but it is time to move to a newer release. I have a number of 16.04 systems here and we are planning their migration work for the next few months.  
[LIST]
[*]16.04 support ends April 2021.
[*]18.04 support ends in 2023.  
[*]20.04 support ends in 2025.
[/LIST]

---

### Post by ainahjeanbalela on 2020-10-15
ok thank you and have a good day

---

