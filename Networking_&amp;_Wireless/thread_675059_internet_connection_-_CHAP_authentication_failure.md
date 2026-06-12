---
title: "internet connection - CHAP authentication failure"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by nftaus on 2008-01-22
I am a new user of the Ubuntu Linux 7.10 distribution.  I installed it on a Dell Dimension 8250 that was previously running Windows XP.  However, when I try to connect to the internet, I get a CHAP authentication failure.

I have a DSL account with AT&T.  My external modem is connected directly to my computer.   When I run "sudo pppoeconf", the ethernet cards 

eth0
eth0:avah 

are detected.  I followed the procedure outlined in the documentation.  

When I follow the procedure, I obtain the following when I try "ifconfig ppp0": 

ppp0: error fetching interface information:  Device not found

When I enter "plog", I obtain the following response:

Plugin rp-pppoe.so loaded.
pppd 2.4.4 started by root, uid0
PPP session is 5595
Using interface ppp0
Connect: ppp0 <- - > eth0
CHAP authentication failed:  Unable to authenticate
CHAP authentication failed
Connection terminated.

I have also tried using the static IP address 192.168.1.105 with subnet mask 255.255.255.0, gateway address 192.168.1.1,  with the open DNS servers 208.67.220.220 and 208.67.222.222 (also with the DNS servers given by AT&T).  In this case, only the eth0 card is detected when I run "sudo pppoeconf".  I get a CHAP authentication failure here as well.

When I try "sudo dhclient", I am told that there are no DHCP offers.  

I was unable to solve the problem with my CHAP authentication failure.  I opted to switch to Optimum Online, whose broadband service connects directly to their server using DHCP.  Consequently, I now have internet service.  I did not have to configure my modem, but I still had to configure Evolution in order to send and receive e-mail.  

Thanks,

N. F. Taussig

---

