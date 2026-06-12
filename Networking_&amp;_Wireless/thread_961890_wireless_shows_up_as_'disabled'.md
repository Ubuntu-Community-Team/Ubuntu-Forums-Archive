---
title: "wireless shows up as 'disabled'"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by sambuca on 2008-10-28
I have Ubuntu 8.10 RC1 running on my desktop, and I decided to put it on my notebook.  (I'm still fairly new to Ubuntu/Linux, so excuse my ignorance)

from a terminal, I am typing 'lshw -C network'

I see in the list:
*-network:0 Disabled
description: Wireless interface
logical name: wlan0

If I go to Administration -> Hardware Drivers, I see it lists my Broadcom B43 wireless driver.  I have the option to 'enable' it here, however clicking the 'activate' button does nothing.

Um, what am I missing to 'enable' the wireless?  I should add, the onboard NIC does not work, if that at all matters.

---

### Post by Dvorakis on 2008-10-28
The same thing happens to me... I heard that booting an older kernel fixes it but I'm not sure how to do that.

---

### Post by Ayuthia on 2008-10-28
Can you tell me the numbers that you get when you type (in the Terminal):
```
lspci -nn|grep 14e4
```
I am looking for the numbers in [14e4:43xx].

---

### Post by sambuca on 2008-10-28
> **Ayuthia said:**
> Can you tell me the numbers that you get when you type (in the Terminal):
```
lspci -nn|grep 14e4
```
I am looking for the numbers in [14e4:43xx].

Sure.  I get [14e4:4320]

---

### Post by Ayuthia on 2008-10-28
> **sambuca said:**
> Sure.  I get [14e4:4320]

You might try this:
[http://ubuntuforums.org/showpost.php?p=6028741&postcount=4](http://ubuntuforums.org/showpost.php?p=6028741&postcount=4)

It is a set of instructions on what to download.

---

