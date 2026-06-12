---
title: "Weird network problem after Installed VWware"
date: 2005-08-26
forum: Networking &amp; Wireless
---

### Post by ismxray on 2005-08-26
I meet a strange network problem after I installed VMWare.  The DHCP for the private network is in the range of 172.36.*.*, the system can get a correct IP from the DHCP server. But after I installed the VMWare5, the system get an IP as 192.168.123.103, it is even not in the virtual networks of vmnet*.  Even I uninstalled the vmware package complete, it still get the weird IP, and it change the /etc/resolv.conf. 

Which file controls this? How can I let the network get the correct IP from the private network instead from the virtual network of the computer itself? 

If I assign an static IP to the netcard eth0 and change the /etc/resolv.conf, the network could work. But if I change the eth0 back to dhcp mode, it again use the 192.168.123.103 adress.  How could this happen? ](*,)  ](*,)

---

