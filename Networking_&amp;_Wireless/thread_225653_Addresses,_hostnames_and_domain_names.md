---
title: "Addresses, hostnames and domain names"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by itKiwi on 2006-07-30
[FONT="Verdana"]I am working through the server installation described in [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06) 

It's going slowly.   Got down to para 5 “Configure the network”.  My Belkin ADSL 4 port gateway router sets itself up as 192.168.2.1.  The DHCP server in the router uses addresses 192.168.2.2 to 192.168.2.100.  So the other PCs are all in this group.  The router also sets a local domain name of “Belkin” by default, and I haven't changed this.  My hostname is the default “ubuntu1”   I set up this new server with the address 192.168.2.101.   I edited the first two lines of the “hosts” file to read [/FONT]

[FONT="Courier New"]127.0.0.1   localhost.Belkin   localhost
192.168.2.101  ubuntu1.Belkin   ubuntu1[/FONT]

[FONT="Verdana"]Is this correct ?  I ask this because when I run hosts and hosts-f, I get [/FONT]

[FONT="Courier New"]hostname    ubuntu1
hostname -f     ubuntu1.Belkin[/FONT]

[FONT="Verdana"]The “Perfect” instructions say that these commands should both have the same response.  Have I got a problem ?

I can successfully ping 192.168.2.101 from another computer on the network.

Thanks[/FONT]

---

