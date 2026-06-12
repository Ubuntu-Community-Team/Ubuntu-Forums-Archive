---
title: "[SOLVED] Linksys wpc11 ver4 wireless, rtl8180l controller"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by bhold on 2007-12-25
Trying to get wireless working on Dell Inspiron 5100, Ubuntu Desktop 7.10, with Linksys wpc11 ver. 4 wireless-b card, rtl8180 ethernet controller. There is a lot of info in the forums and by googling this topic.  At the following link, you can read that this has been tested and works just fine in Ubuntu 7.10... says all you need to do is setup with network-manager...

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

That is great for the system this was tested on, but on my system all attempts to setup this device with network-manager result in immediate system hang.

So I'm going to try new drivers next. Maybe a native linux driver, or maybe a WinXP driver and run it under ndiswrapper. At realtek.com I found the following:

- Windows XP driver for rtl8180 that I can try with ndiswrapper.

-  Linux driver for 2.6.x kernel. These are the files I get after unzipping the Linux driver files.

-rw-r--r-- 1 bhold bhold 1891989 2005-02-18 05:52 8180_26_private.ko
-rw-r--r-- 1 bhold bhold    1234 2005-01-20 15:37 Makefile
-rw-r--r-- 1 bhold bhold    4593 2005-01-20 15:37 r8180_if.h
-rw-r--r-- 1 bhold bhold   14010 2005-01-20 15:37 r8180_pci_init.c
-rw-r--r-- 1 bhold bhold     528 2005-01-20 15:37 r8180_pci_init.h
-rw-r--r-- 1 bhold bhold    9453 2005-01-20 15:37 r8180_type.h
-rw-r--r-- 1 bhold bhold    1039 2005-01-20 15:37 readme26.txt
-rw-r--r-- 1 bhold bhold     202 2005-01-20 15:37 rls_note_1220
-rwxrwxrwx 1 bhold bhold     188 2005-01-20 15:37 wlandown
-rwxrwxrwx 1 bhold bhold    4112 2005-02-18 06:59 wlanup

So I have the following questions, help appreciated:

1. First of all, is realtek.com the best place for me to get new drivers to try? Either for a Linux driver or a WinXP driver I can run under ndiswrapper?

2. Anyone had any success installing the Linux driver? I'm not sure how to proceed. If I was to guess I would probably try sudo make but would rather proceed with caution until I can get a little more information.

Thanks for any suggestions.

---

### Post by GSF1200S on 2007-12-26
> **bhold said:**
> Trying to get wireless working on Dell Inspiron 5100, Ubuntu Desktop 7.10, with Linksys wpc11 ver. 4 wireless-b card, rtl8180 ethernet controller. There is a lot of info in the forums and by googling this topic.  At the following link, you can read that this has been tested and works just fine in Ubuntu 7.10... says all you need to do is setup with network-manager...

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

That is great for the system this was tested on, but on my system all attempts to setup this device with network-manager result in immediate system hang.

So I'm going to try new drivers next. Maybe a native linux driver, or maybe a WinXP driver and run it under ndiswrapper. At realtek.com I found the following:

- Windows XP driver for rtl8180 that I can try with ndiswrapper.

-  Linux driver for 2.6.x kernel. These are the files I get after unzipping the Linux driver files.

-rw-r--r-- 1 bhold bhold 1891989 2005-02-18 05:52 8180_26_private.ko
-rw-r--r-- 1 bhold bhold    1234 2005-01-20 15:37 Makefile
-rw-r--r-- 1 bhold bhold    4593 2005-01-20 15:37 r8180_if.h
-rw-r--r-- 1 bhold bhold   14010 2005-01-20 15:37 r8180_pci_init.c
-rw-r--r-- 1 bhold bhold     528 2005-01-20 15:37 r8180_pci_init.h
-rw-r--r-- 1 bhold bhold    9453 2005-01-20 15:37 r8180_type.h
-rw-r--r-- 1 bhold bhold    1039 2005-01-20 15:37 readme26.txt
-rw-r--r-- 1 bhold bhold     202 2005-01-20 15:37 rls_note_1220
-rwxrwxrwx 1 bhold bhold     188 2005-01-20 15:37 wlandown
-rwxrwxrwx 1 bhold bhold    4112 2005-02-18 06:59 wlanup

So I have the following questions, help appreciated:

1. First of all, is realtek.com the best place for me to get new drivers to try? Either for a Linux driver or a WinXP driver I can run under ndiswrapper?

2. Anyone had any success installing the Linux driver? I'm not sure how to proceed. If I was to guess I would probably try sudo make but would rather proceed with caution until I can get a little more information.

Thanks for any suggestions.

Well, if there is a native driver for your card, I would at least give it a shot. Its either going to work or not- I would run 'sudo make' and see what happens. It already has a makefile, so you wont need to configure one. If you are worried about it, you can use 'sudo make' and then 'sudo make checkinstall' which will allow you to remove it at a later time... (you need checkinstall first- sudo apt-get install checkinstall)

**Edit** You may need to restart networking, or even reboot for changes to take effect-

/etc/init.d/networking restart

---

### Post by bhold on 2007-12-28
I could not get the Linux driver to install - errors running make. So decided to use ndiswrapper with a 
windows xp driver.

I downloaded the Win xp driver from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

Then, set it up under ndiswrapper following instructions at
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

The only thing that took me a few tries was the driver name for the entry in /etc/modprobe.d/blacklist,
first I tried rtl8180 and that did not work, still hung the system during network-manager configuration. 
Adding r8180 for the blacklisted driver name worked. This is the string that shows up running 
ndiswrapper -l as alternate driver.

---

### Post by giganerd on 2008-01-19
I had the same problems as you and your post really helped me out.  Thanks!  I just downloaded the XP driver you linked to, installed via ndiswrapper, blacklisted it like you said, and my hardware started working.

However, I was unable to connect to my wireless network, but installing and using Wifi-Radar seemed to allow me to connect to my wireless network (using WEP).

---

