---
title: "Bonding and Bridging Question on Dell R610 - Four Network Ports"
date: 2017-01-16
forum: Networking &amp; Wireless
---

### Post by tremorsfsu on 2017-01-16
I am fairly new to the Linux world and ubuntu server. I have ubuntu 16.04.1 LTS installed on a Dell PowerEdge R610. The server has a Network Port dedicated to management through DRAC6 and four Network Ports. I would like to set up KVM and run a handful of virtual machines. What are my options as far as getting the most out of the four network ports that I have?

My original goal was to set up KVM bridges with bonding to fully utilize all four ports. I originally set up static IP's of: 

192.168.0.111 on eno1
192.168.0.112 on eno2
192.168.0.113 on eno3
192.168.0.114 on eno4

Then I thought maybe I could bridge the connections and set up bonding to take care of a connection if it was to go down so I set up bonding as follows:

bond0
192.168.0.111 on eno1 and eno3

bond1
192.168.0.112 on eno2 and eno4

Is this the best configuration to take advantage of KVM and all four network ports?

Now my /etc/network/interfaces file looks like this for both Bridging and Bonding on the setup above. Problem is when I SSH into the server on 192.168.0.111 I get disconnected a lot because of a broken pipe. Is there something not correct in my setup?

Thank you so much in advance!!


-----------------------------
/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback



# Create the bond0 Interface config and enslave eno1 and eno3 to it
auto bond0
iface bond0 inet manual
bond-miimon 100
bond-lacp-rate 1
post-up ifenslave bond0 eno1 eno3
pre-down ifenslave -d bond0 eno1 eno3
bond-slaves none
bond-mode 4
bond-lacp-rate fast
bond-miimon 100
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1
bond-mode active-backup

# Bond Master bond0
auto eno1
iface eno1 inet manual
bond-master bond0
bond-primary eno1

# Bond Master bond0
auto eno3
iface eno3 inet manual
bond-master bond0


# Create the bond0 Interface config and enslave eno1 and eno3 to it
auto bond1
iface bond1 inet manual
bond-miimon 100
bond-lacp-rate 1
post-up ifenslave bond1 eno2 eno4
pre-down ifenslave -d bond1 eno2 eno4
bond-slaves none
bond-mode 4
bond-lacp-rate fast
bond-miimon 100
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1
bond-mode active-backup

# Bond Master bond2
auto eno2
iface eno2 inet manual
bond-master bond1
bond-primary eno2

# Bond Master bond4
auto eno4
iface eno4 inet manual
bond-master bond1






#---------NETWORK 1 - eno1 --------------

# The primary network interface
#auto eno1
#iface eno1 inet static
# address 192.168.0.111
# broadcast 192.168.0.255
# netmask 255.255.255.0
# gateway 192.168.0.1
# dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

auto br1
iface br1 inet static
address 192.168.0.111
network 192.168.0.0
broadcast 192.168.0.255
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

bridge_ports bond0
bridge_stp off
bridge_fd 9
bridge_hello 2
bridge_maxage 12




#————NETWORK 2 - eno2 --------------
# The Second network interface
#auto eno2
#iface eno2 inet static
# address 192.168.0.112
# broadcast 192.168.0.255
# netmask 255.255.255.0
# gateway 192.168.0.1
# dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

auto br2
iface br2 inet static
address 192.168.0.112
network 192.168.0.0
broadcast 192.168.0.255
netmask 255.255.255.0
# gateway 192.168.0.1
dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

bridge_ports bond1
bridge_stp off
bridge_fd 9
bridge_hello 2
bridge_maxage 12




#---------NETWORK 3 - eno3 --------------
# The Third network interface
#auto eno3
#iface eno3 inet static
# address 192.168.0.113
# broadcast 192.168.0.255
# netmask 255.255.255.0
# gateway 192.168.0.1
# dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

#auto br3
#iface br3 inet static
# address 192.168.0.113
# network 192.168.0.0
# broadcast 192.168.0.255
# netmask 255.255.255.0
## gateway 192.168.0.1
# dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

# bridge_ports bond0
# bridge_stp off
# bridge_fd 9
# bridge_hello 2
# bridge_maxage 12





#---------NETWORK 4 - eno4 --------------
# The Fourth network interface
#auto eno4
#iface eno4 inet static
# address 192.168.0.114
# broadcast 192.168.0.255
# netmask 255.255.255.0
# gateway 192.168.0.1
# dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

#auto br4
#iface br4 inet static
# address 192.168.0.114
# network 192.168.0.0
# broadcast 192.168.0.255
# netmask 255.255.255.0
## gateway 192.168.0.1
# dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

# bridge_ports bond1
# bridge_stp off
# bridge_fd 9
# bridge_hello 2
# bridge_maxage 12

-----------------------------


Regards,
Anthony

---

### Post by tremorsfsu on 2017-01-16
I made a few changes and it looks like this configuration is working now to provide bridging on all four network ports and bonding to bond0 for eno1 and eno3 and bond1 eno2 and eno4. 

I'm no longer having any issues with being disconnected and I've tested unplugging eno1 and eno3 and bond0 stays active on the IP 192.168.0.111 and unplugging eno2 and eno4 and bond1 stays active for IP 192.168.0.112. The thing that I don't understand is that 192.168.0.112 still pings as long as ANY cable is plugged in. It's almost like the failover for that IP is attached to all four interfaces which I am trying to figure out why.

The changes that I made to my initial configuration was:
1. I had two places that I set bond-lacp-rate which I commented out completely
2. I had two bond-modes defined which I changed to active-backup


Here's the updated file:
[B]/etc/network/interfaces
[/B]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback



# Create the bond0 Interface config and enslave eno1 and eno3 to it
auto bond0
iface bond0 inet manual
bond-miimon 100
#bond-lacp-rate fast
post-up ifenslave bond0 eno1 eno3
pre-down ifenslave -d bond0 eno1 eno3
bond-slaves none
bond-miimon 100
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1
bond-mode active-backup


# Bond Master bond0
auto eno1
iface eno1 inet manual
bond-master bond0
bond-primary eno1

# Bond Master bond0
auto eno3
iface eno3 inet manual
bond-master bond0


# Create the bond1 Interface config and enslave eno2 and eno4 to it
auto bond1
iface bond1 inet manual
bond-miimon 100
#bond-lacp-rate fast
post-up ifenslave bond1 eno2 eno4
pre-down ifenslave -d bond1 eno2 eno4
bond-slaves none
bond-miimon 100
bond-downdelay 0
bond-updelay 0
bond-xmit_hash_policy 1
bond-mode active-backup


# Bond Master bond1
auto eno2
iface eno2 inet manual
bond-master bond1
bond-primary eno2

# Bond Master bond1
auto eno4
iface eno4 inet manual
bond-master bond1



#---------NETWORK 1 - eno1 --------------

# The primary network interface
#auto eno1
#iface eno1 inet static
# address 192.168.0.111
# broadcast 192.168.0.255
# netmask 255.255.255.0
# gateway 192.168.0.1
# dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

auto br1
iface br1 inet static
address 192.168.0.111
network 192.168.0.0
broadcast 192.168.0.255
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

bridge_ports bond0
bridge_stp off
bridge_fd 9
bridge_hello 2
bridge_maxage 12




#---------NETWORK 2 - eno2 --------------

# The Second network interface
#auto eno2
#iface eno2 inet static
# address 192.168.0.112
# broadcast 192.168.0.255
# netmask 255.255.255.0
# gateway 192.168.0.1
# dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

auto br2
iface br2 inet static
address 192.168.0.112
network 192.168.0.0
broadcast 192.168.0.255
netmask 255.255.255.0
# gateway 192.168.0.1
dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

bridge_ports bond1
bridge_stp off
bridge_fd 9
bridge_hello 2
bridge_maxage 12




#---------NETWORK 3 - eno3 --------------
# The Third network interface
#auto eno3
#iface eno3 inet static
# address 192.168.0.113
# broadcast 192.168.0.255
# netmask 255.255.255.0
# gateway 192.168.0.1
# dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

#auto br3
#iface br3 inet static
# address 192.168.0.113
# network 192.168.0.0
# broadcast 192.168.0.255
# netmask 255.255.255.0
## gateway 192.168.0.1
# dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

# bridge_ports bond0
# bridge_stp off
# bridge_fd 9
# bridge_hello 2
# bridge_maxage 12





#---------NETWORK 4 - eno4 --------------
# The Fourth network interface
#auto eno4
#iface eno4 inet static
# address 192.168.0.114
# broadcast 192.168.0.255
# netmask 255.255.255.0
# gateway 192.168.0.1
# dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

#auto br4
#iface br4 inet static
# address 192.168.0.114
# network 192.168.0.0
# broadcast 192.168.0.255
# netmask 255.255.255.0
## gateway 192.168.0.1
# dns-nameservers 8.8.8.8 192.168.0.1 8.8.8.8

# bridge_ports bond1
# bridge_stp off
# bridge_fd 9
# bridge_hello 2
# bridge_maxage 12

---

