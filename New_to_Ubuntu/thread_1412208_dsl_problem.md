---
title: "dsl problem"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by crip720 on 2010-02-20
Hi . I think I have a problem with ubuntu 9.10 not seeing my modem or ethonet card. I am using an acer aspire 5536 laptop dual-booted with windows 7 and ubuntu 9.10. with a Broadcom netlink gigabit ethernet [card?] type 802.3, and a wired Ovislink adsl modem. Network manager says device not managed. Part of ifconfig reports; etho Link encap: Ethernet HWaddr 00:1f:16:a8:c2:72, inet6 addr: fe80::21f:16ff:fea8:c275/64 Scope link, UP BROADCAST RUNNING MULTICAST MTU; 1500 Metric:1, RX pactets :18, TX pactets 23, Txquevelen : 1000, rx bytes 1294 tx bytes 1592, Interrupt :16 rest of numbers is zeros I install 9.04 from cd and dsl worked right . upgraded to 9.10 from network and restarted and dsl does not work. tried power management in windows, and turning off modem and on again. also downloaded networkmanager from launchpad, and maybe loaded to ubuntu. I am a newbi at this so any ideas will help. also can you print correct version of ishw-C, tried diffent types but keep getting comand not found. no wirless on this setup. thanks colin.

---

### Post by jmite on 2010-02-21
can you give the output of lspci?

Linux and broadcom are fickle partners... you might want to see if you can download the proprietary broadcom driver on another computer, put it on a usb stick and install it on your ubuntu system.

Network manager is mostly just a graphical frontend to other stuff, so it's not likely the source of the problem. I suspect a driver issue, but if you want, you could try using wicd, which is an alternative to network-manager...

---

