---
title: "Why Does Ubuntu Take The Internet Connection"
date: 2013-11-24
forum: Networking &amp; Wireless
---

### Post by mathiashu on 2013-11-24
Hi.
Why does Ubuntu eat up all the internet bandwidth? Every time I turn on the computer, every other computer in the house loses the connection to the internet (So slow you can't use it). The weird thing is, I don't have this problem at all on Lubuntu, or UbuntuGnome, or any Ubuntu based distro. Why is this? I use the Broadcom STA Wireless Driver on a Lenovo G575. Is there anything I can turn off or something? Any help is appreciated.

---

### Post by chili555 on 2013-11-25
Please find out about your wireless device from the terminal:```
lspci -nn | grep 0280
```Is it 14e4:4727? If so, please see post #12 here: [http://ubuntuforums.org/showthread.php?t=2189774&page=2](http://ubuntuforums.org/showthread.php?t=2189774&page=2)

---

### Post by Kirboosy on 2013-11-25
Have you updated the system with the most recent updates since installing it? There is a chance that Ubuntu is trying to update itself in the background. 

Hope that helps!
~Caboose

---

### Post by mathiashu on 2013-11-25
Thank you soo much it solved the problem! It means a lot!

---

### Post by mathiashu on 2013-11-25
Yes! I prefer having the latest updates, but now as you see it's fixed. Thanks for your reply anyways!

---

### Post by Kirboosy on 2013-11-25
Great, glad it was an easy fix! Please mark the thread as solved. (Under 'Thread Tools' on the top right of your first post)

---

