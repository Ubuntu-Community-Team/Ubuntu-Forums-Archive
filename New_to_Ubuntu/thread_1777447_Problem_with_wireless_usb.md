---
title: "Problem with wireless usb"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by anaa on 2011-06-07
D-Link Wireless adapter  DWL-G122 uses this module rt73usb

works on ubuntu 10.10
now doesn't work on 11.04

Well, it comes up in the applet, but is greyed out, and the ap's 
don't show up. lsmod shows the modules

---

### Post by wildmanne39 on 2011-06-07
> **anaa said:**
> D-Link Wireless adapter  DWL-G122 uses this module rt73usb

works on ubuntu 10.10
now doesn't work on 11.04

Well, it comes up in the applet, but is greyed out, and the ap's 
don't show up. lsmod shows the modulesHi, have you looked in additional drivers to see if there is a driver? Put these commands in a terminal
```
sudo lshw -c network 
```
```
nm-tool
```
```
ifconfig
```
Paste results in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read. Do this for each command.

---

