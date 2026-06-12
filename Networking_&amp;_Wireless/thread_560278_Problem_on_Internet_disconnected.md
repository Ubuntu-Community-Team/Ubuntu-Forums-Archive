---
title: "Problem on Internet disconnected"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-09-26
Hi folks,


Ubuntu 7.04 server amd64
VMware 
router IP address - 192.168.0.10


I'm building a virtual machine with Ubuntu as Host OS and playing round on following packages;
- denyhosts
- sshd
- iptables

with following files edited;

1)
/etc/hosts.allow```

sshd: 127.0.0.1

# Domain
sshd: .mydomain.com

# myISP from home
sshd: *.myISP

```

/etc/hosts.deny```

sshd:ALL EXCEPT localhost \
: spawn /bin/echo `/bin/date` access denied for %a %h>>/var/log/sshd.log

ALL: ALL

```

$ sudo /etc/init.d/denyhosts start


2)
/etc/ssh/sshd_config 
uncomment following line and change "no" to "yes"
# PasswordAuthentication yes

uncomment following line and change "0.0.0.0" to "192.168.0.10"
# ListenAddress 0.0.0.0

&#8230;where 192.168.0.10 is the IP of the management network interface (server's router IP address) so that ssh daemon will not listen on the NICs dedicated to the VMs. 

Then run;
$ sudo /etc/init.d/ssh restart


3)
Copy  following file on /etc/rc.local```

#
# INPUT
#

# allow all incoming traffic from the management interface NIC
# as long as it is a part of an established connection
iptables -I INPUT 1 -j ACCEPT -d MGMT_NIC_IP -m state --state RELATED,ESTABLISHED

# allow all ssh traffic to the management interface NIC
iptables -I INPUT 2 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 22

# allow all VMware MUI HTTP traffic to the management interface NIC
iptables -I INPUT 3 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 8222

# allow all VMware MUI HTTPS traffic to the management interface NIC
iptables -I INPUT 4 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 8333

# allow all VMware Authorization Daemon traffic to the management interface NIC
iptables -I INPUT 5 -j ACCEPT -p TCP -d MGMT_NIC_IP --destination-port 902

# reject all other traffic to the management interface NIC
iptables -I INPUT 6 -j REJECT -d MGMT_NIC_IP --reject-with icmp-port-unreachable


#
# OUTPUT
#

# allow all outgoing traffic from the management interface NIC
# if it is a part of an established connection
iptables -I OUTPUT 1 -j ACCEPT -s MGMT_NIC_IP -m state --state RELATED,ESTABLISHED

# allow all DNS queries from the management interface NIC
iptables -I OUTPUT 2 -j ACCEPT -s MGMT_NIC_IP -p UDP --destination-port 53

# reject all other traffic from localhost
iptables -I OUTPUT 3 -j REJECT -s 127.0.0.1 --reject-with icmp-port-unreachable

# reject all other traffic from the management interface NIC
iptables -I OUTPUT 4 -j REJECT -s MGMT_NIC_IP --reject-with icmp-port-unreachable

```

and change "MGMT_NIC_IP" to "192.168.0.10"

Then run;
$ sudo /etc/init.d/rc.local start


Afterwards I can't browse Internet.

Then I run;

$ sudo /etc/init.d/denyhosts stop
$ sudo /etc/init.d/rc.local stop

and revert all files to their original states.  Still I can't browse Internet.


Reboot PC.  Internet connection works again.


My questions are;

a)
Whether I have to run;```

sudo iptables -F

```

just run;```

sudo /etc/rc.local stop

```
is not sufficient.


b)
Is changing "MGMT_NIC_IP" to "192.168.0.10" CORRECT ?


c)
If I have only ONE NIC, I don't need to uncomment following line and changeing "0.0.0.0" to "192.168.0.10"
# ListenAddress 0.0.0.0

???


d)
Whether I need adding follow to bottom of  /etc/hosts.allow```

ALL:CLIENT_HOSTNAME_1, CLIENT_HOSTNAME_2, CLIENT_IP_ADDRESS_1,
*.CLIENT.DOMAIN.COM

```
If for local network, whether adding IP addresses of the workstation as "CLIENT_HOSTNAME_1"

???


e)
Any advice on the above files? What makes Internet connection not working?


TIA


B.R.
satimis

---

