---
title: "How can I install a usb wifi lan adapter ?"
date: 2005-07-29
forum: Networking &amp; Wireless
---

### Post by ricardo06 on 2005-07-29
Hello,

I have been searching the wikis, how to's and others for hours and I can't find a post on How to connect to the internet with one of these magic small usb wifi lan adapters.
On my FC3 machine i select 'USB CDC' in the network-system-configuration panel and here it goes.
I have some side questions on top of this one :
 - Is there a graphical tool to install and configure a new (second, third etc...) network interface ?
 - If not, how can install a new network interface ?
 - Is there a way to list the network device drivers available ?

I know that's many question If I can have some pointers ans hints I would be glad.

Richard

---

### Post by spd106 on 2005-07-30
Hi, first I suggest you look at this wiki page to see if your usb card is known to be supported.
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)
Maybe also look at [http://www.qbik.ch/usb/devices/search_res.php?pattern=802.11](http://www.qbik.ch/usb/devices/search_res.php?pattern=802.11)

If you are in luck, it should be detected by the network administration tool. Then it's just a matter of configuring it (system->administration->networking).

If not, this doesn't mean it won't work. You may need to find a driver for the card.

To check it's been detected try $lsusb at the command line.

You may need to install ndiswrapper
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

I would suggest you start with the ndiswrapper-utils package included with hoary then try the source package if that doesn't work.

Hope this helps

---

