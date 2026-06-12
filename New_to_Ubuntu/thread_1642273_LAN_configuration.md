---
title: "LAN configuration"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by abhishek.mathur on 2010-12-10
Hi . . I am a newbie . .
I am running Ubuntu 9.04 as a live user (running from pen drive) on my sony vaio VPCM126AG netbook....
I am trying to connect to my DLINK DIR-300 router on ethernet port to connect my netbook to internet but it is not working... DHCP is enabled in my router...I have tried following methods:
Network manager -> Auto Eth0 -> IPV4 settings

1. connection type -> DHCP ...... Eth0 not getting connected
2. connection type -> DHCP . . manually assigned DHCP client id  . ... Eth0 not getting connected
3. connection type -> Manual ..ip address . .subnet mask..gateway..DNS servers ..all specified..->Eth0 gets connected but I can not access internet..neither could i access my router through web interface

4.I have also tried other 2 settings..link local and DHCP(addresses only)..but neither of them is working..

I have even checked by modifying the network configuration file in /etc/networks/  . . . but still the problem remains as it is..


Please suggest solution for this problem..

---

### Post by BugBuster on 2010-12-10
First of all, Ubuntu 9.04 has already reached its end of life, so if you are serious about Ubuntu try 10.04 LTS or latest 10.10 if possible.

And when you connect to your modem using ethernet, can you ping your modem?

---

### Post by abhishek.mathur on 2010-12-10
My router is connected to my modem and I am trying to connect to my router over eth0... and I am not able to ping to my router .  .neither to my modem..

---

