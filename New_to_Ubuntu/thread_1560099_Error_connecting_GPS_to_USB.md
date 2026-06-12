---
title: "Error connecting GPS to USB"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by amarumayo on 2010-08-24
Hi all,

I am trying to connect my GPS in Ubuntu to be recognized by QLandkarte.  When I plug in the device I get the following error:

 p, li { white-space: pre-wrap; }  Failed to query loaded maps. Failed to configure USB: could not set config 1: Device or resource busy
 
 The kernel driver 'usbfs' is blocking. Please use 'rmmod usbfs' as root to remove it temporarily. You might consider to add 'blacklist usbfs' to your modeprobe.conf, to remove the module permanently.


I am not sure what that means or how to go about solving it. 



Thanks in advance for any help that anyone can provide. 



Chris

---

### Post by khelben1979 on 2010-08-24
To me it looks like that: ```
sudo rmmod usbfs
``` would solve your problem. Start an X terminal and just type it in (use at your own risk, but it looks safe).

The error message explains that a kernel module is causing a problem in your Ubuntu system and that it needs to get temporarily removed. A kernel module is like a driver which gets loaded by the Linux kernel when the Ubuntu system decides what is needed.

If uncertain, making a google search and using your exact model of your GPS is another way of searching for relevant information in this.

---

