---
title: "Ubuntu 16.04.2 LTS rtl8192cu stopped working"
date: 2017-06-20
forum: Networking &amp; Wireless
---

### Post by eep40d on 2017-06-20
Hi,

I have managed to get the wifi working on my desktop computer at university, however, it suddenly stopped working. The wifi cone GUI on the top of the screen is now empty.  I tried to restart the computer, but that didn't work at all.

I had it working for about 11 days. I had to install the updated driver, as shown in the following link: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

I even had to carry out the power management step, as it refused to work without doing this.  I have attached the link to the output from wireless-info.txt: [http://pastebin.ubuntu.com/24908839/](http://pastebin.ubuntu.com/24908839/)

So, what could be the problem here?

Thanks.

PS. I am using a Windows computer in order to write this, as there is no wired connection available in the lab.

---

### Post by eep40d on 2017-06-21
I have managed to resolve the issue.  I deleted the Wifi connection from the list of recognised connections, then I reinstalled the settings.

---

