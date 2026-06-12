---
title: "How do I setup a static IP address?"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by Vormeph on 2013-10-06
I have disabled DHCP on my router's configuration page so I can use a static IP Address. How do I go about this? I tried using the Network GUI on Ubuntu 13.04 but when I choose 'Manual' and then input the following info, I then lose internet connection; but somehow I'm still connected to my router. Can anyone help me out? How do I PROPERLY setup a static IP address?

---

### Post by Iowan on 2013-10-06
You can use **ifconfig** (from a terminal) to verify that you got an IP address.  IF you have an address in the router's subnet, it may be a routing issue.
Without the DHCP server to configure it, you will need to set up the DNS server address.

Maybe you already attended to these details...

---

### Post by chili555 on 2013-10-06
>  I tried using the Network GUI on Ubuntu 13.04 but when I choose 'Manual' and then input the following info, I then lose internet connection; but somehow I'm still connected to my router. That sounds an awful lot like you neglected to set up DNS nameservers. Did you? Please see attached.

You can probably use the address of the router and also good old Google's nameservers: 8.8.8.8 and 8.8.4.4.

---

