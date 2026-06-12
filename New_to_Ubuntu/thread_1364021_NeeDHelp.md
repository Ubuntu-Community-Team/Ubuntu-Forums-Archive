---
title: "NeeDHelp"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by King_Dud on 2009-12-25
hey i need help with driftnet can any 1 please give me tutorial:confused:
i am using ubuntu v9.10
thanks

---

### Post by King_Dud on 2009-12-25
ok i have found out how to use it on  my self but can u please tell me how to use it on other one?

---

### Post by King_Dud on 2009-12-25
hi. i use this command 

sudo driftnet -i 192.198.5.23
it doesnt work

but when i try this:

sudo driftnet -i eth0 it works y is that?>

---

### Post by King_Dud on 2009-12-25
hi.
i am new to ubuntu.
i just wanted to know how to use driftnet and ettercap.

well i know how to use driftnet on my self. i just give this command.

```
sudo driftnet -i eth0
```but when i test on my 2nd PC with this code:

```
sudo driftnet -i 192.13.21.4
```i get this.: 

```
driftnet: pcap_open_live: SIOCGIFHWADDR: No such device
```_**ETTERCAP.**_

when i use ettercap i give this command.

```
sudo ettercap -C -M arp:remote /192.13.21.5/ /192.13.21.4/
```even if i did it right i dont get password of any thing. need help with this.

when i give the -T interface sometimes it does not work.

---

### Post by aliayaz on 2009-12-25
Ok Driftnet you should simply do this

```
 driftnet -i eth0 
```

for ettercap

```
 ettercap -Tqp -M ARP // // -i eth0
```

it's how I do both of them and so far they work pretty well I'll explain them to you.

in driftnet you can't choose an IP it simply takes it from your network.

Ettercap however, you CAN set an IP.. but you don't have to I for example do it on the whole network


-i = Interface. To know which interface you have to use run this command in terminal


iwconfig


it shows you all the network devices with i.e wireless or no wireless capabilities I for example use wireless so if I need to know what device it is I use iwconfig. k good luck.

---

### Post by sandyd on 2009-12-25
> **aliayaz said:**
> Ok Driftnet you should simply do this

```
 driftnet -i eth0 
```for ettercap

```
 ettercap -Tqp -M ARP // // -i eth0
```it's how I do both of them and so far they work pretty well I'll explain them to you.

in driftnet you can't choose an IP it simply takes it from your network.

Ettercap however, you CAN set an IP.. but you don't have to I for example do it on the whole network


-i = Interface. To know which interface you have to use run this command in terminal


iwconfig


it shows you all the network devices with i.e wireless or no wireless capabilities I for example use wireless so if I need to know what device it is I use iwconfig. k good luck.
should be ifconfig

---

### Post by bapoumba on 2009-12-26
Threads merged.

---

