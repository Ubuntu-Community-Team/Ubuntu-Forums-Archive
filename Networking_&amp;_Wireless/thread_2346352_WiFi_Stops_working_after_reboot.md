---
title: "WiFi Stops working after reboot"
date: 2016-12-13
forum: Networking &amp; Wireless
---

### Post by tozian on 2016-12-13
I am using Ubuntu GNOME 16.10. When I reboot the computer, the computer fails to detect any networks. However, if I *shut it down* and turn it back on, the WiFi works just fine. It also works perfectly after being suspended. Restarting NetworkManager fails to fix the problem, as does unloading the kernel module and reloading it. The kernel module being used is rtl8188ee.

I have reinstalled Network Manager, and then all of Ubuntu itself. This does not solve the problem. It most certainly is not a hardware problem, as I have no such trouble when booting Windows. Never have I been so befuddled. Is this fixable?

---

### Post by Hadaka on 2016-12-14
Hi, please open a terminal...ctrl/alt/t...then copy and paste one line at a time.
```
echo 'rtl8188ee' | sudo tee -a /etc/modules
sudo sed -i '/^exit/ d' /etc/rc.local
echo -e 'sudo modprobe rtl8188ee\nexit 0' | sudo tee -a /etc/rc.local
```
remove wired connection and any usb connections, boot and test wireless
Thanks.

---

### Post by tozian on 2016-12-14
> **Hadaka said:**
> Hi, please open a terminal...ctrl/alt/t...then copy and paste one line at a time.
```
echo 'rtl8188ee' | sudo tee -a /etc/modules
sudo sed -i '/^exit/ d' /etc/rc.local
echo -e 'sudo modprobe rtl8188ee\nexit 0' | sudo tee -a /etc/rc.local
```
remove wired connection and any usb connections, boot and test wireless
Thanks.No luck. also the file /etc/rc.local did not exist. I had to create it.

---

### Post by tozian on 2016-12-23
bump?

---

