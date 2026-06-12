---
title: "Broadcom BCM4306 WiFi card installation help"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by splttingatms on 2007-04-04
I own a **HP ze5470us Laptop** that came with a built-in **Broadcom BCM4306 802.11b/g Wireless Lan** hardware. I installed Ubuntu 6.10 but the wireless wifi did not work. I have looked into the problem and some people had NdisWrapper working but I cannot find an easy howto guide on how to go about and installing everything. 

I looked into the help on NdisWrapper site but got even more confused when it started talking about pci numbers and I could not find in the list.

Can someone make an easy to follow guide showing me how to get the wifi working? I have another computer that has internet so I can download files. Appreciate the help.
~Sunny

---

### Post by Floppyjoe on 2007-04-04
> **splttingatms said:**
> I own a **HP ze5470us Laptop** that came with a built-in **Broadcom BCM4306 802.11b/g Wireless Lan** hardware. I installed Ubuntu 6.10 but the wireless wifi did not work. I have looked into the problem and some people had NdisWrapper working but I cannot find an easy howto guide on how to go about and installing everything. 

I looked into the help on NdisWrapper site but got even more confused when it started talking about pci numbers and I could not find in the list.

Can someone make an easy to follow guide showing me how to get the wifi working? I have another computer that has internet so I can download files. Appreciate the help.
~Sunny

Goto the HP site and download the Broadcom drivers for you computer model. Then use your Ubuntu install disk as a repository to install ndiswrapper-utils-1.8 and ndiswrapper-common. Extract the bcmwl5.inf and bcmwl5.sys files to your home folder and then install them with the ndiswrapper -i bcmwl5.inf command. Do a sudo depmod -a command. Then sudo modprobe ndiswrapper. Then sudo ndiswrapper -m. Then open /etc/modules and add the word ndiswrapper, close and save file.

Don't forget to blacklist bcm43xx.

---

