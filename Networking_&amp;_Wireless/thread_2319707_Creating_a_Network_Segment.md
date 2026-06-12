---
title: "Creating a Network Segment"
date: 2016-04-06
forum: Networking &amp; Wireless
---

### Post by uwe-bungto on 2016-04-06
I have a Synology NAS and would like to connect a number of computers to it  in the IP range 192.16.0.20 to 192.168.0.30. How can I do create a network segment in this range to avoid typing in every possible address singularly?

Thanks

Paul

---

### Post by bab1 on 2016-04-07
> **uwe-bungto said:**
> I have a Synology NAS and would like to connect a number of computers to it  in the IP range 192.16.0.20 to 192.168.0.30. How can I do create a network segment in this range to avoid typing in every possible address singularly?

Thanks

Paul
Is this a typo```
192.16.0.20
# Should this be 192.168.0.20
```
Where would you be typing these addresses?  Is this a non-gui server or a deskktop?  If this is a desktop that uses Network-Manage the settings for the individual hosts.  The fields are: IP address - Network Mask (b'cast addr) and gateway. 

If you have 1 machine and you define its IP address and  broadcast address you have already defined [s]the[/s] a possible network segment it resides on.  That segment can be further defined when you add a second configured machine.

If you truly have machines in a single network that spans 192.16.0.20 to 192.168.0.30 you would have a network segment of *_16,777,216 _* IP addresses (i.e 192.0.0.0 /8).  The boundaries would be 192***.0.0.0*** to 192***.255.255.255***.

More likely you have a much smaller (and typical) 192.168.0.0 /24 with only 255 IP addresses.  The boundaries on this segment would be 192.168.0***.0*** and 192.168.0***.255***.

---

### Post by uwe-bungto on 2016-04-07
> **bab1 said:**
> Is this a typo```
192.16.0.20
# Should this be 192.168.0.20
```
Where would you be typing these addresses?  Is this a non-gui server or a deskktop?  If this is a desktop that uses Network-Manage the settings for the individual hosts.  The fields are: IP address - Network Mask (b'cast addr) and gateway. 

If you have 1 machine and you define its IP address and  broadcast address you have already defined [s]the[/s] a possible network segment it resides on.  That segment can be further defined when you add a second configured machine.

If you truly have machines in a single network that spans 192.16.0.20 to 192.168.0.30 you would have a network segment of *_16,777,216 _* IP addresses (i.e 192.0.0.0 /8).  The boundaries would be 192***.0.0.0*** to 192***.255.255.255***.

More likely you have a much smaller (and typical) 192.168.0.0 /24 with only 255 IP addresses.  The boundaries on this segment would be 192.168.0***.0*** and 192.168.0***.255***.

That was a typo should be 192.168.0.20. to 192.168.0.30
The server is managed with a web browser. It does show an example to set up a segment 
203.74.205.32/255.255.255.0, 203.74.205.32/24. I have no idea what it means.:confused:

I require just a few IP addresses. I have an ARRIS cable  modem/router. every time we have a power outage (Which is becoming common place here in Nova Scotia)the device reassigns some of the IP address and some of the computers can not connect to the Synology NAS.


What I would like to know is how to set up a segment 192.168.0.20. to 192.168.0.30, the basics behind it so I could say expand  it to 192.168.0.40 later without having to ask for help a second time.

Thanks
Paul

---

### Post by bab1 on 2016-04-07
> **uwe-bungto said:**
> That was a typo should be 192.168.0.20. to 192.168.0.30
The server is managed with a web browser. It does show an example to set up a segment 
203.74.205.32/255.255.255.0, 203.74.205.32/24. I have no idea what it means.:confused:

These are 2 examples of describing the network range of an example network.  The first one uses a subnet mask (255.255.255.0) to describe a 24 bit subnet segment (each 255 represents an 8 bit section of the network)  Three (3) octets of 8 equal 24 bits.  The second example defines the same network using CIDR notation (/24 = the same 24 bit mask).  

These definitions both say: The host at 203.74.205.32 in a network with a 24 bit mask is in a network that starts at 203.74.205.0 (the network ID number) and ends at 203.74.205.255 (the network broadcast address)
> 
I require just a few IP addresses. I have an ARRIS cable  modem/router. every time we have a power outage (Which is becoming common place here in Nova Scotia)the device reassigns some of the IP address and some of the computers can not connect to the Synology NAS.

If these addresses are set via DHCP you need to set the DHCP pool of addresses to the network range you want.
> 
What I would like to know is how to set up a segment 192.168.0.20. to 192.168.0.30, the basics behind it so I could say expand  it to 192.168.0.40 later without having to ask for help a second time.

Thanks
Paul
As I said you just set the pool of DHCP addresses to contain the lowest number address to the highest number.  Why do you need to expand it?  You can just set the range as 192.168.0.20 to 192.168.40 and be done with it.  That is 21 IP Addresses out of the 254 usable addresses of the network segment (subnet) 192.168.0.0 /24 (255.255.255.0.

Bear in mind these numbers are decimal listings of binary numbers.  The above network looks like this to the computer```
[COLOR="#FF0000"]**110000001010100000000000**[/COLOR][COLOR="#0000FF"]**00000000**[/COLOR] (192.168.0.0)

[COLOR="#FF0000"]**110000001010100000000000**[/COLOR][COLOR="#0000FF"]**11111111**[/COLOR] (192.168.0.255)
```
The red numbers are the network ID number (192.168.0).  The first 3 octets.
The blue numbers are the host addresses (00000000 = .0 to 11111111 = .255) The last octet.

---

### Post by Bucky Ball on 2016-04-08
I generally setup a range on the router itself then set static IPs outside of that range on the devices I want them on on the local machines themselves, but that may not be what you are looking for.

---

### Post by uwe-bungto on 2016-04-08
> **bab1 said:**
> These are 2 examples of describing the network range of an example network.  The first one uses a subnet mask (255.255.255.0) to describe a 24 bit subnet segment (each 255 represents an 8 bit section of the network)  Three (3) octets of 8 equal 24 bits.  The second example defines the same network using CIDR notation (/24 = the same 24 bit mask).  

These definitions both say: The host at 203.74.205.32 in a network with a 24 bit mask is in a network that starts at 203.74.205.0 (the network ID number) and ends at 203.74.205.255 (the network broadcast address)



Could I define my 10 address segment starting at 192.168.0.20 and ending at 192.168.0.30  by writing 192.168.0.20/255.255.255.30 ?

---

### Post by SeijiSensei on 2016-04-08
No, that's not how addressing works.

You can set up subnets in powers of two, so subnets can have two, four, eight, sixteen, etc., address ranges.  For instance, the range of addresses from 192.168.0.16 to 192.168.0.31 is defined as 192.168.0.16/28, or 192.168.0.16/255.255.255.240.  That means that 28 of the 32 bits in an IP address are used as the network prefix, and four are left for individual addresses within the subnet.  However two of those addresses cannot be assigned to hosts. In this case only the fourteen addresses between 17 and 30 can be assigned.  The address 192.168.0.16 is the "network address," and 192.168.0.31 is the "broadcast address."  

A common "class-C" private network like 192.168.1.0/24 encompasses all the addresses in the last "octet" of a dotted IP address.  It starts with a network address of 192.168.1.0, followed by 253 host addresses from 192.168.1.1 through 192.168.1.254, and a broadcast address of 192.168.1.255.

Rather than ten addresses you can use a /28 subnet that will give you 14 available addresses, or perhaps better a /27 that will give you 30 addresses to assign if you expect to expand the number of hosts you will be supporting.  The subnet value for a /27 is 255.255.255.224.  The last number is the difference between 256 and the number of addresses in the subnet, in this case 32.

If you need more help I recommend searching with Google about ip addressing and subnets.  You could also read the [Internet RFC about "CIDR" addressing]("https://tools.ietf.org/html/rfc4632"), but that may be too technical for your needs.

---

### Post by uwe-bungto on 2016-04-08
> **SeijiSensei said:**
> No, that's not how addressing works.

You can set up subnets in powers of two, so subnets can have two, four, eight, sixteen, etc., address ranges.  For instance, the range of addresses from 192.168.0.16 to 192.168.0.31 is defined as 192.168.0.16/28, or 192.168.0.16/255.255.255.240.  That means that 28 of the 32 bits in an IP address are used as the network prefix, and four are left for individual addresses within the subnet.  However two of those addresses cannot be assigned to hosts. In this case only the fourteen addresses between 17 and 30 can be assigned.  The address 192.168.0.16 is the "network address," and 192.168.0.31 is the "broadcast address."  

A common "class-C" private network like 192.168.1.0/24 encompasses all the addresses in the last "octet" of a dotted IP address.  It starts with a network address of 192.168.1.0, followed by 253 host addresses from 192.168.1.1 through 192.168.1.254, and a broadcast address of 192.168.1.255.

Rather than ten addresses you can use a /28 subnet that will give you 14 available addresses, or perhaps better a /27 that will give you 30 addresses to assign if you expect to expand the number of hosts you will be supporting.  The subnet value for a /27 is 255.255.255.224.  The last number is the difference between 256 and the number of addresses in the subnet, in this case 32.

If you need more help I recommend searching with Google about ip addressing and subnets.  You could also read the [Internet RFC about "CIDR" addressing]("https://tools.ietf.org/html/rfc4632"), but that may be too technical for your needs.

Thanks
I think this is what I am looking for.

---

