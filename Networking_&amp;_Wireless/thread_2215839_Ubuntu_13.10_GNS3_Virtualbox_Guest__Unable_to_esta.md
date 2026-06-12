---
title: "Ubuntu 13.10 GNS3 Virtualbox Guest | Unable to establish console"
date: 2014-04-08
forum: Networking &amp; Wireless
---

### Post by sam49 on 2014-04-08
Hello everyone,

I have a bit of a complicated issue to which I haven't found any solution, yet.

My system runs Ubuntu 13.10 and has the latest GNS3 as well as the virtual box installed ("sudo apt-get install" today). GNS3 runs just fine and I can also establish a console connection to any Cisco router for which I configured an IOS image as usual.

The problem is that I cannot get to the console of any imported VMWare guest. I can start the guest, access it via VMWare window but not via GNS3 console option.

The configuration is shown in the attachment and I would be glad if someone could give me some pointers (I tried minicom and it does not show any serial port). In the process of "fixing" it I have also somehow moved the interface configuration file as there is nothing anymore under /sys/network/interfaces but under var/tmp.

Thanks

---

