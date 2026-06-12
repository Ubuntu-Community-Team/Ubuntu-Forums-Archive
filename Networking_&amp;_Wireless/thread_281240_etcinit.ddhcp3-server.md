---
title: "/etc/init.d/dhcp3-server"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by phil79 on 2006-10-20
Please can someone explain this. The concept I understand. The implementation I do not.

I have my ubuntu PC that I want to serve IP addreses to a thin client and a couple of other PC's - I have turned off the dhcp on my adsl/modem/router.

I have a script in /etc/init.d/dhcp3-server that seems to call /etc/dhcp3/dhcp.conf

default-lease-time 6048;
max-lease-time 604800;

allow booting;
allow bootp;


# The next paragraph needs to be modified to fit your case

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.254;
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.168.1.255;

# the gateway address which can be different
# (access to the internet for instance)

  option routers 192.168.1.1;

# indicate the dns you want to use
 option domain-name-servers 192.168.1.99;
}


# This is address of Ubuntu box.....
host ubuntu {

#  ip address
  fixed-address 192.168.1.99;

#  hardware address
  hardware ethernet 00:11:DB:44:2B:2C;

  option routers 192.168.1.1;

}


# This is address of laptop.....
host laptop {

#  ip address
  fixed-address 192.168.1.98;

#  hardware address
  hardware ethernet 00:EE:35:62:D7:C7;

  option routers 192.168.1.1;

}

host tftpserver {
# tftp server ip address
  fixed-address 192.168.1.99;

# tftp server hardware address
  hardware ethernet 00:EE:35:62:D7:C7;
}



# This is address of client

host tftpclient {
# tftp client hardware address

hardware ethernet  00:0F:EA:5C:81:39;
fixed-address 192.168.1.100;
filename "/var/lib/tftpboot/ltsp/pxelinux.0";
next-server 192.168.1.99;
 }



BUT 

I also have something:

ubuntu:/etc/default> more dhcp3-server
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"



The first script does not work because it is not associated with eth0 ???



I do not undestand the interaction between the two......


Am going insane.

---

