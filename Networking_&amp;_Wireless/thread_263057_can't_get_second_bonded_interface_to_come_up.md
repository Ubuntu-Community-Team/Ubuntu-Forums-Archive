---
title: "can't get second bonded interface to come up"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by empathy0020 on 2006-09-22
Hello!! I check these forums all the time when i have questions and it is always very helpful. So before i start, i want to say "thank you" to everyone who posts here. You have all made my life easier.

OK down to business.

I am trying to get two bonded interfaces working on one machine. Call them bond0 and bond1. bond0 comes up fine, but bond1 fails.

here are the steps i have taken to get this configured:
1. add bonded interfaces to /etc/network/interfaces (and commented out all other eth[x] configs)

 auto bond0
 iface bond0 inet static
        address 10.x.24.24
        netmask 255.255.255.0
        network 10.x.24.0
        broadcast 10.x.24.255
        gateway 10.x.24.1
        dns-nameservers 10.x.24.14 10.x.24.15
        up ifenslave bond0 eth0 eth3
        down ifenslave -d bond0 eth0 eth3

 auto bond1
 iface bond1 inet static
        address 10.x.152.24
        netmask 255.255.255.0
        network 10.x.152.0
        broadcast 10.x.152.255
        up ifenslave bond1 eth1 eth2
        down ifenslave -d bond1 eth1 eth2


2. loaded bonding by executing: #modprobe bonding
3. added bonding to /etc/modules
4. added the following lines to /etc/modprobe.d/aliases

     alias bond0 bonding
     alias bond1 bonding
     options bonding mode=0 miimon=100

when i restart networking bond0 comes up fine. However when bond1 tries to come up i get the following errors:

  SIOCSIFADDR: No such device
  bond1: ERROR while getting interface flags: No such device
  SIOCSIFNETMASK: No such device
  SIOCSIFBRDADDR: No such device
  bond1: ERROR while getting interface flags: No such device
  bond1: ERROR while getting interface flags: No such device
  Failed to bring up bond1.

I assume i have to do something to extra since i want two bonded interfaces. However, i can't figure out what.

Thanks!!

---

### Post by empathy0020 on 2006-09-22
I got it!!

have to add max_bonds=# in the options line in /etc/modprobe.d/aliases. So lines added to this file should look like this.

alias bond0 bonding
alias bond1 bonding
options bonding mode=0 miimon=100 max_bonds=2

---

