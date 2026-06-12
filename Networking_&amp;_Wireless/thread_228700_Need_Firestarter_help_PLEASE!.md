---
title: "Need Firestarter help PLEASE!"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by CUBANb95 on 2006-08-03
ok I understand ther has been alot of post on this app but I havent really seen anybody having this problem with sharing internet connections.
OK, I would like my setup be: cable modem---->Ubuntu box---->Router--->3 Windows XP machines. now I have read the tutorial at the [firestater website]("http://www.fs-security.com/docs/connection-sharing.php") about internet sharing. 

First i set the corret configuration using dhcp for the incomming internet network card. Then I used a static IP config for the outgoing network card(or local network)of 192.168.0.1. Next I set a ip to the router wan interface using 192.168.0.2 and then using the default gateway of the local network ethernet card. lastly i sent the router dhcp to machines connecting to it off and set an ip to my xp box of 192.168.0.3 with a gateway of the router(192.168.0.2). now when starting firestarter with this configuration I get no error messages or anything but I have no connectivity to my xp box, however my ubuntu box still has internet and i have link lights all around. When I try to ping the local network card IP(192.168.0.1), host is unreachable, however i can obvisouly ping the router. 

The second setup I tried was to set up dhcp in firestarter using the default configuration, the router and on the xp box. when starting firestarter then I get a "failure to connect for unkown reason" message which im guessing is because of the static IP that the local network card is using. I still have internet on the ubuntu box. With link lights all around still.

So my question is should I be using a straight through cable from the ubuntu box to the wan port on the router or a crossover, and if not what may i be doing wrong with this config? Thanks for anyones input on this subject, sorry for such a long post. Thanks in advance.

I am using all straight through cables

---

### Post by CUBANb95 on 2006-08-03
Also I forgot to add I am using Version 5.10 of ubuntu. Any replies are much appricated...

---

### Post by tuga on 2006-08-03
Hello,
This is how I could share the internet with two PCs PC(xp)<->PC(Ubuntu)<->Internet(DHCP)...
# sudo -i
# ifconfig eth1 192.128.0.1
eth1 is the card connected to the PC(xp)
# iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
eth0 is the card connected to internet
# echo 1 > /proc/sys/net/ipv4/ip_forward
# apt-get install dnsmasq ipmasq
# /etc/init.d/dnsmasq restart
# dpkg-reconfigure ipmasq
Choose: After network interfaces are brought up. If this do not work try the other options...
# ifconfig eth1 192.128.0.1
# iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
On the file /etc/sysctl.conf, remove the # from the line "#net.ipv4.ip_forward=1"

---

### Post by CUBANb95 on 2006-08-03
yes I have tried this but i didnt do one thing. i actaully got the idea for firestarted from that thread. thanks for the help. However i do want to go cable modem---->Ubuntu box---->Router--->3 Windows XP machines. And i am now upgrading to 6.06

---

### Post by Mickeysofine1972 on 2006-08-03
Hi

I think you will be best off setting your main (Ubuntu computer connecting to the internet) machine to a static IP of something like 192.168.0.1 then you can set each of the other machines to XXX.XXX.X.2 & 3 etc. (where X is that same as the first part of the 'Main' machines IP address)

Because its a small network, you should get away with this. If you try this on a bigger scale you with need to use DHCP for sure.

any hoo, you need samba installed and also need to run firestarter on the the machine that accesses the internet.

once you have done this you should find the others can connect to the internet and you can search for samba shares (folders on other computers) after you have right-clicked on the folder you want to share and configured (on the ubuntu machine that is).

I have literally just done this myself and was amazed at how easy it was  after I read through all the bumf.

Mike

---

### Post by CUBANb95 on 2006-08-04
Ok, thanks for the reply. I will try this out tomrrow night nic I just finished installing drapper with all the packages i wanted. Just a couple of ?....did you have a router to all the other machines and did you assign that an ip of the same network? also wont ISP's get mad for using this ip class? i appricate the reply.

---

### Post by Mickeysofine1972 on 2006-08-04
Hi

I have two PC both running kubuntu, but no router, one has an adsl internet connection, the other shares by the NIC connection. If you are using a router then it would most probably have dhcp but if not then you can treat it like the router is a PC and assign IPs to the other PCs according to what IP the router starts with e.g.:

```

ROUTER : 192.168.0.1 (might be some thing else according to the make of router though)
PC #1: 192.168.0.2
PC #2: 192.168.0.3

```

all must share the same subnet mask though.

You ISP shouldn't have a problem with this type IP address as its private to your internal network and the only IP address they should see is your public one on the ADSL connection, because you should also be using a subnet mask of 255.255.255.0 and this will make sure your on your own network.

Your /etc/network/interfaces file should look something like this on the internet connected PC:
```

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0

```

and on your other PC without a ADSL connection it should be:

```

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

```

assuming the system recognises your ethernet cards as eth0 of course.

Mike

---

