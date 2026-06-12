---
title: "Can't access the network"
date: 2005-01-02
forum: Networking &amp; Wireless
---

### Post by Shimonn on 2005-01-02
I Just installed Ubuntu.
I had no problem else the installer didn't found my DHCP server, so i set the IP (192.168.0.11), mask, and gateway address manually.
In fact can not access anything through my network from Ubuntu.

I've only one ethernet card. "lspci" say it is "Linksys NC100" and Windows "ADMtek AN938".
This card works with Windows and Knoppix 3.4 (at least)
My network is simple : each computer is conected to a switch, the gateway (192.168.0.254) is using NAT for the internet connection. It works without problem form other computers and when i'm using windows instead of linux (ubuntu).

The configuration is correct : an IP address (192.168.0.11), a correct netmask (255.255.255.0) ; a route on eth0 for the local network 192.168.0.0 with the correct mask 255.255.255.0 and a default route using the gateway 192.168.0.254

If i try to ping the gateway : "ping 192.168.0.254", i've an error message : "Destination Host Unreachable". Sniffing with tcpdump, i see ubuntu sends an arp query to know the MAC address of 192.168.0.254, but does not receive anything.
Form other computer (the gateway) i see thet the arp query is received and answered, but ubuntu does not receive the answer.
It's the same with DHCP : the DHCPDISCOVER is sent but ubuntu doesn't receive the DHCPOFFER (wich is sent)
It seems i can send datas but not receive anything.

Any idea what's the problem ?

---

### Post by Shimonn on 2005-01-04
In short : i can send datas bt not receive anything

I tried the live CD, the network works without problems !
I tried a 2.6.7 kernel (used by the live CD) but no change ...

nobody knows what could be the problem ?

---

### Post by fng on 2005-01-04
Could you run the command 'ifconfig' and post the result here?

---

### Post by Shimonn on 2005-01-05
> The configuration is correct : an IP address (192.168.0.11), a correct netmask (255.255.255.0) ; a route on eth0 for the local network 192.168.0.0 with the correct mask 255.255.255.0 and a default route using the gateway 192.168.0.254 

```
# ifconfig eth0

eth0
      Lien encap:Ethernet  HWaddr 00:50:BF:A0:AE:30

      inet adr:192.168.0.11  Bcast:192.168.0.255  Masque:255.255.255.0
      adr inet6: fe80::250:bfff:fea0:ae30/64 Scope:Lien

      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

      collisions:0 lg file transmission:1000

      RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

      Interruption:11 Adresse de base:0xa000

# route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
```

---

### Post by rolando on 2005-01-05
What is your 192.168.0.0 is that your router?

If it is I would use 192.168.0.0 as your default gateway

Thats what I do.

---

### Post by Shimonn on 2005-01-05
No. 192.168.0.0 is the local network. I should have said 192.168.0.*

The router, gateway or whatever it is named, is a computer witch uses NAT for the internet access. It's IP address on the private network is 192.168.0.254

---

### Post by rolando on 2005-01-06
So your router / gateway is a computer? What OS is it running, has it got a firewall on it?

How does your network setup look?, mine is like this:

Laptop (192.168.0.x)---------- >(192.168.0.1) Wireless Router & ADSL modem using NAT (66.102.11.123)--------- >Internet

What is the private side and public side of your Router / Gateway?

---

### Post by wallijonn on 2005-01-06
You're using DHCP and assigning a static address?

Applications -> System Tools -> Network Tools to ping your gateway.

Computer -> System Configuration -> Networking
What is set active?
Hit the "Add button" go through the wizard...

---

### Post by Shimonn on 2005-01-07
Please *read* my first message ...
My router is running Debian Linux (Woody) with a 2.6 kernel and iptables (for NAT and firewall)
I've installed a DHCP server on it and all of this works well.

Thanks you, I know how to ping the gateway.
I already said it doesn't work beacause Ubuntu does not receive anything, so does not receive ARP traffic.

I set a static address as DHCP did *not* work during the install and after (running dhclient eth0)

One again, please read my first post, i said the configuration is correct.

---

### Post by hardcandy on 2005-01-07
> I've only one ethernet card. "lspci" say it is "Linksys NC100" and Windows "ADMtek AN938". 
That may be a clue, perhaps the driver that is loaded is not the correct version? I realize you can get a ifconfig result, but make sure the tulip.o module is being used. 
[Linksys driver support for linux](http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=769&p_created=1084221281&p_sid=CtUOCXuh&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3NlYXJjaF90eXBlPXNlYXJjaF9ubCZwX3Byb2RfbHZsMT0xMjQmcF9wcm9kX2x2bDI9JnBfc2NmX2xhbmc9MSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWxpbnV4&p_li=)  That was for a 2.4 kernel, but the section "new bus configuration" and "use PCI shared memory for NIC registers" maybe the problem?? Don't really know. 

No google reults at all for "admtek an938".  What brand is it exactly?

---

### Post by Shimonn on 2005-01-07
Yes, the tuliup module is loaded (lspci)

[QUOTE=hardcandy]That may be a clue[/QUOTE]
I already successfuly used this card with other versions of windows, and with other linux distro (Debian Sarge, Knoppix, MandrakeMove), and i always seen that (Linksys / ADMtek)
Windows says the constructor is "ADMtek Incorporated". I think Linksys is the type of chipset.

---

### Post by wallijonn on 2005-01-07
[QUOTE=Shimonn]The installer didn't find my DHCP server.
I set the IP (192.168.0.11), mask, and gateway address manually.
I can not access anything through my network from Ubuntu.

"lspci" - "Linksys NC100" 
Windows - "ADMtek AN938".
This card works with Windows and Knoppix 3.4 (at least)

Each computer is conected to a switch.

The gateway (192.168.0.254) is using NAT for the internet connection. 

It works without problem form other computers and when I'm using Windows instead of Linux (Ubuntu).

The configuration is correct : an IP address (192.168.0.11), a correct netmask (255.255.255.0) ; a route on eth0 for the local network 192.168.0.0 with the correct mask 255.255.255.0 and a default route using the gateway 192.168.0.254

If I try to ping the gateway : "ping 192.168.0.254", I get an error message : "Destination Host Unreachable". 

Sniffing with tcpdump, i see ubuntu sends an ARP query to know the MAC address of 192.168.0.254, but does not receive anything.

Form other computer (the gateway) I see thet the ARP query is received and answered, but Ubuntu does not receive the answer.

It's the same with DHCP : the DHCPDISCOVER is sent but Ubuntu doesn't receive the DHCPOFFER (which is sent).

It seems I can send data but not receive.[/QUOTE]

What ethernet card do you actually have? Is it a Linksys NC100? Or is it an ADM938? The fact that you're saying that it is seen as two different interfaces makes me believe that the correct driver is not being compiled and installed. 

[http://www.etherboot.org/db/nics.php?show=tech_data&chip_manufacturer=ADMTek](http://www.etherboot.org/db/nics.php?show=tech_data&chip_manufacturer=ADMTek)

Is it an ADM938 or an ADM983? [http://www.infineon.com/cgi/ecrm.dll/ecrm/scripts/prod_cat.jsp?oid=-12485](http://www.infineon.com/cgi/ecrm.dll/ecrm/scripts/prod_cat.jsp?oid=-12485)

Do you use a dual boot or caddies?

On my old Fedora and SUSE installs I would many times have to reset my modem when I switched from Linux to Windows or from Windows to Linux. I am not saying that Ubuntu has a problem, I am just saying that there may be remnants of Windows mappings.  

Now, starting with /etc/iftab, I take it that that is your real MAC address? It's what is listed in Network Tools when you select the Netwrok device.

I also take it that /etc/resolv.conf contains your gateway or ISP addresses?

If you have the Ubuntu LiveCD, does it connect correctly? 

Does /etc/network/interfaces list "auto eth0" and "iface eth0 inet dhcp" ?

---

### Post by hardcandy on 2005-01-07
One other thing to consider, if you have another nic to put in that machine and see if the situation is resolved. Rule out any hardware problem.

---

### Post by Shimonn on 2005-01-08
I bought a "Network Starter Kit", sold by Sitecom, containing 2 PCI cards and a crossed cable.
(this one : [http://sitecom.com/products_info.php?product_id=181&grp_id=5](http://sitecom.com/products_info.php?product_id=181&grp_id=5) )

In Windows' device manager I see an "Carte Ethernet à base ADMtek AN983" (in french)
The drivers used by Windows XP is C:\WINDOWS\System32\DRIVERS\an983.sys
It works without problems with Windows XP and 98.


Ubuntu installor installed grub, to do a dual boot with Windows XP and Ubuntu (+ Memtest)

/etc/resolv.conf contain the DNS server i set during te install (it is 192.168.0.254 : i installed Bind on my gateway)

I tried Ubuntu LiveCD, it works without problems (inculding the network)

> Does /etc/network/interfaces list "auto eth0" and "iface eth0 inet dhcp" ?
No. The DHCP discover failed during the install (as Ubuntu does not receive server's answer), so /etc/network/interfaces contain the manuel config i set during the install

---

### Post by BWehrle on 2005-01-26
I believe I am having the same problem.  I have a similar setup and am using the tulip driver.  I noticed that my link gets dropped, so I load the driver with a media sense flag:

tulip options=4

However, I have a similar setup, but I CAN see the ARP response using:
arp -a

Can you please try that and see what info you get?
Likewise, confirm that the link light stays green after bringing up the interface.

I, too get a message saying the same thing, and my network is really the same as the one you described.   Since I know the packet is going to the right place, namely my router, the routes are right, and the ICMP message comes FROM my router,  I feel that my system is in part emitting the correct IP frame.   I should install a sniffer to find out!

It seems funny that you are having the same problem with the same card!

---

### Post by Shimonn on 2005-02-09
Hi, i tested another ethernet card, and i've the same problem  :shock:  ](*,)

---

### Post by alastair on 2005-02-09
This is really odd. I read your first post and it looks like you know what you're doing - all looks OK.

You say that the arp query is received by the gateway, which replies but Ubuntu does not get the reply?

So you card /is/ physically working - it transmits an arp query. You see the reply from the gateway.

I've never played with manually setting arp up - but it can be done. You could try setting an arp cache on the Ubuntu machine manually (for the gateway) - then try a ping. At least this removes the need for an arp query.

e.g.

sudo arp -i eth0 -s 192.168.0.254 <gateway MAC>

Then check via "arp -a".

Extremely odd.

---

### Post by Shimonn on 2005-02-11
Yes, i could set the MAC address manually, but it won't resolve the problem.
I can not receive *any* data. The problem is exactly the same with DHCP : the query is received and answered, but Ubuntu does not receive anything.

I've been reading about IPv6. The [Linux+IPv6-HOWTO](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Linux+IPv6-HOWTO.html#AEN767)  says :
> A major issue is that because of the network layer structure of kernel implementation an IPv6 packet isn't really recognized by it's IP header number (6 instead of 4). It's recognized by the protocol number of the Layer 2 transport protocol. Therefore any transport protocol which doesn't use such protocol number cannot dispatch IPv6 packets. Note: **the packet is still transported over the link, but on receivers side, the dispatching won't work** (you can see this e.g. using tcpdump). 
It looks strangely like my problem.

How to disable any IPv6 unsing attempt in Ubuntu ?

---

### Post by jubuntus on 2005-02-12
Your configuration sounds 100% correct. Perhaps you need to clear the forwading database on your switch? A switch dynamically updates a database with port number/mac address mappings. A switch usually clears entries for a port if the connection goes down on that port or they clear the entry after a configurable timeout value and no packets have been received from that mac address.
Maybe yours has gone a bit haywire?
Sorry, that's all I can think of. You're sending packets ok, the switch is getting them, forwarding them to the router, and they're not getting back to you coz the switch thinks you're on another port, perhaps?

[QUOTE=rolando]What is the private side and public side of your Router / Gateway?[/QUOTE]

Just so you know, the 192.168.x.x ip address range is a private address range, as is 10.x.x.x, and are therefore not routable on the public internet. Therefore, in any case when someone mentions a network address range of 192.168.x.x they are, by definition, talking about a private network.

Update! Actually, I just reread the OP more carefully, and the 2nd page of this thread! (why doesn't the thread just appear on one long page?). If you put the Live CD in and it worked, then I doubt it's a switch fdb problem, so disregard what I have said, which you probably already have! :)

Good luck.

---

### Post by jubuntus on 2005-02-12
> 4.1.4. IPv6-ready network devices

Not all existing network devices have already (or ever) the capability to transport IPv6 packets. A current status can be found at IPv6+Linux-status-kernel.html#transport.

A major issue is that because of the network layer structure of kernel implementation an IPv6 packet isn't really recognized by it's IP header number (6 instead of 4). It's recognized by the protocol number of the Layer 2 transport protocol. Therefore any transport protocol which doesn't use such protocol number cannot dispatch IPv6 packets. Note: the packet is still transported over the link, but on receivers side, the dispatching won't work (you can see this e.g. using tcpdump). 

Upon first reading, I don't think this is your problem. Especially if you follow the link, it says that Ethernet should work ok.

But I think your thoughts of disabling IPv6 could be wise. I thought IPv6 had been put on the back burner after NAT became widely implemented? Sorry, I've been out of the networking industry for 3 years now.

---

### Post by Shimonn on 2005-02-12
IPv6 is probablly not the problem beacause :
* as you said, it should work on ethernet
* i ping an IPv4 address
* deleting the IPv6 address (sudo ifconfig eth0 del [IPv6_addr]) doesn't resolve the problem.

Also, i thinks the switch is doing it's job as :
* I've no problem using the same computer with the same ethernet card on the same switch's port while running windows
* The switch relayed arp and dhcp queries, so it should know the MAC address
* I've the same problem being directly conected to my modem/router (with NAT routing disabled, it's simply a DHCP relay)

---

### Post by Shimonn on 2005-02-12
Strange ...

* MandrakeMove : autodetect, config via DHCP, connection works. kernel : 2.4.22-21.3mdk
* Debian Woody 3.0r2 (CD1 installer) : go to step "Configure the network", choose DHCP, connection works. kernel : 2.2.20-idepci or 2.4.18-bf2.4 (both works)
* Gentoo LiveCD 2004.1 : autodetect failed, eth0 appears in ifconfig after "modprobe 8139too", but doesn't work (dhcp and ping failed).
* Knoppix 3.7 : eth0 autodetected, but dhcp and ping failed. kernel : 2.4.27
* Ubuntu LiveCD : autodetect, works. kernel : 2.6.7

---

### Post by jubuntus on 2005-02-12
OK. To rule out all network stuff for 1000% sure and to consign this problem to being software/driver related (at which point I could no longer help you :)), I would do the following.
Install a packet sniffer on ubuntu. I think the best oss sniffer available is [http://www.ethereal.com](http://www.ethereal.com). Start sniffing and restart the network service (so that a DHCP request is sent out). You can also set IP manually and ping the gateway. Capture all packets. I would do this on both Windows (working) and Ubuntu (not working) just to compare the 2 and see if Ubuntu is sending out the same stuff that Windows is sending out.
An even better solution, if you have a spare computer and a hub, is to install ethereal on the spare PC and plug both this PC and ubuntu into the same hub, and connect that hub to a port on the switch. Then capture packets. Then do the same thing but swap ubuntu and the gateway, so the spare PC is now sniffing the gateway side of the switch.
You want to look at all layer 2 stuff in the packets, and make sure everything is OK. You sound like you know your stuff, so I'm sure you can work it out if you haven't done it before, and if you have, then easy peasy.
Mate, I don't envy you installing all those distros to solve this problem one little bit.
Update: OK, that's the last time I post without reading the entire thread completely. It seems you already did a sniff. Sorry.

---

### Post by Shimonn on 2005-02-12
yes :-)
it would be a bit difficult to install Etheral without connection, but i've tcpdump installed with ubuntu.
When sniffing on my dhcp server, i see DHCPDISCOVER queries from Ubuntu and DHCPOFFER answers from the dhcp server, but on Ubuntu i only see DHCPDISCOVER.
When trying to ping, i see the same situation with ARP.

That's how a made the conclusion i can *send* data, but not *receive* anything ... strange, isn't it ?

lol, i did not install all these distros, i just tested live CD's or installation CD's ...

I tried to sniff Windows' DHCP queries, but Etheral stops when i disable the inferface. (and i'm not fast enought to launch the sniff *after* reactivating the interface and *before* Windows sends DHCP queries ;-) )

It's not an hardware or configuration problem, as it works with the same hardware and config with Windows and some distros.
It's not specific to Ubuntu as i've the same problem with some other distros.
It's not my ethernet card wich is uncomplatible as i tested two differents cards.

So ... what ?

---

### Post by wa03 on 2005-02-18
Try downloading the .deb for dhcpcd on a different machine and transferring it to the ubuntu system. I had problems with my wireless card and dhclient that were completely alieviated when I switched to dhcpcd. I understand you don't have the internet... perhaps liveCD and chroot? All I know is that the instant I install dhcpcd on my machine, I was able to get a response from the DHCP server and internet worked.

wa03

---

### Post by Shimonn on 2005-02-18
Downloading is not the problem, i still have Windows on the same computer (with grub dual boot)

My problem is not related to DHCP
It's exactly the same with ARP : i do not receive any data.
When sniffing from other computers i see answers are sent, but i don't see them when sniffing from Ubuntu.

---

### Post by maverick on 2005-03-18
[QUOTE=Shimonn]I Just installed Ubuntu.
I had no problem else the installer didn't found my DHCP server, so i set the IP (192.168.0.11), mask, and gateway address manually.
In fact can not access anything through my network from Ubuntu.

I've only one ethernet card. "lspci" say it is "Linksys NC100" and Windows "ADMtek AN938".
This card works with Windows and Knoppix 3.4 (at least)
My network is simple : each computer is conected to a switch, the gateway (192.168.0.254) is using NAT for the internet connection. It works without problem form other computers and when i'm using windows instead of linux (ubuntu).

The configuration is correct : an IP address (192.168.0.11), a correct netmask (255.255.255.0) ; a route on eth0 for the local network 192.168.0.0 with the correct mask 255.255.255.0 and a default route using the gateway 192.168.0.254

If i try to ping the gateway : "ping 192.168.0.254", i've an error message : "Destination Host Unreachable". Sniffing with tcpdump, i see ubuntu sends an arp query to know the MAC address of 192.168.0.254, but does not receive anything.
Form other computer (the gateway) i see thet the arp query is received and answered, but ubuntu does not receive the answer.
It's the same with DHCP : the DHCPDISCOVER is sent but ubuntu doesn't receive the DHCPOFFER (wich is sent)
It seems i can send datas but not receive anything.

Any idea what's the problem ?[/QUOTE]

Please check if your ethernet card is still working after you've used Windows by checking it's leds on the back side of your PC. I'have a 8139too card which turns off after hibernating the Windows XP.

Cheers,
Aleksandar Dezelin

---

### Post by Shimonn on 2005-03-20
> Please check if your ethernet card is still working after you've used Windows by checking it's leds on the back side of your PC. I'have a 8139too card which turns off after hibernating the Windows XP. 
I don't understand what you mean.
The ethernet card's led is always on ...

---

### Post by maverick on 2005-03-21
[QUOTE=Shimonn]I don't understand what you mean.
The ethernet card's led is always on ...[/QUOTE]

I mean exactly what I've said: If you hiberneted your Windows, there's a possibility that your network card is left in a hibernated state so it wont work when you dual boot into your linux system. But this is probably not the couse of your troubles with network becouse your network card is working.

---

### Post by corentin on 2005-04-27
'may seem stupid, but i already had a similar problem playing with the freesbie,
a free-bsd live cd.

the freesbie and your conf have sthg in common :

both of them have this default config : ipv6 interfaces ( lo and ether )  and an ipv6-to-ipv4 sit virtual interface...

when i tried to connect to the internet, i couldnt receive anything, when with another
distro ( pure ipv4 ) dhcp succeeded.


i think that it IS ipv6 related : look at advanced routing howto - part ipv6 over ipv4:
ip tunnel mode sit (...) is working with fixed ip.

as far as I know, you can't "dhcp" virtual interfaces ( --> no dhcp success with sit )
so, you cannot get your dns and you default routing table with sit
is not dynamically  created .....


 If it helps ....

---

### Post by andrubuntu on 2005-04-28
I had the same problem today.  One of the forums (I forget which) suggested looking  at /var/log/syslog  I had a couple entries during boot that had comments.

localhost kernel: irq 10: nobody cared ( try booting with the "irqpoll" option.
localhost kernel: PCI: IRQ 0 for device 0000:00:08.0 doesn't match PIRQ mask - try pci=usepirqmask
 

anyway, what worked for me was to use this as the default of /boot/grub/menu.lst

kernal  /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro acpi=off aclpi=off pci=usepirqmask irqpoll

---

