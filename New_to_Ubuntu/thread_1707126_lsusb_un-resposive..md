---
title: "lsusb un-resposive."
date: 2011-03-14
forum: New to Ubuntu
---

### Post by Carter12s on 2011-03-14
I just finished my first install of ubuntu, and i started trying to set up my usb wireless adapter, but when i ran lsusb in the terminal the terminal simply died ctrl+c did nothing, in fact nothing at all could bring back the terminal. I was forced to close it and open a new terminal. I am brand new to linux and have no idea where to start on tackling this problem, any ideas?

---

### Post by coolbrook on 2011-03-14
Which adapter are you trying to install?  Make and model number please.

---

### Post by lkraemer on 2011-03-15
When you say you ran lsusb are you stating you typed lsusb in a
Terminal Window (Console) as shown below, then depressed the ENTER KEY?
```

[larry@localhost ~]$ lsusb
Bus 002 Device 004: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5130 IMC Networks 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[larry@localhost ~]$

``` 
You're output may very a bit because I did this in Fedora 14.


Open a Terminal Window and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci > junk.txt
lsusb >> junk.txt
lshw -C network >> junk.txt
lsmod >> junk.txt
ndiswrapper -l >> junk.txt
cat /etc/modprobe.d/blacklist.conf >>junk.txt
iwconfig >> junk.txt

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the file.


lk

---

