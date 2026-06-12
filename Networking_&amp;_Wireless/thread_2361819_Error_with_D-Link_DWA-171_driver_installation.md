---
title: "Error with D-Link DWA-171 driver installation"
date: 2017-05-21
forum: Networking &amp; Wireless
---

### Post by hous0034 on 2017-05-21
I've newly installed Ubuntu 16.04 LTS on a desktop. Wi-fi didn't turn on, wi-fi is through a usb D-Link DWA 171.

From reading these forums I surmised it was driver problems. I followed the instructions provided in [this post about the same issue]("https://ubuntuforums.org/showthread.php?t=2168426")

Since I couldn't connect to the internet I downloaded the git onto a usb then copied it to the desktop, navigated to the directory and ran the rest of the steps from there. 

When I try to make the file I get a bunch of errors. They all seem to stem from the error below. I'm brand new to linux, any help in resolving this error would be greatly appreciated.

error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]   rtw_proc=create_proc_entry(rtw_proc_name, S_IFDIR, init_net.proc_net);

---

### Post by Hadaka on 2017-05-21
Hi, the link you provided is "dated" , let's try something more recent.
From a working wired connection , open a terminal...ctrl/alt/t then do..
```
sudo apt-get update
sudo apt-get purge rtl8812au-dkms
```
*If you get an error, or not installed or found,
it is ok..just continue with the link.

Then go here..and start with Wildmanne39's post #6
[https://ubuntuforums.org/showthread.php?t=2348220](https://ubuntuforums.org/showthread.php?t=2348220)
Thanks.

---

