---
title: "P4i45GV onboard lan card is too slow"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by yubyungho on 2010-02-25
this is too slow I upgrade ubuntu 9.04 to 9.10 so I had to download 300mb? 
 
it tries 10 hours to download file and DID download SOME but failed at the end
 
I tried another server and it does same slow internet
 
and also firfox's loading is slow to
 
so howto see config of my lan card and change it?

---

### Post by cariboo on 2010-02-25
Try ethtool, I think it's installed by default. Oepn a terminal and type:

```
sudo ethtool eth0
```

You should get something that looks like this:

```
sudo ethtool eth0
[sudo] password for me: 
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes
```

The above is the default settings for my motherboard. Have a look at the help file by typing:

```
ethtool -h
```

---

### Post by yubyungho on 2010-02-26
```

Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes


```

I got this message 

is your mainboard P4i45gv same as me?

---

### Post by Peter09 on 2010-02-26
This sounds more like a router/isp problem than the LAN card. How are you connected to the Internet?

---

### Post by yubyungho on 2010-02-26
my linux machine is connected through router

only difference between ubuntu pc and windows pc is that I am using port fowarding 

(port 22 for ssh only)

but I dont think this is problem though.

this is SLOOOOOOOOOW I am getting frsutrated....

---

### Post by yubyungho on 2010-02-27
I have done many things to fix this problem

I am curious it ACTUALLY WORKED BEFORE

it worked as ssh server very well with good transfering speed(sftp)

but installing ubuntu again it went to nut.

takes forever to apt-get update install

never have to mention speed of firefox 

and ssh-server

---

