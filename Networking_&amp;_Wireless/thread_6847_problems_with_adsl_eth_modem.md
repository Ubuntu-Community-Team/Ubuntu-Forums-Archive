---
title: "problems with adsl eth modem"
date: 2004-12-02
forum: Networking &amp; Wireless
---

### Post by iDleR on 2004-12-02
After setting pppoeconf, my computer is not able to resolve hosts. I don't know why.

Here the "route -n"

```

root@dierrehome:/home/dierre # route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.1   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

the dsl.provider.conf

```

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0


user "**********@tin.it"

```

and plog

```

Nov 29 12:51:34 localhost pppd[5333]: PAP authentication succeeded
Nov 29 12:51:34 localhost pppd[5333]: peer from calling number 00:05:5E:B3:49:CF authorized
Nov 29 12:51:34 localhost pppd[5333]: not replacing default route to eth0 [192.168.1.1]
Nov 29 12:51:34 localhost pppd[5333]: Cannot determine ethernet address for proxy ARP
Nov 29 12:51:34 localhost pppd[5333]: local  IP address 80.117.19.141
Nov 29 12:51:34 localhost pppd[5333]: remote IP address 192.168.100.1
Nov 29 12:51:34 localhost pppd[5333]: primary   DNS address 217.141.254.206
Nov 29 12:51:34 localhost pppd[5333]: secondary DNS address 151.99.125.1

```

DNS addresses are not my DNS Privider but I think there are some problem with ethernet setting..but i didn't touch anything.

---

### Post by iDleR on 2004-12-02
pls help me :(

---

### Post by arctic on 2004-12-02
open a terminal and type:

*sudo gedit /etc/sysctl.conf*

now add the following line: 

*net.ipv4.tcp_window_scaling=0*

save the file. now type in the terminal
*sudo gedit /etc/modprobe.d/aliases*

edit the following line from
*alias net-pf-10*
to
*alias net-pf-10 off*
or
*alias net-pf off*

if that does not help, type in the terminal

sudo apt-get install pump
sudo apt-get install resolvconf
sudo apt-get install dnsmasq

i hope this solves your problem.

---

### Post by iDleR on 2004-12-18
Sorry if I'm late but i found the problem...when I've installed Ubuntu i accepted to configure DHCP network... :|
I'm a newbie, but now it's ok...tnx :D

---

### Post by kahping on 2004-12-19
idler, i have the exact same problem. could u tell me how u resolved the issue?

thanks in advance

---

### Post by iDleR on 2004-12-23
[QUOTE=kahping]idler, i have the exact same problem. could u tell me how u resolved the issue?

thanks in advance[/QUOTE]


ifconfig eth0 down

i've red the documentation but i didn't find which conf file i have to edit to obtain a right solution

---

### Post by Averatec5400 on 2004-12-23
[QUOTE=iDleR]ifconfig eth0 down

i've red the documentation but i didn't find which conf file i have to edit to obtain a right solution[/QUOTE]
 use the gnome network configuration tool, go to eth0 and take it off of DHCP, or set the nameservers manually.

---

### Post by iDleR on 2004-12-24
[QUOTE=Averatec5400]use the gnome network configuration tool, go to eth0 and take it off of DHCP, or set the nameservers manually.[/QUOTE]
 it ask me the system admin password, I use sudo passwd to set root password but i can't have an access in everything is about gnome sys-config

---

### Post by alrom9820 on 2007-05-15
> **iDleR said:**
> ifconfig eth0 down

i've red the documentation but i didn't find which conf file i have to edit to obtain a right solution


[build insects blood pressure physics Britney Spears](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

