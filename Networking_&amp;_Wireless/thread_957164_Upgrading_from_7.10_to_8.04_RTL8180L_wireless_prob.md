---
title: "Upgrading from 7.10 to 8.04 RTL8180L wireless problem"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by barrel_master on 2008-10-24
Hello, my wireless was working fine in 7.10 but stopped working in 8.04.  

I'm using a Realtek RTL8180L wireless adapter.  As far as I know the driver is natively supported I think... 

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

However the result of lshw gives me a:

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
network UNCLAIMED 
...
configuration: latency=0 maxlatency=64 mingnt=32
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

Which suggests that my drivers aren't installed properly.  

I tried to:

sudo modprobe r8187

as per: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

But still had problems/didn't seem to get me anywhere.  Are there any other resources out there/obvious little fixes that I'm overlooking?

---

### Post by barrel_master on 2008-10-24
A shameless bump on my part.  Please keep in mind that I don't have direct internet access on my laptop as my room mate refuses to let me connect to the router with a wired connection for privacy reasons.

---

### Post by barrel_master on 2008-10-24
Bump

---

