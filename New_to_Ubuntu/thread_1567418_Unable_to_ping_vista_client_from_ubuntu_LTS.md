---
title: "Unable to ping vista client from ubuntu LTS"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by punjabdapunk on 2010-09-03
Hi,
I'm a newb... just installed ubuntu and am enjoying ubuntu. I have a ubuntu server, a vista client and a netgear router all of which is cabled...

I've been trying to get samba to work but with little success. I've started diagnosing the problem and noticed that I can't ping the vista client on the network from ubuntu. I can ping ubuntu from vista though.

When I issue 'ping vistaclient' on ubuntu the command hangs until I hit ctrl-c. The command reports 100% packet loss.

I've looked at everything I know and have numerous tips picked up via the web but I'm at a loss.

Could someone point me in the right direction.

Once I get the ping sorted I'll work on getting samba working.

Later

PunjabDaPunk

---

### Post by davidmohammed on 2010-09-03
in vista, use the command window and type

ipconfig

this will display the IP address of vista.

in ubuntu type

ping <IP address>

e.g.

ping 192.9.168.10

---

### Post by punjabdapunk on 2010-09-04
Hi davidmohammed,
Yeh, I've tried that too. I've updated my host file to map the vista's hostname to its IP address. Both IP address and hostname produce the same result.

That is the ping command hangs and I have to hit ctrl-c. It shows that there was 100% packet loss.

I'm beginning to believe that ubuntu doesn't recognise an internal network IP address e.g. 192.168.0.xxx and is attempting to resolve it via my ISP's DNS.

Does that make sense?

I have modified /etc/network/interfaces as follows:

   Static IP address: 192.168.0.100
  Netmask:  255.255.255.0
  Network :  192.168.0.0
  Broadcast: 192.168.0.255
  Gateway: 192.168.0.1
  And then restarted networking... is that right?

Later

---

### Post by CharlesA on 2010-09-04
That looks right. if a host is listed in the hosts file, the machine will skip DNS look up.

Make sure that the Vista machine is set to allow ICMP packets (pings, etc).

---

### Post by punjabdapunk on 2010-09-05
Thanks CharlesA,
Vista is accepting pings. I've tested through my router and vista responds to pings.

I still have no luck pinging the vista client from ubuntu though.

Any further suggestions?

I'll keep looking too...

Thanks for your suggestion so far.


Later

---

