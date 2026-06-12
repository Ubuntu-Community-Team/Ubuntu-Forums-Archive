---
title: "Atheros HAL + ettercap = failure"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by Drzymalski on 2007-08-04
I have built in atheros wireless in my Toshiba m45 laptop. When i try to use ettercap with the restricted Atheros HAL driver is functioning with every application except ettercap. 

Here is the error I receive:

Listening on Ath0... 
ERROR : 1, Operation not permitted
[ec_capture.c:capture_init:146]

 pcap_open: socket: Operation not permitted 

Is there a file i need to download?

---

### Post by Drzymalski on 2007-08-05
> User@Computer:~/filters$ sudo ettercap -T -q -i Ath0 -F filter.ef -M ARP // //
ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA

Content filters loaded from filter.ef...
Listening on Ath0... 
ERROR : 19, No such device
[ec_capture.c:capture_init:146]

 pcap_open: SIOCGIFHWADDR: No such device 



I sudo'ed this time and i receive this error. What do i do?:confused:

---

