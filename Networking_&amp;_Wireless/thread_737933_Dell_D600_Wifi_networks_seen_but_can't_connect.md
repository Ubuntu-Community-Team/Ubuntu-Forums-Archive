---
title: "Dell D600 Wifi networks seen but can't connect"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by nephmon on 2008-03-28
Hi

I've just installed Ubuntu 8.04beta on my D600. In the wireless manager I can see a bunch of networks, including my own, which is WPA-protected, and the open Google one we have here in Mt View. But whenever I try to connect to either of them, it just tries for a while and then gives up. In the system log I see:

> 
Mar 28 00:46:57 pete-ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Mar 28 00:46:57 pete-ubuntu kernel: [  823.307206] ADDRCONF(NETDEV_UP): eth1: link is not ready


and the ouput from iwconfig is:

> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0


Any ideas??

Thanks,
Pete

---

