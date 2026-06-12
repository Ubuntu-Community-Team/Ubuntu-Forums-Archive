---
title: "USB to Ethernet adapter with linux?"
date: 2014-01-25
forum: Networking &amp; Wireless
---

### Post by riccardosl45 on 2014-01-25
Hello guys, I see a lot of new ultrabooks are missing the RJ45 ethernet port, there are USB to Eth adapters but I suppose some driver is needed and probably not provided for linux 

Do you have any experience with USB to Ethenet adapters under ubuntu linux?

---

### Post by spjackson on 2014-01-27
I don't have experience with USB to Ethernet adapters, but I do use USB to Wifi adapters e.g. [http://www.amazon.co.uk/Edimax-EW-7811UN-150Mbps-Wireless-Adapter/dp/B003MTTJOY/](http://www.amazon.co.uk/Edimax-EW-7811UN-150Mbps-Wireless-Adapter/dp/B003MTTJOY/)

Some USB to Ethernet adapters are advertised as working with Linux e.g. [http://www.amazon.co.uk/Plugable-Ethernet-Network-Chromebook-Specific/dp/B00484IEJS/](http://www.amazon.co.uk/Plugable-Ethernet-Network-Chromebook-Specific/dp/B00484IEJS/)

Note that USB 2 devices are limited to 100Mbps. You will need USB 3 for Gigabit ethernet.

---

### Post by oldfred on 2014-01-27
Several years ago I had a 10 year old laptop that had no Ethernet ports and one USB port. I used a $5 Airlink 101 USB2 to Ethernet adaptor. PC was supposed to use PC Cards for Ethernet but I did not have one and they were expensive.

If it is a new system, the wi-fi would probably be faster. As USB ports are slow and USB3 may not work?

I tried several distributions. Some did not work. Then I tried Ubuntu. While it worked out of the box PC only had 128MB of RAM and minimum then was 256MB. I think only because I had swap already created did it install but was so slow as not to be useable. 
Further research found some older kernels worked, some very new worked, but there was a regression and several did not work that many distributions were using.
Finally found an install back then that worked and was functional if not speedy, then then one of its update broke it and I gave up.
I have not tried with that adapter for at least two years so do not know now what may work.

How much RAM? What video? As that may help determine if a distribution will even work.

---

