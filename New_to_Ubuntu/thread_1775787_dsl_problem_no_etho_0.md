---
title: "dsl problem no etho 0"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by harvindercs on 2011-06-05
[LIST=1]
[*]i use a DSL connection
[*]when i installed Ubuntu 11.04 it was fine and it showed 2 networks one was eth0 and other was DSL-1(which i created using network manager->dsl->add->then by filling user name and password)
[*]then one day i tried pppoeconf after that i was not able to view my dsl-1 connection and etho-0 on network manager indicator,
[*]then i googled and i changed /etc/network/interfaces
[*]now i see only one connection that is DSL-1 and my firefox do not open yahoo home page and several other website(which may be due to ipv6 conflict but i disabled it and still it has same problem it says loading.. loading and nothing comes up)
[*]anyone having solution Please come up :(
[/LIST]

---

### Post by jtarin on 2011-06-05
In a terminal issue the command "sudo pon dsl-provider" and see if you connect. Then the command "sudo poff dsl-provider" will disconnect.

---

### Post by harvindercs on 2011-06-05
> **jtarin said:**
> In a terminal issue the command "sudo pon dsl-provider" and see if you connect. Then the command "sudo poff dsl-provider" will disconnect.

i can connect, it works but as i said some websites wont load, including yahoo and eth0 is not shown by network-manager 
my configuration of /etc/network/interfaces is 
```
 auto lo
iface lo inet loopback

``` 

and this command sudo pon dsl-provider it is used in pppoeconf that i dont want to use agian

---

### Post by harvindercs on 2012-08-21
i solved it, it was MTU problem

---

### Post by Bashing-om on 2012-08-21
outstanding! ... on same note, did you purge the old pppoeconf ?
```
sudo apt-get --purge remove pppoeconf
```
This is to prevent any future conflicts with any remaining config files.

[INDENT]regards <==BDQ
[/INDENT]

---

### Post by harvindercs on 2012-08-22
> **Bashing-om said:**
> outstanding! ... on same note, did you purge the old pppoeconf ?
```
sudo apt-get --purge remove pppoeconf
```
This is to prevent any future conflicts with any remaining config files.

[INDENT]regards <==BDQ
[/INDENT]

thanks bud! i will purge it

---

