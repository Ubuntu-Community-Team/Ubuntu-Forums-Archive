---
title: "gigabit Realtek 8110S driver install"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by matt91 on 2007-06-09
i have been trying to get full speed from my ubuntu server for months. I have now got very close by trying to install the realtek drivers from [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")  (the 2.6.x version) and tried to follow the readme, the first command being 'make clean modules' and this is what i get:
> root@server:~/gigabit# make clean moduled
make -C src/ clean
make[1]: Entering directory `/root/gigabit/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions
make[1]: Leaving directory `/root/gigabit/src'
make: *** No rule to make target `moduled'.  Stop.
root@server:~/gigabit# make clean modules
make -C src/ clean
make[1]: Entering directory `/root/gigabit/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions
make[1]: Leaving directory `/root/gigabit/src'
make -C src/ modules
make[1]: Entering directory `/root/gigabit/src'
make -C /lib/modules/2.6.20-16-server/build SUBDIRS=/root/gigabit/src modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.20-16-server/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/root/gigabit/src'
make: *** [modules] Error 2
root@server:~/gigabit#


all i want is to get full speed from my gigabit setup which includes cat6 cables and gigabit swich. i currently get around 10MB/s

thanks, Matt

---

### Post by chili555 on 2007-06-09
Do you have *build-essential* and *linux-headers-`uname -r`* installed? You can *sudo apt-get install* them.

---

### Post by matt91 on 2007-06-10
thanks for that, i had to upgrade the system to the latest kernel first as the packages didnt exist for the one installed.

---

### Post by matt91 on 2007-06-10
the driver has been installed accordingly with the readme but it isnt any faster,

ifconfig -a gives:
> 
root@server:~# ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:0C:76:B3:8F:34
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:feb3:8f34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:171698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:239171189 (228.0 MiB)  TX bytes:11131481 (10.6 MiB)
          Interrupt:16 Base address:0x6f00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6248 (6.1 KiB)  TX bytes:6248 (6.1 KiB)



and lsmod | grep r8169 gives:
> root@server:~# lsmod | grep r8169
r8169                  32392  0


i have forced the link status in many combinations and restarted networking with no difference.

---

### Post by chili555 on 2007-06-10
> inet addr:192.168.1.1 Bcast:192.168.1.255 Mask:255.255.255.0This is a little unusual, isn't it? Generally 192.168.1.1 is the gateway. Or is *this* the gateway for other computers?

Does *sudo ethtool eth1* tell us something interesting?

---

### Post by matt91 on 2007-06-10
ah, got something with ethtool eth1:
> root@server:~# ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes


so it is using 10Mb/s although i want it at 1000Mb/s. in the driver readme there is this:
> 	2. Force the link status by using ethtool.
		a. Insert the driver first.
		b. Make sure that ethtool exists in /sbin.
		c. Force the link status as the following command.

			# ethtool -s ethX speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

			,where
				SPEED_MODE	= 1000	for 1000Mbps
						= 100	for 100Mbps
						= 10	for 10Mbps
				DUPLEX_MODE	= half	for half-duplex
						= full	for full-duplex
				NWAY_OPTION	= off	for auto-negotiation off
						= on	for auto-negotiation on

whatever i do with this ethtool eth1 stays the same :confused:

---

### Post by matt91 on 2007-06-10
i have got a linksys EG1064 which i could put into the server, would this be any better?

---

### Post by chili555 on 2007-06-10
> i have got a linksys EG1064 which i could put into the server, would this be any better?Not necessarily, but let's check a few things first. What is on the other end of the switch? Is it capable of gigabit speeds?

Second, does ethtool take commands without complaint? When you command it to 1000Mb/s, are you turning auto-negotiation off?

---

### Post by matt91 on 2007-06-11
network cards on the other side of the switch are gigabit capapale (confirms this in status windows) and connected to the switch (Netgear GS605).

i have done:
[LIST]
[*]ethtool -s eth1 speed 1000 duplex full autoneg off
[*]ethtool -s eth1 speed 1000 duplex full autoneg on
[*]ethtool -s eth1 speed 1000 duplex half autoneg on
[*]ethtool -s eth1 speed 1000 duplex half autoneg off
[/LIST]
> root@server:~# ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes


I have been able to turn to 100Mb/s by doing:
> root@server:~# ethtool -s eth1 speed 100 duplex full autoneg off
root@server:~# ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

... yet when i then try 1000 again it goes back to 10:(

100 is beter than 10 but still, 1000 would be nice since i have all the hardware for it :)

---

