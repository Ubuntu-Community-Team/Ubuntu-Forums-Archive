---
title: "Need ralink driver install help"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by Jackie999 on 2008-05-06
I am trying to install the rt2870 ralink driver but am having trouble understanding all of the posts and conflicting information.

I am using the ndiswrapper at the moment, but I'm pretty sure it's causing the hourly freezing I'm experiencing.

I know I'm supposed to do the following changes in the makefile:

```
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

```Which I follow - but I'm not sure how I change this to mine (ubunto 8.04) or..does it even need changing?

ifeq ($(PLATFORM),PC)
# Linux 2.6
LINUX_SRC = /lib/modules/$(shell uname -r)/build

Thanks.

---

