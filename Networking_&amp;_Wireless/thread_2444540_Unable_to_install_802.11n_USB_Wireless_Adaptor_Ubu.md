---
title: "Unable to install 802.11n USB Wireless Adaptor Ubuntu 20.04 - Wireless-info attached"
date: 2020-05-31
forum: Networking &amp; Wireless
---

### Post by rafaelabrahamdavis on 2020-05-31
I am running into errors while trying to run install.sh which came with the wifi USB adapter  (RTL8188EUS Software Package - Linux Driver).

1) error: ‘_timer’ {aka ‘struct timer_list’} has no member named ‘data’
  956 |  ptimer->data = (unsigned long)cntx;
2) error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  957 |  init_timer(ptimer);
3) error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
 1423 |  daemonize("%s", name);

Tried - [https://askubuntu.com/questions/1170202/how-to-install-rtl8188eus-driver-on-ubuntu-18-04?](https://askubuntu.com/questions/1170202/how-to-install-rtl8188eus-driver-on-ubuntu-18-04?) - It did not solve the problem
Attaching wireless-info as mentioned in [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

[ATTACH]286060[/ATTACH]

Please help.

---

### Post by chili555 on 2020-06-01
Try the rtl8188fu process here and post back if you need further assistance.

[https://askubuntu.com/questions/1197223/install-0bdaf179-realtek-semiconductor-corp-rtl8188fu-or-netgear-rtl8812au](https://askubuntu.com/questions/1197223/install-0bdaf179-realtek-semiconductor-corp-rtl8188fu-or-netgear-rtl8812au)

---

### Post by rafaelabrahamdavis on 2020-06-01
Thanks a lot.. That worked..

---

### Post by chili555 on 2020-06-02
Awesome! Glad it's working.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

