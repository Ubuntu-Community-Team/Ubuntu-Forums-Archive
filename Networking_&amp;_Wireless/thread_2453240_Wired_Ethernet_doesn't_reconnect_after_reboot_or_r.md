---
title: "Wired Ethernet doesn't reconnect after reboot or resume on 20.10"
date: 2020-11-05
forum: Networking &amp; Wireless
---

### Post by fcosentino on 2020-11-05
Hi folks,

I installed recently Ubuntu 20.10 on my Lenovo Thinkpad T450s notebook. Everything works well except that after reboot, wired network requires unplugging / plugging back the cord to be enabled again. I tried to disable/enable wired network using the UI switch, no luck.
I have many other devices using a mix of wired and wireless network connected through my Asus AX11000 router and no issues whatsoever, only this Ubuntu notebook seems to play up.
Wireless has no issues.
The notebook uses Intel Ethernet Connection I218-LM (Clarkville) according to specs online. It works fine on Windows 10. Any ideas?

---

### Post by TheFu on 2020-11-06
Intel 2.5Ghz network chips have shown issues for many people here.  Sorry.

Intel has put out updated drivers, but those didn't help any of the people we've tried to help. Most have spent $25 to get an older Intel NICs that use the e1000e or igb drivers instead.  The igb drivers are expected to handle high, sustained, traffic better than other non-server solutions.

But because you are using a laptop, there isn't much to be done except to watch for updated drivers from intel. [https://downloadcenter.intel.com/product/71307/intel-ethernet-connection-i218-lm](https://downloadcenter.intel.com/product/71307/intel-ethernet-connection-i218-lm) has an update from Oct 1 2020

---

### Post by fcosentino on 2020-11-06
Thanks for your reply. Is this a specific issue in Ubuntu, e.g. has anyone else tried another Linux distro to see if the problem persists? I was thinking to try Linux Mint for example.

---

### Post by TheFu on 2020-11-07
I don't know. Can't hurt to try, but since Mint is based off LTS Ubuntu and you are running non-LTS ubuntu for some reason, I'd assumed you wanted to be on the bleeding edge. Mint is based on 20.04.  Perhaps try Fedora or SuSE to get farther away from debian-based issues.  But really, the driver is the driver, regardless of distro, so I wouldn't expect it to matter, but you never know until you try.  If it was me, I'd download the driver from Intel, read the README, and follow their instructions.

I don't have the hardware you do. Few people will, but hopefully, someone here who solved the issue will post.  Did you search these  and other forums for your specific chip, driver, issues?

---

