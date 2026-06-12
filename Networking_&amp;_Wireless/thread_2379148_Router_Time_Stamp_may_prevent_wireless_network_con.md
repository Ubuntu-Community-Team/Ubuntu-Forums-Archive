---
title: "Router Time Stamp may prevent wireless network connection"
date: 2017-12-01
forum: Networking &amp; Wireless
---

### Post by krawlb4uwok on 2017-12-01
Relative newbie...

I installed Xubuntu 16.04.02, with inline updates, on a Dell Latitude 110L notebook, which has a Broadcom BCM4318 R. 02 wireless card.  Wireless was not active from the base install.  I did "sudo apt install firmware-b43-installer" to install the Broadcom driver.  The 110L then recognized the wireless access point.  I also did "sudo apt-get purge bcmwl-kernel-source" for good measure, although nothing was found to purge.  My wireless router is a D-Link DIR-655 Hardware version A4, with WPA2 enabled.  Attempts to connect resulted in a churning "wait" icon, and then after about 20-30 seconds, a disconnect.  The logs on the router showed the 110L would connect and then deauthenticate (router's term).  Various updates to the Xubuntu install had no affect.  

After extended head scratching, and a night's sleep, and more head scratching, I eventually found the problem.  The time on the router was a little off, by about 13 years.  I set the time to current, plus or minus a minute, and the 110L immediately connected and has remained connected for about an hour now.  Thought I would share this, and maybe save someone re-experiencing this particular headache.

---

