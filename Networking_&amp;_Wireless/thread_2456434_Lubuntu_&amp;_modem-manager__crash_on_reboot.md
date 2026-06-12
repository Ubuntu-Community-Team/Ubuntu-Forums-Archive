---
title: "Lubuntu &amp; modem-manager : crash on reboot"
date: 2021-01-11
forum: Networking &amp; Wireless
---

### Post by rolho7 on 2021-01-11
Hello,

I have Lubuntu 16.04.5 LTS on an ARM board ([https://www.friendlyarm.com/index.php?route=product/product&product_id=227](https://www.friendlyarm.com/index.php?route=product/product&product_id=227)). All is going well, except one big problem with 4G...

By default, I can create a "Mobile broadband" connection but I can't connect on it. So i install "modem-manager" with "sudo snap install modem-manager" command.
I now can connect on my 4G and it works.

But the problem is that it crashes on every reboot (black screen). I did many Lubuntu fresh installs and some problem everytime, when i install modem-manager with "sudo snap install modem-manager", I could not reboot anymore after that (black screen).

Thank you very much in advance for answer,
Best regards!

---

### Post by rolho7 on 2021-01-20
I found the problem !!!
Add "blacklist qmi_wwan" to /etc/modprobe.d/blacklist-modem.conf file
Reboot
It works!

---

