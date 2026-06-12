---
title: "No wireless driver on Ubuntu 14.04"
date: 2016-11-02
forum: Networking &amp; Wireless
---

### Post by mcmaster-99 on 2016-11-02
I'm new to Linux and I've been having trouble with the wireless/wifi not showing up on my Ubuntu on a VM. I'm currently running Ubuntu on a virtual machine and the wifi on my Dell Inspiron 15 runs perfectly fine but I've been trying to get it to work on Ubuntu for the past 2 days with no luck. Searched everywhere on the web to try and find a solution to no avail.

Ubuntu Version: 14.04
Additional Drivers: no additional drivers show up in settings even with Ethernet connection.
This is the ouput when I type "sudo lshw -class network": [http://imgur.com/a/H1pT1](http://imgur.com/a/H1pT1)

Any help is greatly appreciated.

---

### Post by wildmanne39 on 2016-11-02
In a vm the internet connection runs off the host system and it shows as an ethernet connection in the vm even if the host is using wifi.

See in the vm the actual hardware of the conmputer can not be seen it runs off the host system. The exception to this is if you use a usb wifi adapter.

---

### Post by mcmaster-99 on 2016-11-02
> **Wild Man said:**
> In a vm the internet connection runs off the host system and it shows as an ethernet connection in the vm even if the host is using wifi.

See in the vm the actual hardware of the conmputer can not be seen it runs off the host system. The exception to this is if you use a usb wifi adapter.

You're literally the man. When I did my searches for the past 40 hours or so, I never included me having a VM and now when I google this issue involving a VM, I get that same exact answers as yours. THANK YOU!!

---

### Post by Bucky Ball on 2016-11-03
Welcome. Does that mean you fixed it?

---

