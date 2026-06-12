---
title: "Pci Card Not Turning On"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by talltraveler on 2007-02-26
Hi
   Others seen to be having this problem too, I am using ubuntu ultimate 1.1 and when I plug in the netgear card it shows up in the device manager but it won.t turn on. Is there some setting I have overlooked or should I get a more user friendly  pci card? Can you help?

---

### Post by chili555 on 2007-02-26
Yes, we can help, but you have given us precious little to go on: Netgear.  Let's start by opening up System -> Administration -> Networking and see if your wireless interface is listed. It might be eth1 or wlan0 or wifi0. Yes? Click properties, enable and select DHCP. Does it sit for a few seconds and close? Great, you are probably all set. Does it throw up an error message? Post back and we'll help.

No wireless interface shown? Open a terminal and enter a command sudo lspci -vv | grep Network. That should give you information about the chipset your wireless card uses. You can search this forum for posts dealing with your chipset and see posts that will describe how to get your card going.

Post back if you get stuck.

More information is better than less. If you need more help, we'll want to see the terminal output of sudo lspci -vv | grep Network, sudo iwconfig and sudo ifconfig -a.

---

### Post by talltraveler on 2007-02-26
Thank you but it didn't even show up in the network settings. Think I will purchase another card, one that works instantly with ultimate 1.1. I don't want to go back to windows!! Perhaps you know of a brand and model number.

---

### Post by talltraveler on 2007-02-26
Hello
 How do you get that vertical line between lspi-vv and grepNetwork, and what does it mean? Also when I tried to install the windows drivers using ndiswrapper it says can't install line 188 and I can't delete any of the drivers that were installed. That is why I am here. Completely stuck!

---

### Post by chili555 on 2007-02-26
lspci -vv | grep Network means, roughly, list all my devices and be verbose and *more* verbose and pipe (that little vertical line) the output through a command called "grep" which means, roughly, look for a pattern: Network.

The vertical line is on your keyboard above the frontslash \. On my laptop, it's to the right of ]. On my desktop it's to the right of =. Very handy!

Can you walk us through the steps you took to get to "can't install line 188"? You can list out your last commands in order with the command history.  Then put the commands relevant to ndiswrapper here. history | grep ndiswrapper.

We are here for you, tall.

---

### Post by talltraveler on 2007-02-27
Thankyou for your help, tho it all seems to be a bit foreign to me at this stage. I bought a DLINK DWL-G630 pci card, when I get home I will try to install it. Any special things I should do before I take the plunge? Thanks again... Will look for a reply soon....:)

---

### Post by chili555 on 2007-02-27
There are several versions of this card and some work out of the box and some need ndiswrapper. You will only know what chipset you have when you do sudo lspci -vv | grep Network. Sound familiar?

 Check here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

---

