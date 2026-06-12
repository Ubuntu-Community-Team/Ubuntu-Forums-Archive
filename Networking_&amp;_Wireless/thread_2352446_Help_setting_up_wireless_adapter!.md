---
title: "Help setting up wireless adapter!"
date: 2017-02-12
forum: Networking &amp; Wireless
---

### Post by burns-kyle23 on 2017-02-12
Hello, I recently built a PC and didn't want to purchase an OS so I decided to go with Ubuntu. i am unable to have a wired connection long term and need to find a way to set this wireless adapter I found to work with Ubuntu. It is a D-Link DWl-g122, I have searched for instructions on how to set it up but it is confusing and i don't know where to start! I have a little bit of experience with linux but not enough to know how to do this. Thanks!

---

### Post by Hadaka on 2017-02-12
Hi, please open a terminal ...ctrl/alt/t..then Copy and paste ..
```
uname -r
lsusb
modinfo rt73usb
rfkill list all
```
post the output
Thanks.

---

