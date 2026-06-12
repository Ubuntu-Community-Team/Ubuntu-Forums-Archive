---
title: "problem with wifi (iwlwifi)"
date: 2016-06-19
forum: Networking &amp; Wireless
---

### Post by ax-lx on 2016-06-19
Hello
   My wifi connection has some problem: when i first boot and loggin to KDE it is connected to my wifi modem automatically and when clicking on the network-manager icon it display all the wifi Access-Points' names around me . But if i disconnect from my wifi modem, immediately the list of those Access-Points disappeared from network-manager icon ( even my wifi modem name disappeared ) and i can not reconnect to any wifi . In this state occur i run command "service network-manager restart" from root login and after running that command again the list of Access-Points' name is appeared and again it connects to my wifi modem automatically. 

   I am using "Kubuntu 16.04" and my computer is a HP-notebook with wifi module card: "Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)" as lspci reports. Its Kernel is "4.4.0-24-generic #43-Ubuntu x86_64". of course this problem was existed with kernel "4.4.0-22" too.
A glue is that when i installed Kubuntu 15.04 on this notebook 1 year ago it has no any problem with its wifi and all of above problem begins after installink Kubuntu 16.04 . and i installed now the updates fro network-manager and linux kernel as above but the problem exists yet.

  A report of /var/log/syslog after disconnectiong from my wifi modem is at pastebin site and you can see here: [http://pastebin.com/jHtCKz3R](http://pastebin.com/jHtCKz3R)
  A report of /var/log/syslog after doing "service network-manager restart" is at pastebin site and you can see here: [http://pastebin.com/pUEjDfXR](http://pastebin.com/pUEjDfXR)

Please help to solve this problem :(

---

