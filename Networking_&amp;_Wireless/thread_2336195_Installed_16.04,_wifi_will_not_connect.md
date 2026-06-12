---
title: "Installed 16.04, wifi will not connect"
date: 2016-09-05
forum: Networking &amp; Wireless
---

### Post by patd68 on 2016-09-05
Hi,

I recently bought a new laptop (HP Pavilion x360 m3 convertible) and installed Ubuntu 16.04.  My wifi works fine when I use Windows, but will not connect when I use Linux.  I used Ethernet to install updates, but wifi still does not work.  

Any help would be appreciated.
I'm new to Linux too.

Thanks.

---

### Post by autocrat on 2016-09-05
Can you give us some more details?
- Can you see wifi networks but it wont connect?
- Can you not see any wifi interface at all?
- What do you see when you open up the network manager? 

Have you tried downloading and installing drivers for your wireless adapter?

---

### Post by wildmanne39 on 2016-09-05
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by patd68 on 2016-09-11
Hi,

Sorry for the delay!

When I have wi-fi enabled, I cannot see any wi-fi networks, it simply says "device not ready".

When I go to the network tab in settings and attempt to turn wi-fi on, it will immediately switch to off again.  

I ran the script requested and have attached the the .tar.gz file below (or at least I think I did).  
I ran the script while using ethernet, so hopefully that doesn't effect the results.  

Thank you!

[ATTACH]271085[/ATTACH]

---

### Post by jeremy31 on 2016-09-11
Another HP computer with an acer_wmi module loaded ```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by patd68 on 2016-09-11
The result of that command was:

```
blacklist acer-wmi
```

The wifi did not start working after that.  Should I have done something else after that?

Thanks.

---

### Post by wildmanne39 on 2016-09-11
Did you reboot?

---

### Post by patd68 on 2016-09-11
I hadn't rebooted it.  My wifi started working after I did reboot.  Thank you so much!

Also, if anybody would like to explain what the command I ran did, I'd be very interested to know.  

Thanks

---

### Post by wildmanne39 on 2016-09-11
It stops the acer-wmi from loading which usually tells the kernel to turn the wifi on but in a lot of cases it does not and has to be stopped from loading so your wifi can work.

---

