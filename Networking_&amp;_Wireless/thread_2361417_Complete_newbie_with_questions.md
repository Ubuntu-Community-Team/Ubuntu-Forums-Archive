---
title: "Complete newbie with questions"
date: 2017-05-16
forum: Networking &amp; Wireless
---

### Post by kevin.richards on 2017-05-16
Hi, I am new on this forum, and completely new to Linux and Ubuntu experience. I have an old Dell Inspiron 1515 laptop with (T6500 processor/ 3GB DDR2/ GMA4500) and the latest Ubuntu 17.04 OS runs fine on the USB but it does not picks up the Wi-Fi driver. I searched the Internet and I came up with Shell commands to install it, of which I have little knowledge. My question is how do I install Wi-Fi through shell command? Secondly, I tried installing Ubuntu on HDD but despite configuring the details I couldn't get it to install it on my HDD. Though, it works through USB. Thirdly, what is Ubuntu Kylin?

---

### Post by howefield on 2017-05-16
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by wildmanne39 on 2017-05-16
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

