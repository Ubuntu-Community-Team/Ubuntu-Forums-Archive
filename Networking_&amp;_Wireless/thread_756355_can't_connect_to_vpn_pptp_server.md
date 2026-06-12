---
title: "can't connect to vpn pptp server"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by glederfein on 2008-04-15
Hi all!
I've been trying recently to connect to a VPN PPTP server using the "network-manager-pptp" package on Feisty. I found some instructions on how to connect to the specific server [here]("http://vpn.technion.ac.il/") however they are Windows specific (of course).
I tried entering the ip given (132.68.254.109) in the "gateway" field and tried playing around with the "authentication/compression/encryption" options however I always get "VPN connection failed"!

Does anyone have some sort of solution for me?

Thanks in advance,
glederfein.

---

### Post by torry_loon on 2008-04-15
I could never get a VPN connection to work from the GUI. This is how I connect to my VPN.

Edit /etc/hosts - add the entries for the servers to connect to
e.g.

```
192.168.1.2   server1
192.168.1.3   server2
```

Install pptp 

```
apt-get install pptp-linux
```

Make /etc/ppp/options look like this: 

```
lock
debug
mtu 1000
nobsdcomp
nodeflate
noaccomp
nopcomp
novj
defaultroute
name *USERNAME*
```

Make /etc/ppp/pap-secrets look like this: 

```
*USERNAME* *IP ADDRESS* *PASSWORD*
```

e.g.
```
admin 91.189.94.158 mypassword
```


Make sure /etc/ppp/pap-secrets is not world readable 


Connecting

Issue the following commands as root in a terminal:

```
pptp *IP ADDRESS* debug name* USERNAME* remotename *IP ADDRESS* noipdefault

route add -net 192.168.1.0/24 dev ppp0
```

---

### Post by glederfein on 2008-04-16
Hey torry_loon!
Thanks for the post!
However I have a few questions:
By "username" you mean the username for the vpn connection?
By "ip address" you mean the ip of the vpn server?
And at the routing part what should I put instead of "192.168.1.0/24"? Is that my internal ip address and what is that number after the "/"?
Last but not least: Is there a way to enter the password for the connection in the terminal (my password changes every time I connect!)

---

### Post by glederfein on 2008-04-17
Can some one please help me with this??
I tried following torry_loon's directions however after the "pptp" command nothing happened and it did not connect to the server!
](*,)

Any suggestion would be helpful...

---

### Post by torry_loon on 2008-04-18
Hi glederfein,

USERNAME is the username used to connect to the VPN server. Replace IP ADDRESS with the external IP address of the VPN server.

The 192.168.1.0 is the internal subnet of the network. Replace this with the subnet of the network you are trying to access. For example if the DHCP servers on the network assigns IP addresses in the range 192.168.2.2-192.168.2.255, then the subnet would be 192.168.2.0

The /24 indicates that the first 24 bits of the IP address are used as the network address (same as 255.255.255.0).

---

