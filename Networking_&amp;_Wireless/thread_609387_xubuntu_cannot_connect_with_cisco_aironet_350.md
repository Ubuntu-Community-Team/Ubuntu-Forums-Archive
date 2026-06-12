---
title: "xubuntu cannot connect with cisco aironet 350"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by manqueller on 2007-11-10
I have a sony vaio that I was running Ubuntu 6.06 on.  I decided to install xubuntu since it should perform better on this old hardware (which it does).  I now can't get it to connect to my WRT54GL using the Cisco aironet 350.

Previously with Ubuntu 6.06 I had the same problem, then I was able to get it to accept a dhcp by using : sudo dhclient eth1 from the teminal.  Now it's not working it attempts to discover four times and then says no DHCPOFFERS received.  No working leases in persistent database - sleeping.  

Under network settings I see two devices besides the modem, one is wifi0 and the other is eth0.  This laptop has no ethernet port, only the pcmcia wifi card, so I don't know why I see an eth0 at all.  

I tried removing network manager as this thread suggested:
[http://ubuntuforums.org/showthread.php?t=398144&highlight=Network-Manager](http://ubuntuforums.org/showthread.php?t=398144&highlight=Network-Manager)  
and still after the re-boot I get the same problem.  
Anyone have any ideas, or should I just buy a network card that is suported?

Thanks!

---

### Post by jaysons on 2007-12-07
I am having same issues, try giving this a look...

[http://icebreaker.wordpress.com/2007/11/03/wireless-ubuntu-710-love/](http://icebreaker.wordpress.com/2007/11/03/wireless-ubuntu-710-love/)

---

