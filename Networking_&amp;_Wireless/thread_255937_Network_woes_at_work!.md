---
title: "Network woes at work!"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by elpuerco on 2006-09-12
I have a wi-fi adaptor and ethernet card in this laptop.

At home I use wi-fi with no trouble at all.

At work inside the firwall/gateway/whatever I cannot access the web or outside world when on the UTP cable?

I have tried to configure the card with no joy.

I entered the proxy guff

I entered my laptop hostname/computer name 

I entered the domain name

There are some IP addresses which are at our Head Office which looks right.

Under the defualt gateway it has the IP address of the laptop itself?

Any clues please? ](*,)

---

### Post by elpuerco on 2006-09-12
Is there some file somewhere that I need to edit to open port or something to get this to work maybe?

Have asked the IT bods at our HQ and they are as much use as chocolate condom!

---

### Post by tbonius on 2006-09-12
You might want to describe your network layout a bit more.  Is there DHCP at work?  Are you getting an address?  Is the ethernet card configured for DHCP?  Is there a firewall?  Proxy?  What does dmesg kernel messages show?  DO you get a link light?

T

---

### Post by Iowan on 2006-09-12
> **elpuerco said:**
> Under the defualt gateway it has the IP address of the laptop itself? Somehow that doesn't sound right - that would seem to make the laptop want to talk to itself??

---

### Post by elpuerco on 2006-09-12
Card is eth0 

Yes work is DCHP

When I installed on another laptop whilst connected to work it detected the IP addresses from HQ and entered them in the DNS list.

Card is confirgured for DCHP

There is a firewall

I entered the proxy when prompted during install and tried again after install.

The laptop doea not have a light as you describe...

---

### Post by tbonius on 2006-09-12
If you get no link light when plugging in the ethernet card.. is the card even detected?  I would assume it would have to be if you configured it for DHCP?  Again... answer the other questions.. what shows up when you type dmesg.  What shows up as your IP information.  How is /etc/network/interfaces configured?

T

---

### Post by elpuerco on 2006-09-12
I was mistaken re my IP address as the I beleive the IP there is the first one in the local range, xxx.xxx.xxx.1

Yes the card is enabled with a green tick.

the dmesg output is huge so I posted this bit:

[17179589.176000] PCI: Setting latency timer of device 0000:02:05.0 to 64
[17179589.180000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0a:e4:a4:13:dc
[17179589.180000] PCI: Enabling device 0000:02:06.0 (0000 -> 0002)
[17179589.180000] **** SET: Misaligned resource pointer: c1be2a02 Type 07 Len 0
[17179589.180000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[17179589.180000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKE] -> GSI 10 (
level, low) -> IRQ 10
[17179589.180000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179589.280000] ts: Compaq touchscreen protocol output
[17179589.304000] Yenta: ISA IRQ mask 0x0038, PCI irq 11
[17179589.304000] Socket status: 30000006
[17179589.304000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 t
o #06

/etc/network/interfaces shows this:

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth1
iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid xxxxxxx
	wireless-key1 xxxxxxxxxxx

iface eth0 inet dhcp

Note I am on wireless at home now not on eth0 at work.

But what the hell is the wep key saved as readable text in this file?  Is that not safe?

Thnx

---

### Post by tbonius on 2006-09-12
wheres your auto line for eth0?

auto eth0

You might want to do that.. or try manually :

ifup eth0

See of that works for you

T

---

### Post by elpuerco on 2006-09-13
I tried it manually and it gave a load of output, no errors.

I checked the Network config again and all looked OK

dmesg had this at the end of the output


[17179676.392000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179679.384000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17179679.384000] b44: eth0: Flow control is off for TX and off for RX.
[17179679.388000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17179690.104000] eth0: no IPv6 routers present

still not connecting?

could it be something to do with iptables?

---

### Post by elpuerco on 2006-09-13
I have sinced discovered that whilst on the network at work connected to eth0 I can ping computers both local to me and those at head office!

I configured the proxy settings to our proxcfg file and did the same in swiftfox but still no joy?

---

### Post by tbonius on 2006-09-14
A Proxy changes the entire picture.  Proxy settings are for applications.  Are you at least getting an IP address at work?  If you are then you have network connectivity.  Getting outside of your network out onto the internet is another story.  You need to configure individual applications for use with proxy services. (Or you could export HTTP_PROXY and FTP_PROXY lines via the shell environment)

---

### Post by cbaoth_2000 on 2006-09-14
The reason you can't get onto the Internet after configuring your Network Adaptor is purely because

A:your IP address setings are all wrong - similar settings to these should help you with explanations about your company Network.
private company LAN's will generally go with the normal private IP address ranges

an example IP address config on a Corporate LAN with less than 1000 computers will look like this

ip address:      192.168.1.20
subnet mask:     255.255.0.0
Default Gateway: 192.168.1.1

IP Address Ranges for LANS
A) 192.168.1*.100*
B  10.10.1*.100*
C) 172.16.1*.100* (The values with the * next to them can be any value from 0 to 255 but not 0.0)

SUBNET MASKS
used to identify which subnetted portion of the LAN you are on
255.255.0.0 the 0.0 signifys the 3rd and 4th octets 0.0 is used for host IP addresses(your laptop for instance is a host) giving a possible 255 multiplied by 255 = 65025 individual IP addresses for host usage
these two ip addresses are on the same NETWORK and the same subnet
A) 192.168.1.30
   255.255.0.0
B) 192.168.1.40
   255.255.0.0

the following are on the same NETWORK but different subnets
A) 192.168.2.30
   255.255.0.0
B) 192.168.1.40
   255.255.0.0
So being on a Network and wanting to communicate with another host not on the exact same Subnet(internet for instance)would mean you needed a Gateway entry for your computer to be able to attempt to reach the destination:
192.168.1.100 host
255.255.0.0   subnet mask
192.168.1.1   deault gateway 
which typically is .1 for ease of use seeing as it will be the WAY OUT (gateway)and means the IP Address of your Router or Firewall off your subnet/company LAN to the INTERNET normally or to another subnet for all you lot on a big enough LAN

So in short the Gateway ip address should be the ip address of your Firewall/Router which can be easily ascertained on a LAN from another computer on Your Work LAN with access to the Internet(or ask the choccy condoms to tell ya) If your company use a proxy server for Web Sufing it usually means they will have blocked all traffic out of the firewall except from the proxy server so you would need the IP address of the proxy server plus the Port (usually 8080 or 8118 or 80 for all protocols) to be able to even surf the net, Although i must say if it was my network your computer would just get quarantined whist authentication was checked and then blocked once your computers certificate failed the test all of which would have been logged to file automatically resulting in instant dismissal in line with normal corporate computer misuse policy if ever the user was identified.

All this eh just to surf the Net and i havnt even got onto DNS which is how your computer would be able to type [www.google.com](www.google.com) and find it by reolving the "www.google.com" to its IP Adrress but on your Company LAN it is needed for you to communicate anywhere!!!!!!!!!
A tale for another day though.

---

### Post by elpuerco on 2006-09-15
cbaoth_2000, a tad too techy for me I'm afraid!  

The IP address for the default gateway is the first IP address in out 'locale' allocation on DHCP.  My actual IP address differes with each logon usually ending in 60, 75 89 etc.

I asked our IT bods at head office and told them what I was trying to do and they directed me to the proxy setup page and said I could do it.

I can ping IP addresses in my physical location and elsewhere outside my physical location.

I entere the proxy address in both the network config and in Firefox and still no joy, it uses port 8080 by the way.

All this was tried prior to your post and so am still stuck?

:confused:

---

