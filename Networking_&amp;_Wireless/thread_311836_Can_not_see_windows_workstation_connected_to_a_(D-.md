---
title: "Can not see windows workstation connected to a (D-Link 504T)"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by Simon4tk on 2006-12-03
Hi

I am finding my way around Ubuntu 6.10 and, with the valuable help here have managed to make visible a 2nd hard disk. The area I am still struggling with is how to get an internet connection.
I have a D-Link 504T Router and I can ping it successfully from Network Tools. However, I cannot get beyond to the internet or see other computers on the network. My other PC is running Windows XP and I have a good internet connection from that via the same router so I know there is no problem there. I use PPPOA with the ADSL service from my ISP.

I would be grateful if someone could spell out what I need to do to get connected.

Thanks

---

### Post by John.Michael.Kane on 2006-12-06
linux/windows networking requires samba [http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)  

If your linux workstation is able to connect to the net with out issue then it maybe an issue of samba not being setup on the machine.

---

### Post by Simon4tk on 2006-12-07
Many thanks - finally got connected, especially once I had discovered to use the F5 key to see the network.

---

