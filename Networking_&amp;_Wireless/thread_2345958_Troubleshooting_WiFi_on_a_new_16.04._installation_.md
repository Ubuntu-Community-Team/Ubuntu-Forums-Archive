---
title: "Troubleshooting WiFi on a new 16.04. installation on a Lenovo Thinkpad X140e"
date: 2016-12-09
forum: Networking &amp; Wireless
---

### Post by mlnease on 2016-12-09
Hello,

I've just done a fresh install of xubuntu 16.04.1 on my wife's new (refurbished) Lenovo Thinkpad X140e.  Everything went swimmingly except that I can't seem to connect to our wireless router.

I installed it alongside Windows 8 (my wife's preference) and that OS connects to the router with no problems.

I've done many, many Ubuntu/xubuntu installations on both laptops and workstations but find myself stymied.

The indicator applet in my xfce4 panel shows the ethernet connection as usual (which works as well as Centurylink ever does), but none of the usual list of local wifi connections appears.  I've installed WiFi Radar; no luck; ditto with System/Network Tools, Settings/Network and Settings/Network Connections.

I feel I'm missing something obvious but am drawing a blank--any suggestions, anyone?

Thanks in advance.

mn

---

### Post by jeremy31 on 2016-12-09
Please see the wireless script link in my signature and post your results

---

### Post by mlnease on 2016-12-09
> **jeremy31 said:**
> Please see the wireless script link in my signature and post your resultsThanks very much for the quick response.  The output is at [http://paste.ubuntu.com/23605723/](http://paste.ubuntu.com/23605723/) ; should I paste the text here as well?

I've been studying the text and gather that my problem is a missing driver for an old Broadcom wireless device and that I need to download and install that driver from the site you linked to.  Is that correct?  

Thanks again and in advance.

mn

edit:  Unfortunately, the PCI device output from 
lspci -vnn -d 14e4:

(14e4:0607) doesn't appear in the list of devices at that site.  Is this helpful?

Thanks again for your time and attention.

---

### Post by wildmanne39 on 2016-12-09
Please do the following with an internet connection:
```
sudo apt-get install bcmwl-kernel-source
```
Reboot

---

### Post by mlnease on 2016-12-09
> **wildmanne39 said:**
> Please do the following with an internet connection:
```
sudo apt-get install bcmwl-kernel-source
```
RebootBrilliant--bravo--solved!  THANK YOU!

---

### Post by wildmanne39 on 2016-12-09
Your welcome!
Enjoy!

---

