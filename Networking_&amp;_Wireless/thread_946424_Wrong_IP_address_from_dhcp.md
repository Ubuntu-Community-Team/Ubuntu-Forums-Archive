---
title: "Wrong IP address from dhcp"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by Helge on 2008-10-13
I have a dual-boot machine at my workplace, with a "professionally" installed Suse 9 and with Ubuntu 8.04, which I have installed myself. The machine gets its IP address and host name from the network. Other machines on the network are mostly Solaris and Suse.

When I boot with Ubuntu, I get the right hostname, but the wrong IP address. 
Expected IP: 147.214.195.156
Actual IP:   147.214.195.141.
The hostname is the same: ws7146.

Two things show which IP-address the right one:
- The expected address is used by the Suse installation.
- The command "nslookup ws7146" returns the expected IP-address.

Generally, you would expect the address returned by
  nslookup `hostname`
to be the same as given by
  ifconfig | grep "inet addr"
but it isn't on this machine.

I tried with a Ubuntu live-CD (also 8.04), and it also used the faulty IP address. I've tried various things with /etc/network/interfaces. I've rebooted and restarted /etc/init.d/networking.

* Is this a bug in Ubuntu? (I would suspect the dhcp3 package)
* Is it a configuration error?
* What kind of information moves between the Ubuntu host and the dhcp server, which leads to this error? 
* Is there a workaround?


Helge

---

### Post by koenn on 2008-10-13
the suse may be configured to send some sort of identifier to the dhcp server, which in turn would be configured to assign an address based on this identifier. 
Talk to your network administrator.

you could have a look at the dhclient config and configure it to send its hostname if it doesn't already do that, then see if it gets the desired address ...

---

### Post by jimv on 2008-10-13
Kinda odd, because IP addresses are usually leased to MAC addresses.  I'd check the client lease table on the DHCP server to see what MAC address is associated with both of those IPs.

---

### Post by koenn on 2008-10-13
usually, yes, but at least the dhcp server I'm running can assign addresses based on hostnames,  and on number of custom tags

a very likely scenario is that the suse sends its hostname and requests a continuation of its lease, and the ubuntu just requests a new lease without mentioning its hostname, so it gets a new lease with a different address, and continues to ask for renewals of *that* address.

---

### Post by Iowan on 2008-10-13
**dhclient** can be configured to send it's hostname, but I think the **/etc/dhcp3/dhclient.conf **file  has that line (#send hostname "andare.com"; or something like that) commented out by default.

---

### Post by Helge on 2008-10-18
Thank you for all suggestions and hints. The problem is still unsolved, but I'm prepared to give it up for now, because of higher priorities. 

Probably a lot could be learned from a wireshark analysis of the dhcp negotiation at startup, but I haven't been able to see it all; my 3com OfficeConnect switch doesn't send all packets to the computer running wireshark. 

I have also to learn where the "network" stores information that connects MAC, IP and hostname. It uses NIS to connect IP and hostname, even when the host is powered down. I guess the MAC-IP connection comes from a dhcp server closer to the host than the NIS server is. In other words, the computer gives the network it's MAC address and the IP address is returned. I haven't found the IP address stored on disk in the Suse installation, so it seems to be decided from the dhcp server. The hostname probably is given to the host later, when NIS is started. When I find more time to dig into this, I will start from there.

Thank you all.

---

### Post by prodigel on 2010-04-20
Found the cause yet? I'm facing the same problem.

---

### Post by Helge on 2010-04-20
> **prodigel said:**
> Found the cause yet? I'm facing the same problem.

Not really, but I'm not having the problem any longer. I'm don't think the problem was in the Ubuntu machine, but rather that my RedHat machine was configured oddly by the sysadmin, or the network function that maps MAC addresses to IP numbers. Later, when I got my RedHat machine replaced with another RedHat, I had the same problem initially, but it was solved. I don't remember the details. Sorry. :(

---

