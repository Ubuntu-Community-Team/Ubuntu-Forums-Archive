---
title: "Help Belkin rt2500usb gusty"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by darkreaction on 2007-11-29
I need some help I just got gusty working. I have a belkin 54g usb rt2500. I have ndiswrapper installed and i have the windows .inf and .sys files. I have no idea of what to to do from this point on could someone help?

---

### Post by dannyboy79 on 2007-11-29
if the windows driver is rt73.inf than you don't need ndiswrapper. there's a native linux driver from serialmonkey developers. check this out: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

I am using gutsy xubuntu and I have my belkin working due to the guide that I linked you to. good luck

you can find out what chipset your belkin is by opening it up, stick a knife in the crack and slowly twist the knife until the 2 plastic pieces seperate than you can see what wifi chip is in the wifi adapter. if you don't want to do that, you can issue this command within a terminal (gnome-terminal) 

lsusb -v | grep Belkin

that's if it's a usb adapter if it a pci card, then issue this: 

lspci -v | grep Belkin

---

### Post by darkreaction on 2007-11-29
Its rt2500 chipset

---

### Post by dannyboy79 on 2007-11-29
well in the forum, i believe that there are plenty of people how use the serialmonkey rt2500 drivers. still check out that link I gave you.

---

