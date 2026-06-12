---
title: "[HOWTO?]create a network and share internetconnection between ubuntu and windows?"
date: 2005-10-05
forum: Networking &amp; Wireless
---

### Post by zoobooboozoo on 2005-10-05
Hello all.


I have to PCs at my house. and I'll refer to them like this:
1) PrimaryPC - my PC, with the linux, 2 netcards, the PPPOE internet connection
2) SecondryPC - the family PC, with windows xp pro, one netcard, and the printer.
* I have a LAN cable, connecting these two.

and I would like to connect between them this way:
1) Internet connection shared
2) printer shared

I have ubuntu latest *stable* realese, 5.04 on the primary PC.




any other info I should provide?

ths in advance

p.s.
Hope my post is good enough:(

---

### Post by zoobooboozoo on 2005-10-05
anyone?
If the post isn't good enough I'm VERY sorry, how can I make it bettER?:confused:

---

### Post by zoobooboozoo on 2005-10-07
Anyone?
this is really inmportant to me :(

---

### Post by Some_Bored_Dude on 2005-10-07
Hey Man!

It is possible. I'm currently setting that up now.

I have 2 eth's in my server, running ubuntu. eth0 is PPPoE, and eth1 is local, which shares the connection out to the pc's. However, this isnt the case yet as I'm still waiting for the ADSL to be connected. Hoping Monday. When its connected I'll get it going, and try and do up a howto for ya.

Have you got webmin installed? You should be able to setup a PPPoE connection (SO long as you installed pppoe with apt-get). I believe you need to set a route from say eth0 (pppoe) to eth1 (LAN), and make eth1 the gateway address for your internet connections. Give it a try. Once I get it going, I'll let you know. :D

---

### Post by zoobooboozoo on 2005-10-08
i already have the PPPoE connected.
yet I have no idea how to get the network works

---

### Post by Matchless on 2005-10-08
[QUOTE=Some_Bored_Dude]Hey Man!

It is possible. I'm currently setting that up now.

I have 2 eth's in my server, running ubuntu. eth0 is PPPoE, and eth1 is local, which shares the connection out to the pc's. However, this isnt the case yet as I'm still waiting for the ADSL to be connected. Hoping Monday. When its connected I'll get it going, and try and do up a howto for ya.

Have you got webmin installed? You should be able to setup a PPPoE connection (SO long as you installed pppoe with apt-get). I believe you need to set a route from say eth0 (pppoe) to eth1 (LAN), and make eth1 the gateway address for your internet connections. Give it a try. Once I get it going, I'll let you know. :D[/QUOTE]

Hi,
      Install Firestarter firewall on your ubuntu pc, follow the wizard to set up, it has built in internet connection sharing. I am using the same setup. Use Samba to share printer and files. You may have to specify DNS as well.
Good luck.

---

### Post by born_confused on 2005-10-08
Well I have a similar setup and I have it working.

I have a laptop with a wireless connection to a router. Laptop also contains an ethernet card.

So this is what I did. 

For clarification:

ath0(laptop) connects to net through router using static ip.
eth0 is my ethernet card on my laptop.
pccard is my ethernet card on my computer
I now have a crossover cable connected from computer to laptop.

I installed a dhcp server

sudo apt-get install dhcp3

then edited the dhcpd.conf in /etc/dhcp3/

like how specified in 

[http://ubuntuguide.org/#installdhcpserver](http://ubuntuguide.org/#installdhcpserver)

that site shows


# A slightly different configuration for an internal subnet.
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.200;
  option domain-name-servers 202.188.0.133, 202.188.1.5;
  option domain-name "tm.net.my";
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  default-lease-time 600;
  max-lease-time 7200;
}

but for the dhcp server my router is my wireless card, so I changed option routers from 192.168.0.1 to 192.168.1.2 which is my wireless card ip

I also changed the domain-name-servers to show what was on my /etc/resolv.conf 

and final the 3rd section is 0 for this subnet and 1 for my wireless card I changed the netmask to 255.255.0.0 and not 255.255.255.0 as specified above

so in my network settings for eth0 I had the ip as 192.168.0.101
broadcast as 255.255.255.0
and gateway as 192.168.1.2 which is my ath0 address.

then I started the dhcp server

sudo /etc/init.d/dhcp3-server start

and voila I had a dhcp server running. I then started firestarter and went through the wizard, enabling internet connection sharing through eth0.

From the above eth0 was no directing towards my ath0, so the laptop side was fine.

My computer has windows xp on it. I double clicked the local area connection, to enable it went through properties and allowed it to use the dhcp.

Voila. I now had internet connection on both my computer and laptop through my computer.

Long story, I hope this helps.

---

