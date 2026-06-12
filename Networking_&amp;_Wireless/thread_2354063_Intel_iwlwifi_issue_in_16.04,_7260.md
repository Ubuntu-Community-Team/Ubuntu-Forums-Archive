---
title: "Intel iwlwifi issue in 16.04, 7260"
date: 2017-02-27
forum: Networking &amp; Wireless
---

### Post by ryan-jentzsch on 2017-02-27
This bug is driving me crazy. I was [working with the Intel devs]("https://bugzilla.kernel.org/show_bug.cgi?id=191601") and thought I found that an older kernel version fixes this problem. **I was wrong**. The Intel devs went silent as soon as they thought it was a kernel issue. Anyone have any idea how to solve this? Random disconnects is not productive. I've tried multiple kernels and the 7260 still craps out. I tried the backports and building to the kernel to no avail.

---

### Post by jeremy31 on 2017-02-27
Moved to it's own thread.  See the wireless script link in my signature and post results

---

### Post by Keith_Helms on 2017-03-01
What are the symptoms you're seeing?  My laptop has an Intel 7260 in it and I have problems when I'm connected to the hotspot on my Android tablet, but not when connected to my router at home.  Data will frequently stop moving over the connection.  Sometimes it revives after a few minutes.  I can click on the network again to reestablish the connection and it works again for a while. 

This all worked fine on 14.04 and only cropped up when I installed 16.04.  I may (fingers crossed) have stumbled across a solution.  I went out to the Intel firmware site 
[http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html](http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html)
and the latest file for the 7260 was for Linux kernel 4.2 (16.04 is on 4.4).  I downloaded that file
**iwlwifi-7260-ucode-25.30.14.0.tgz**
extracted the iwlwifi-7260-14.ucode and copied that to the /lib/firmware directory.  That directory already had versions 16 and 17 in it, so I moved them to my home directory for safekeeping. When I rebooted, it looked for the -17,-16, and -15 versions and then settled for the -14 version.  So far, there have been no wifi hung problems using that firmware version.

---

### Post by Keith_Helms on 2017-03-01
Oh well.   The session lasted longer but eventually hung.  It looks like it was in the process of trying to renew a dhcp lease when it quit working.

---

