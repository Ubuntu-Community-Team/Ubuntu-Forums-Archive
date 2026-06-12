---
title: "Ethernet port configuration problem"
date: 2014-06-08
forum: Networking &amp; Wireless
---

### Post by Jacob_Tennant on 2014-06-08
I am trying to setup a TFTP server so as to ref lash some Cisco 7962 phones.

From the directions I need to have a TFTP server & a DHCP server running on the same computer so once the phone is booted into is flash config mode it will grab a IP address and then it will begin the TFTP install of the new firmware.

I have a laptop setup with 12,04 server running TFTPD 9working) and sic dhcp server (appears to be working).

My problem is when I set the eth0 with a static address as 192.168.1.1 the port eth0 never become live?

If I set it to DHCP it works fine.

The computer is connected to the phone via a crossover cable.

***Is there any way to tell eth0 to stay active even if there is nothing connected to it?

If I enter ifup eth0 with the crossover cable connected to the phone it fails, ir I enter ifup eth0 with no cable it fails.

---

### Post by Rsxhawk on 2014-06-11
Display the output of:

# cat /etc/network/interfaces
# ifconfig

And install ethtool 

# sudo apt-get install ethtool
# sudo ethtool eth0

---

