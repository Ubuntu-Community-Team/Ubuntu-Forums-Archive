---
title: "Relatively awful connection speeds"
date: 2020-03-23
forum: Networking &amp; Wireless
---

### Post by vincentur802 on 2020-03-23
Hi,

I'm running dual boot (Ubuntu 19.10 and Windows 10) on a Lenovo 81SQ. The wireless adapter is a Realtek RTL8822BE 802.11a/b/g/n/ac chip.
I'm getting relatively slow connection speeds specifically on Ubuntu. Through speedtest.net, I'm getting ~30Mbps down compared to ~250Mbps down on the same device, but on Windows.

So far, I've tried every suggested fix in this article with no success: [https://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](https://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/)
I've also used the nethogs tool to verify there isn't any malware eating up the bandwidth.

Just wondering if there's a configuration I need to change or if this is a known driver issue.

Thanks

---

### Post by ajgreeny on 2020-03-23
Is secure boot disabled in the UEFI settings?  I believe it needs to be for the kernel modules for that card to be installed in Ubuntu, but I have not used Windows since XP so I'm very out of date when it comes to dual booting.

---

### Post by vincentur802 on 2020-03-23
I updated the drivers after disabling secure boot, unfortunately I'm still bottlenecked. Thanks for the suggestion, however.

---

### Post by ajgreeny on 2020-03-24
Have a look at the thread at [https://askubuntu.com/questions/883673/realtek-rtl8723be-wi-fi-incredibly-weak](https://askubuntu.com/questions/883673/realtek-rtl8723be-wi-fi-incredibly-weak) which is  for a different realtek card but perhaps is appropriate for your card and laptop.

You may, of course, need to edit the card number to fit your machine, ie, rtl8822be indtead of rtl8723be shown in those answers.

Backup the file first in case anything goes wrong so that you can reverse your actions.

---

### Post by vincentur802 on 2020-03-25
I checked it out and scoured the web for more possible fixes without any luck. I should have mentioned this bottleneck is only present on my 5 GHz band. The speeds are very similar, running both at around ~40 Mbps.

---

### Post by ajgreeny on 2020-03-25
See Wireless-Info in my signature below and follow the instructions there to show information about your hardware and software. 
The output  from the script  may help our wife experts.

---

