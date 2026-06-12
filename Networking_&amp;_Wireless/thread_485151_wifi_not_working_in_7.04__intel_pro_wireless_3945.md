---
title: "wifi not working in 7.04 / intel pro wireless 3945"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by gonzalezcarlos on 2007-06-26
Hi,

I've got a Dell Inspiron 640m with an Intel Pro Wireless 3945. On top of that, I've got Feisty running. 

I see that feisty comes with the ipw3945 drivers, and in fact the network manager shows all the SSIDs of the wifi networks near here. But when I try to connect to my own one, the link is established (as shown in the message in the /var/log/messages), but the network is not working properly due to the following error:

dhcdbd: Unrequested down :3

I've done several ifdowns and ifups, and I've seen that the dhcpclient is trying to obtain a lease but cannot contact any dhcp server.

If I switch to windows, everything is working properly.

Could you give some hints or suggestions about how to fix the problem?

Thank you very much in advance,

Carlos

---

### Post by spd106 on 2007-06-26
Hi Carlos,

I am experiencing similar symptoms with both my Atheros and Broadcom cards. At least for me the problem is intermittent. I have found that sometimes I can connect if I remove and then reload the wireless card's driver as so:
```
sudo modprobe -r ipw3945
```
then 
```
sudo modprobe ipw3945 
```
Though I use bcm43xx or ath_pci, instead of ipw3945.

I wish I knew of a more permanent solution.

Good luck

---

