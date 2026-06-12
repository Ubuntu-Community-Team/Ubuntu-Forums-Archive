---
title: "Unable to connect to Wi-Fi on Xubuntu 12.04 on a HP Pavilion 15 n268sa"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by josh45 on 2014-04-19
I am unable to connect to wireless internet on my new computer. There is no "enable wifi" option under "enable networking" on the Network Manager. Wired internet works fine.

I am using Xubuntu 12.04 because my computer is currently having an issue with any other version of Linux: [U][see this thread]("http://ubuntuforums.org/showthread.php?t=2218095")

[/U]I am currently reinstalling Xubuntu 12.04 as after upgrading it to 13, it no longer loads. Unfortunately I can't get information about my computer until I have reinstalled it, but I will post more information as soon as I can.

I have a HP Pavilion 15 n268sa. It has a Realtek RTL8188ee. 
When I do: sudo lshw -C network
It said "UNCLAIMED" next to the bit of hardware for wireless.
I managed to install the RTL8188ee driver for the hardware so it no longer said "UNCLAIMED" (but it didn't say CLAIMED either). 
Even when it said "driver: rtl8188ee" the wi-fi still did not work. There is no option for me to check enable wifi.

I was able to connect to wireless internet on the installation wizard for the other versions of Linux I tried to install and I was equally able to do so on Windows 8.1
I had the same problem in Linux Mint 10, but I did not try to fix it on Mint. 

I have Xubuntu on my older computer and I am sure it was just able to detect wi-fi straight away. 

I would really appreciate any help with this. I have been struggling all day. Thank you very much.


Edit: if I manage to sort out my problem installing more recent version of Xubuntu, then I think I will avoid this problem as I was able to connect to wireless when installing them so hopefully will be able to do so if they correctly install.

---

### Post by praseodym on 2014-04-19
Hi,

which kernel is in use? Please show
```

uname -a
```

---

### Post by josh45 on 2014-04-19
With help on my other thread, I managed to fix the problem I had installing more recent versions of Xubuntu. The version I have now works fine with wireless. Thank you nonetheless. I will update the thread as "solved".

---

