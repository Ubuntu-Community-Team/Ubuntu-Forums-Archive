---
title: "how can i set eth0 to use 2 IP addresses!?"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by syntek on 2007-02-05
ive got an edgy system setup and working beautiful for one of my clients sites that im trying to move them from microsoft systems to ubuntu/open office and so far everything is working perfectly..

ONLY ONE PROBLEM..

Their network is using the subnet 192.168.17.x (the ubuntu box is 192.168.17.220, set static)

Way back when,  8+ years ago, when they setup their original IP network, they had it setup with the subnet 192.0.2.x.. The Windows clients grab their 192.168.17.x addresses thru DHCP, and in network config on XP, I added a static address on a few of the machines in the 192.0.2.x subnet..

How can I have eth0 use 2 IP addresses, like i have done on the XP boxes?

For instance, I'd like the single network card (eth0) to have the addresses 192.168.17.220 and 192.0.2.20 both set statically.

How can this be done? Thanks for any help in advance!

---

### Post by dmizer on 2007-02-05
i can't even begin to imagine how you've possibly made this work in windows.  i'd like to help you out, but the best of my knowlege states that your network adapter can only process with ONE ip address at any one given time.  in order for it to communicate with another ip address, it must disconnect from the first and then connect to the next.

need LOTS more information here.  how exactly does this work in windows?  please be as specific as possible.

---

### Post by syntek on 2007-02-05
i guess this is the single one thing windows does that linux cant! wow, im impressed..

check out this screenshot I just took of a Windows box where you can see what I'm talking about in the "advanced tcp/ip settings" window..

[IMG]http://jeremyaltman.net/gfx/windows-extra-IPs.png[/IMG]

---

### Post by SMGauna on 2007-02-05
The simple method would be to open a terminal and issue the command :

sudo ifconfig eth0:0 <ip address> netmask 255.255.255.0 up

Make sure you add an entry into /etc/network/interfaces :

auto eth0:0
iface eth0:0 inet static 
address <address>
netmask 255.255.255.0

Check the manual page for "interfaces" for more details on this.

Hope this helps... weird office set-up. :P

---

### Post by dmizer on 2007-02-05
windows can do many things linux cannot.  just as linux can do many things windows cannot.  they are not the same.

the only reason i know of to use the above configuration is if you are using windows as a web server where you are hosting two different sites on two different ip addresses.

anyway, truth of the matter is, that i think i'm in over my head with the understanding of your network design.

---

### Post by aberry5555 on 2007-02-06
it is definately possible as I do the same thing with apache to serve a few different sites on one card. It's built in to most every linux kernel with networking. As the guy a few posts above me has said, configure it in the same way as you usually would, only put a colon and a number after each one, e.g:

eth0:0
eth0:1
eth0:2

etc.

---

### Post by zgornel on 2007-02-07
For more info on linux networking, and multiple NIC IPs check [this]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking")
This is a very old feature of both Windows (NT) and Linux, dating back at least 12 years ago.

---

### Post by hectare on 2007-02-07
Its pretty simple to add multiple ip address to a nic and linux does not put any limit on it as such.

**ip addr add 192.168.17.220/24 dev eth0 brd + **
**ip addr add 192.0.2.20/24 dev eth0 brd + **
**ip addr add 10.1.1.1/24 dev eth0 brd + **

and so on
please check
**man ip**

Infact IP infrastructure on linux is mind blowing. There is no limit to what you can do.

---

