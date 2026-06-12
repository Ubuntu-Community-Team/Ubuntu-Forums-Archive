---
title: "Ubuntu 14.04 Dell Inspiron 1525 &quot;connects&quot; to Wifi but not internet"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by a.f.malouin on 2014-04-21
Hello there,

I'm new to Linux and Ubuntu and tried installing it on my Dell Inspiron 1525 laptop.

It detects the wireless networks and can connect to these networks but won't access the internet.

I tried rebooting the machine, my modem and my router but to no avail.

I tried connecting via an ethernet cable and only then could I access the internet.

I tried various "solutions" I found around the internet but this particular problem seems very case by case.

I can provide you with any information you may need.

Thank you for taking the time to read this post and have a good day. Any help is appreciated.

---

### Post by shaansweb on 2014-04-21
Same issue here with Dell Inspiron 7437

---

### Post by chainick95 on 2014-04-24
Same issue with DELL Inspiron M5010

---

### Post by Cutesquirrel on 2014-05-05
Hi,
did you find any workaround for this problem ?
I have a Dell Latitude E6520 with the same problem.
Many thanks

---

### Post by Cutesquirrel on 2014-05-05
ok, after uninstalling proprietary driver, all is ok !

---

### Post by chili555 on 2014-05-05
> **Cutesquirrel said:**
> ok, after uninstalling proprietary driver, all is ok !Indeed. In many of these Dells, a Broadcom driver is installed. The Additional Drivers tool often installs the *wrong* driver. I urge each of you to see if you have a Broadcom:```
lspci -nn | grep 0280
```If so, please see the sticky at the top about installing the correct driver.

---

### Post by nathanielbradfordkelley on 2014-05-16
hey, I am having the same issue how do you remove that driver specifically?

---

### Post by chili555 on 2014-05-16
> **nathanielbradfordkelley said:**
> hey, I am having the same issue how do you remove that driver specifically?Before we apply the wrong fix to the wrong device, please identify it as I requested above:```
lspci -nn | grep 0280
```

---

### Post by nathanielbradfordkelley on 2014-05-16
It output :
> 02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)



---

### Post by chili555 on 2014-05-17
> Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727]In fact, yours is *not* the same device as above. It is the trickiest, most difficult device we have here!

As an aside to the searchers, not all wireless devices are the same; not all Broadcoms are the same. The pci.id is everything. If yours is a Broadcom, next consult the sticky: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

nathanielbradfordkelley, let's remove the wrong driver:```
sudo apt-get purge bcmwl-kernel-source
```And let's blacklist a possibly competing driver:```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```In some cases, blacklisting ssb will disable your Broadcom ethernet card. Post back for help if that is your case..

---

### Post by joshua28 on 2014-05-17
I am having a similar issue. For me whenever i enable the use of the broadcom driver under 'Additional Drivers', Ubuntu will automatically unselect this after applying changes. I did not have any issue with wireless in 13.10. My pci.id of the broadcom driver is 14e4:4315 and on the sticky it says TBA in 14.04. Can I use the 13.10 method to install the drivers?

---

### Post by chili555 on 2014-05-18
> **joshua28 said:**
> I am having a similar issue. For me whenever i enable the use of the broadcom driver under 'Additional Drivers', Ubuntu will automatically unselect this after applying changes. I did not have any issue with wireless in 13.10. My pci.id of the broadcom driver is 14e4:4315 and on the sticky it says TBA in 14.04. Can I use the 13.10 method to install the drivers?Yes, please. Be sure to purge the proprietary driver first, as outlined in the sticky.

---

