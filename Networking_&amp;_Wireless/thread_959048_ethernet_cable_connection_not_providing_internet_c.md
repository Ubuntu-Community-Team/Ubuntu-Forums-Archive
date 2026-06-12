---
title: "ethernet cable connection not providing internet connection."
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by 4ant on 2008-10-26
I have installed Hardy Heron, but cant get the internet connection to work.
I am using an ethernet cable which works fine on all other machines that use it.
It comes straight from an ethernet switch via a cable modem.
Will Ubuntu detect & install all motherboard device drivers from boot? ie: my onboard LAN card? The lights on the back arent flickering when the ethernet cable is plugged in.
Should choose DCHP as the protocol in theis case?

Thanks for your thoughts.

---

### Post by Iowan on 2008-10-26
Ideally, Ubuntu install will find/configure onboard NIC, and set up DHCP. Sometimes that doesn't happen and you must install different drivers for your NIC.  Unfortunately, I'm not really familiar with the different NICs and the process of loading a special driver.  For starters, though, you could post results of **ifconfig -a**, **lspci**, and contents of */etc/network/interfaces* file.

---

