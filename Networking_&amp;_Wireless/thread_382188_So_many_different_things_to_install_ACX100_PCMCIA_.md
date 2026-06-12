---
title: "So many different things to install ACX100 PCMCIA card- help me sort this all out!"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by jerseyboy91 on 2007-03-11
I found the section in the ndiswrapper list to install the D-Link Airplus DWL 650+ plug-in card for laptops. It shows a whole bunch of links to install the thing, but I don't know which one to go to. I've tried all day installing it, but with no avail. I saw the open-source driver, and there's a link to tutorials to install it, but I'm confused as to whether or not it applies to the open-source driver.

So if anyone else has already done this before, can you help me out? I'm very confused with doing this, and I want to restore my old laptop's functionality after it crapped out with Windows 2000 (it now has Xubuntu).

---

### Post by chili555 on 2007-03-11
I have never done this before, but my dentist tells me I have a very high pain threshold.

Are you quite sure you need ndiswrapper? Unless you have blacklisted acx100, please show me the output of the following, in order. Sudo modprobe acx, then dmesg | grep acx and finally ifconfig.

---

