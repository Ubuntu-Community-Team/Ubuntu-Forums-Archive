---
title: "Question about multiple Vlans in 14.04 Desktop"
date: 2016-01-21
forum: Networking &amp; Wireless
---

### Post by Jason_Simmerman on 2016-01-21
I need some assistance here if anybody can help.  Here is what I am doing.  I am a network engineer and I'm building a testing box that will host several Virtual machines to fully test a network firewall we are upgrading.  The virtual machine software will be VMware Workstation (yes it's legit/paid for).  Ultimately my goal with the virtual machines is to ensure all firewall configurations are going to work out 100% prior to physically installing the unit at the site and want to limit surprises.  Decided to use an old Panasonic Toughbook CF-52 as my testing platform 'Basically it's what I have at my disposal to test with'.  I installed Ubuntu 14.04 AMD64 Desktop on the laptop in question.  I also installed the following from the repository.

apt-get install vlan 
apt-get linux-headers-'for my distro'

I then modified the /etc/network/interfaces file and added the following to the configuration so I could validate the 3 zones and so on.

auto eth0.10
iface eth0.10 inet static
        address 192.168.10.250
        netmask 255.255.255.0
        gateway 192.168.10.1

auto eth0.20
iface eth0.20 inet static
        address 192.168.20.250
        netmask 255.255.255.0
        gateway 192.168.20.1

auto eth0.30
iface eth0.30 inet static
        address 192.168.30.250
        netmask 255.255.255.0
        gateway 192.168.30.1

The laptop IPs on the Vlans just for local testing before I went through mapping everything to VMNICs.  As it is right now Vlan 10 works AOK, but Vlan 20 and 30 never come up.  Doing an ifconfig shows the interfaces up,  but you can't ping anything and there are no ARP entries or anything (Yes I'm sure the firewall has ping open).  I thought about maybe there being a hardware limitation, but I'm fairly certain the laptop NIC supports Vlan tagging given it works with the first.  

Any suggestions why the second and third vlans are not working?  I have exhausted my GoogleFU on this one.  Thanks guys.

---

### Post by Jason_Simmerman on 2016-01-26
Ok!  Does anybody have any suggestions?  Tried ESXI last night, but it needs over 4 gigs of memory (laptop has only 4) so can't do that.  Some help would be appreciated here.

---

