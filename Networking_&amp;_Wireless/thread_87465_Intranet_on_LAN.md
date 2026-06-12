---
title: "Intranet on LAN"
date: 2005-11-08
forum: Networking &amp; Wireless
---

### Post by rodent43 on 2005-11-08
Hi,

I have 2 net cards in my Ubuntu 5.04 box...one is set up for the 2mb adsl in the office with a specific IP and dns etc.

the other is on the lan by a specified ip also.

we have an intranet server sitting on a dmz on the firewall and i used to specify the gateway on the lan card to the firewall ip and it would route the request to the intranet server.

so when browsing with firefox i could type blah.intranet and the dns server would rooute me to an address on the dmz and in turn the firewall would route local traffic.

now i have the adsl card in to, i cant browse to the intranet on the local lan.

i am assuming this is because the default gateway is now the router for the adsl card.

is there a way i can set up so that i can still get to the intranet via lan rather than wan?

thx in advance

---

### Post by souki on 2005-11-08
you can check the routing rules with
```
route -n
```

---

### Post by rodent43 on 2005-11-08
```

Destination            		Gateway         Genmask         Flags Metric Ref    Use Iface
<Wan Address>  			0.0.0.0         255.255.255.248 U     0      0        0 eth1
<Lan Address (num.num.0.0)      0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0       			<Wan Address>	0.0.0.0         UG    0      0        0 eth1
0.0.0.0         		<Firewall IP>   0.0.0.0         UG    0      0        0 eth0

```


This is what route -n returns...

is that enough info?

thx for the reply

---

### Post by rodent43 on 2005-11-08
anyone pls help me...

i am trying to make ubuntu an alternative to windows here :-)

i really dont want to go back to a windows PC :'(

---

### Post by mips on 2005-11-09
rodent43,

I would suggest running Firestarter, can be installed from Synaptic. Firestarter allows for internet connection sharing. From there you can configure the one Ethernet card for Internet access and the other for your local LAN, where it will assign DHCP, DNS etc to the clients on the local LAN.

The documentation on the website  [http://www.fs-security.com/](http://www.fs-security.com/)  is pretty good. I used it to setup the same scenario as yours except I do not have a DMZ.

[http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by rodent43 on 2005-11-09
thx mips, i will look at that now :)

---

### Post by rodent43 on 2005-11-09
ok i am going from bad to worse

it must be the dns entries...

the adsl has 2 and the lan has 1...depending on the order in the network settings determines what i can and cant access

put the lan one to the top and i have no internet put the wans to the top and i have no local.

and now i cant even browse the smb shares i had setup from the windows servers on the network...xfe just crashes when i try to access the mount point.

its my fault, all was working ok with just the lan card in and using a proxy except Gaim, it wouldnt connect.

thx for the help peeps, it is much appreciated.

---

