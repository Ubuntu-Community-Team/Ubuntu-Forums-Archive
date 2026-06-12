---
title: "DNS servers not remembered"
date: 2005-10-30
forum: Networking &amp; Wireless
---

### Post by mfyahya on 2005-10-30
I have ubuntu 5.10 set up on my laptop at home behind a DSL modem/router set up for DHCP. However I need to enter my ISP's two DNS servers manually. I did this in the DNS tab inside the Network Settings dialog box, but whenever I reboot the DNS server IPs are replaced with 192.168.1.1 (which is my router's address), and I have to enter the correct IP addresses again to connect to the net.

Is there any way to make the change permanent?

---

### Post by DarkB on 2005-10-30
ok the here is what you u have to do:

edit /etc/dhcp3/dhclient.conf and uncomment (remove the # sign) the line that starts with prepend replacing 127.0.0.1 with your dns servers (seperated by commas).

that should get it to work


DarkB

---

### Post by mfyahya on 2005-10-31
Thanks, it worked.
I still get the 192.168.1.1 address at then end, but guess it doesn't matter now.

---

### Post by SUiSQU on 2005-11-02
I had this same problem but I think it's fixed now as well. Why arent these settings kept by default?

---

