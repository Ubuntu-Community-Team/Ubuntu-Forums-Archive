---
title: "wireless driver problem"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by wolfyy on 2008-08-19
hi I installed ubuntu 8.04 today, and now I dont know which driver should I use, for wireless modem. my notebook is lenovo thinkpad R61 T8100. 

bloetooth works corectly, but wireless not. as I say I think I need a correct driver for modem and I have no idea where to find it.:(

can anyone help me??? 

best regards,wolfy

---

### Post by falcon61102 on 2008-08-19
Could you go to your terminal, run and post the results of:
```
lshw -C network
```

That will give us information on your hardware to be able to help you.

---

### Post by wolfyy on 2008-08-19
this is copy paste from terminal:

andrej@andrej-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566MC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:15:2f:22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:27:1b:fb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
andrej@andrej-laptop:~$

---

### Post by falcon61102 on 2008-08-19
By the look of that, it looks like you driver is installed.  If you click on the network manager in the upper right-hand corner of your screen, can you see any wireless networks?  The network manager should look like two black monitors, one atop the other.  Also, try right-clicking on it and ensuring that Wireless Enabled is checked.

---

### Post by wolfyy on 2008-08-19
wireless connection is enabled, the problem is that I cant start my wireless antena. bluetooth start by itself, but wireless dont. I tryed instal wireless assistant, but when I lunch it this error shows: 

Could not launch menu item

Unknown encoding of: file:///usr/share/applications/kde/wlassistant.desktop

---

### Post by falcon61102 on 2008-08-19
Are you using the KDE desktop?  It looks like that version of the program was for KDE and if you are not using KDE, then it won't work for you.

---

### Post by wolfyy on 2008-08-19
do you have any idea how can I turn on wireless radio?? :confused:

---

### Post by falcon61102 on 2008-08-19
Were you able to get your internet working?

---

### Post by wolfyy on 2008-08-19
now I am on internet with cable, but I need wireless. I have only problem now looks like how to turn wireless radio on.

I have Fn+F5 for wireless and bloetooth radio. if I hold Fn+F5 bluetooth turn off and on. but the indicator for wireless is still off always :(

and thanks for helping me:)

---

### Post by wolfyy on 2008-08-19
ok maybe I find something, but now I need to know where I must write this. sry I am newbi on linux so I need a little help :)

I find the thread with same problem, this is it:

[http://ubuntuforums.org/showthread.php?t=395729](http://ubuntuforums.org/showthread.php?t=395729)


but now I still don't exactly know what I must do:(

---

### Post by wolfyy on 2008-08-19
ok I did it :)

tnx for help falcon61102

---

### Post by falcon61102 on 2008-08-19
The first section of code on that page is simply the contents of a log on that users computer.  The next two sections of code are Script files that will run certain processes when called.  You may already have these files on your computer or you may have to create them from scratch.  

By the looks of them, they should be in you /bin/sh folder in your Filesystem.  If you can't find them there, then you are going to have to create them; to do that you simply create a new file for each, using the names there and then placing them in the /bin/sh folder.

---

