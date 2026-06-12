---
title: "phy0 disappear (and no wifi scan) after installation of 18.04.4 LTS on lenovo s340"
date: 2020-02-18
forum: Networking &amp; Wireless
---

### Post by hemanlmf on 2020-02-18
I am trying to install Ubuntu Mate 18.04.4 on my lenovo ideapad s340. The wifi is working when I try the OS via bootable usb as well as throughout the installation progress. I run the wireless info script and the result is as follows:
[https://pastebin.com/txRLhYPb](https://pastebin.com/txRLhYPb) 


However, after a fresh installation (third party driver installed as well), I cannot find any wireless network after I log in. The result of wireless info script is as follows:
[https://pastebin.com/5U3FSMyi](https://pastebin.com/5U3FSMyi) 


I try out several methods in this forum as well as the Internet like "blacklist ideapad-laptop"... However, I guess the problem is not hard block due to the ideapad hotkey. As I am aware of, aafgarci ([https://ubuntuforums.org/showthread.php?t=2436060](https://ubuntuforums.org/showthread.php?t=2436060)) seems to have similar problem. When I tried to install 18.04.3 two months ago, the wifi was even not available throughout the installation progress. I used Windows in the mean time for my work.


Please let me know if I can do anything. Thank you very much for your time.

---

### Post by Jim Z on 2020-02-19
yep, I have the same problem.  Dell Inspiron 13 5000, WiFI works in the USB installer, but after installing it acts like there's no wifi adapter.

---

### Post by wildmanne39 on 2020-02-19
Hello Jim Z, please start your own thread so you and the OP of this thread can get the individual help you both need, most of the time while the issue seems the same the cause is different.

Thanks

---

### Post by hemanlmf on 2020-03-03
Many thanks to @[chili555]("https://askubuntu.com/users/19421/chili555") in [https://ubuntuforums.org/showthread.php?t=2437891](https://ubuntuforums.org/showthread.php?t=2437891), the problem is fixed by booting 5.3.0-28-generic kernel in grub now.

---

