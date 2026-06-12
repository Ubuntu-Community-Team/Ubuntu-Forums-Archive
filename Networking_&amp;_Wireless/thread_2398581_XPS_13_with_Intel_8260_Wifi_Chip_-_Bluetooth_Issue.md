---
title: "XPS 13 with Intel 8260 Wifi Chip - Bluetooth Issues"
date: 2018-08-14
forum: Networking &amp; Wireless
---

### Post by Asif_Ahmad on 2018-08-14
Hey Guys,


I have a Dell XPS 13 (9350) with an Intel 8260 wifi chip that I replaced after purchasing the machine. It appears that sometime after I updated to the new Gnome 3.28 version, my Bluetooth functionality became problematic.  I made a post a few months ago, but this is still a sore spot with my Dell XPS 13 Linux install.


It appears that when I go into the Bluetooth window under settings, NO devices are showing up in the list…it also appears to be slightly buggy.  When I try to 'enable' Bluetooth, nothing changes 90% of the time.  Sometimes from a cold boot, the Bluetooth connection will turn on correctly.   Can anyone else confirm this behavior, and if so, do you have a workaround?


Unfortunately, I do not think it’s working properly in the command line either. Here is the output I get when I run the commands:
    
            [aahmad@aahmad-pc ~]$ sudo bluetoothctl
            [sudo] password for aahmad:
            Agent registered
            [bluetooth]# power on
            No default controller available
            [bluetooth]# agent on
            Agent is already registered
            [bluetooth]# default-agent
            Default agent request successful
            [bluetooth]# scan on
            No default controller available
            [bluetooth]#


Thoughts?  Any assistance would be GREATLY appreciated.


Thanks,
Asif

---

### Post by wildmanne39 on 2018-08-14
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by Asif_Ahmad on 2018-08-15
Bump

---

