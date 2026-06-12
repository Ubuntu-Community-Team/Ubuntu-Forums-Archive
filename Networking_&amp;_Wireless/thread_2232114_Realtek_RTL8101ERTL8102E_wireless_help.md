---
title: "Realtek RTL8101E/RTL8102E wireless help"
date: 2014-06-29
forum: Networking &amp; Wireless
---

### Post by jessie3 on 2014-06-29
I recently accidentally formated the partition of my wife's laptop. I had to install Ubuntu and she's surprisingly willing to give it a try, she might even go pro.

However as it stands I need help connecting her computer through wireless without ethernet cables.

She has a Dell Inspirion 15.

All help appreciated in advance

---

### Post by chili555 on 2014-06-29
RTL8101E is your ethernet device, not wireless. Let's find that wireless. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my keyboard on the same key with \.

Thanks.

---

### Post by jessie3 on 2014-06-29
```
breanna@breanna-Inspiron-3521:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
```

```
breanna@breanna-Inspiron-3521:~$ rfkill list all
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
breanna@breanna-Inspiron-3521:~$ ^C
```

---

### Post by chili555 on 2014-06-30
This is a somewhat newer device for which the support is included in recent Ubuntu versions and pretty tricky in older versions. If you are not running Ubuntu 14.04, I highly recommend you do so.```
lsb_release -d
```If you are, get a temporary wired ethernet connection and do:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```Detach the ethernet, reboot and enjoy!

A certain 70-something grandmother in this house, who uses and loves Ubuntu, offers her encouragement to your wife. She says to take her time to learn it and enjoy life blissfully free of viruses, trojans, and software for an additional fee!

---

### Post by jessie3 on 2014-06-30
Thank you so much for your help. Currently at work but when I arrive home I will do the steps and post my results, hopefully solving this issue.

---

### Post by jessie3 on 2014-06-30
It worked for her computer !

---

### Post by chili555 on 2014-06-30
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

---

