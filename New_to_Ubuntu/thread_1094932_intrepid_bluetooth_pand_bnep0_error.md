---
title: "intrepid bluetooth pand bnep0 error"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by emimathews on 2009-03-13
I want to connect to my robot running embedded linux and if I do the following from Ubunut hardy everything works perfectly.
sudo pand --listen --master -d NAP
sudo pand --connect deviceid
sudo ifconfig bnep0 ipaddr
I can enter the passkey and the bnep0 is created automatically. I can set the ipaddress and login the device using ssh.

But if I do the same from intrepid, it asks for passkey and it pairs. But gives the following error when I try to set the ipaddr
sudo ifconfig bnep0 192.168.4.20
SIOCSIFADDR: No such device
bnep0: ERROR while getting interface flags: No such device

Otherbluetooth services like file transfer and receive from mobile phones, remote control etc are working. So is it a problem in the network manager?

---

