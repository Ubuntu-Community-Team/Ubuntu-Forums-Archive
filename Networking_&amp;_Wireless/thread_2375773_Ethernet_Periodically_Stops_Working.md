---
title: "Ethernet Periodically Stops Working"
date: 2017-10-27
forum: Networking &amp; Wireless
---

### Post by ilia3 on 2017-10-27
Hello,

I have wired internet connection. Connection periodically stops working for about 20-30 seconds, time between these stops is not fixed, sometimes it's 2-10 minutes or so. It is very frustrating while working on something important.
Even though network icon remains same, as if it is connected, internet is gone, can't ping gateway, same happens on DHCP and Manual configuration.
I have no idea from where this issue originated from, everything was working fine about one month ago, probably I did some update and it broke the system or it's ethernet controller hardware problem, I don't know. 
After hours of searching/trying to fix this issue, decided to post here, if any of you can help me.

Here are some information about my system/hardware:
OS: Ubuntu 16.04 LTS
Kernel version: 4.10.0-37-generic (tried also running with 4.10.0-33-generic - which I had month ago when everything was working perfectly, but nothing changed, )
Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
Driver: e1000e 3.3.6-NAPI (This I manually updated after encountering problem, As of kernel, this couldn't fix the problem)

I saw apt-log and couldn't find any ehternet controller driver update recently.

Thanks for paying attention, hope you can provide any useful information.
Please ask me if any command output will give you additional information for troubleshooting and I'll post it.

---

### Post by TheFu on 2017-10-27
Swap the switch port, ethernet cables, and NIC.  If it worked previously, perfectly, I'd restore from a backup from when it worked to validate that is really true.

Also, booting from a flash drive and using that for some time to see if it is OS specific would be good too.  TinyCore is ... er ... tiny and runs completely from RAM.  The distro is 17MB in size, so not a huge download.

Lastly, connect up a different computer to the same cable, switch port and see if that all works.

Off the top of my head, that's all I got.

---

### Post by laduyp74 on 2018-07-14
I have similar issue w/ 18.04 where it'd sporadically disconnect and it's wired also.  It's not the internet b/c other devices are fine; and if I turn off "Wired Connected" (upper right) then turn it back on, there's internet again.

---

### Post by praseodym on 2018-07-15
@ladyup74: Same device? Lets see
```

lspci -nnk
lsmod
ifconfig -a
```

---

