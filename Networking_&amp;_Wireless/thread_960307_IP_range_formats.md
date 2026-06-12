---
title: "IP range formats"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by sefs on 2008-10-27
I would like to specify the IP range:

192.168.0.1 - 192.168.254.254


in the /xx format

for instance if i want to specify 192.168.1.1 - 192.168.1.254 I can put 192.168.1.0/24

but for 192.168.0.1 - 192.168.254.254 how would I do that.

Thanks.

---

### Post by Dark Hornet on 2008-10-27
Well, the problem you are having is you are trying to use a "class C" block (/24) to describe something that should be described by a "class B" (/16) or one of its subnets.  The address space you are looking for would be better accommodated by 172.16.0.0/16, or something along those lines.  Typically the 192.168.0.0 address space is used as /24, and therefore does not have enough hosts do do what you want.  I hope this answers your question, and let me know if you need anything else.

Darkhornet

---

### Post by redmk2 on 2008-10-27
I believe 192.168.0.0/16 is a legitimate IP network (range).  Whether this range is reserved in /24 blocks or one /16 block is another matter.  The range 172.16.0.0/16 is not different in that way than 192.168.0.0/16.  As a mater of fact 10.0.0.0/16 the same also.  The /16 is the number of bits in the network part of the IP address.

There is no "better" it is only convention.  None of the above networks will be passed through routers on the internet.  They are all considered "private"

EDIT: To address the O/P's question of specifying a range, you have to look at it from the binary perspective, not decimal.  There are binary boundaries.  A network is a group of [COLOR="Red"]CONTIGUOUS[/COLOR] numbers.  The boundaries in any octet are defined by the subnet mask.  They are  128, 192, 224, 240, 248, 252 and 255.     These correspond to the numbers used in the /n notation.  If we were looking at the third octet these would be /17 through /24

---

### Post by Dark Hornet on 2008-10-27
You are correct in stating that the 192.168, 172.16, and 10.0.0.0 ranges are all private, and "legitimate" IP blocks...however the IP spacing he requires is more that what a typical /24 block will provide, and if he wants to use the 192.168 block he will HAVE to use a /24 or smaller subnet, as 192.0.1.1 to 223.255.254.254 is defined as a "class C".  "Class B" is defined as 128.1.0.1 to 191.255.255.254, and "Class A" is defined as 1.0.0.1 to 126.255.255.254.  And depending on the network device he is inputing this information into, it will not accept an "incorrect" ip range.

Darkhornet

---

### Post by Iowan on 2008-10-27
CIDR has kinda made the "class" distinction less "strict" (?).
(CIDR= Classless Inter-Domain Routing).

---

### Post by redmk2 on 2008-10-27
I have never seen a device that won't accept any valid subnet mask.  CIDR is the definition of subneting the subnet.  Class definition is just that, a definition only.  I believe the O/P's range is NOT contiguous and crosses binary boundaries.

Edit: Another way to look at the class definition is by which octet you are defining with a subnet mask.  See: [http://mdsafri.tripod.com/classb.htm]("http://mdsafri.tripod.com/classb.htm")

---

### Post by sefs on 2008-10-27
So, 

What I am getting from this is instead of trying to get it in defined in one big block, I should break it up into smaller blocks which are contiguos and does not cross the boundaries?

---

### Post by redmk2 on 2008-10-27
You asked a question on a range and how to list it using /XX nomenclature.  Is this theoretical or real world?  You can use the whole network 192.168.0.0/16 network if you wish or break it up.  But the parts must be on the bit boundaries. 

I am making a chart of the subnetwork bit boundaries for the 192.168.0.0/16 network.  I will post it here in a little while.

Do you have a specific real world question for now?

---

### Post by redmk2 on 2008-10-27
@sefs

Your range of 192.168.0.1 - 192.168.254.254 is almost the entire network 192.168.0.0/16 (s/m 255.255.0.0) network. The amount left over ie; 192.168.254.255 to 192.168.255.255 is one subnet of /24 plus the IP address of 192.168.254.255.

If this is what you want then the proper identification is: 192.168.0.0/16  See the chart below:

**[SIZE="2"]A simple guide to subnetworks in the 192.168.0.0/16 network[/SIZE]**

1 network (s/m 255.255.0.0)

192.168.0.0/16

255 subnetworks (s/m 255.255.255.0)

192.168.0.0/24	
192.168.1.0/24	
192.168.3.0/24
192.168.4.0/24	
192.168.5.0/24
192.168.6.0/24
192.168.7.0/24
192.168.8.0/24
192.168.9.0/24
192.168.10.0/24
192.168.11.0/24
192.168.12.0/24
192.168.13.0/24
192.168.14.0/24
192.168.15.0/24

and so on...

What does the /nn mean?  The number of bits in the 1 state (as opposed to the 0 state).

What does the 255 mean?  The decimal equivalent of all 8 bits on in an octet.

What is an octet?  An 8 bit number ie; octet.octet.octet.octet 

So an octet with all bits on is: 11111111 or 255.  And all off is: 00000000 or 0

Here is a list of the bitwise listing of the 3rd octet (remember there already are 16 bits from the first two octets):

/24 = 11111111 = 255 
/23 + 11111110 = 254 
/22 = 11111100 = 252
/21 = 11111000 = 248
/20 = 11110000 = 240
/19 = 11100000 = 224
/18 = 11000000 = 192
/17 = 10000000 = 128


Your range of 192.168.0.1 - 192.168.254.254 is almost the entire network 192.168.0.0/16 (s/m 255.0.0) network. The amount left over ie; 192.168.254.255 to 192.168.255.255 is one subnet of /24 plus the IP address of 192.168.254.255.

If this is what you want then the proper identification is: 192.168.0.0/16 or where appropriate use the s/m of 255.255.0.0

---

### Post by sefs on 2008-10-28
My apologies for the confusion....

I really meant the entire network...
192.168.0.1 to 192.168.255.255

As for real world i want to open some ports in a firewall that are accessible to the range above.

the firewall gui allows you to enter the range with x.x.x.x/xx format

so I wanted a simple way to just specify the whole range without have to do

192.168.0.0/24
.
.
.
192.168.255.0/24

multiple times so i had thought that 192.168.0.0/16 would have done the trick.

---

### Post by redmk2 on 2008-10-28
@sefs,

You are correct.  The way to describe the host range is: > 192.168.0.1 to 198.162.255.254
(192.168..0.0 = network id and 192.168.255.255 = broadcast address)
Therefore the network is: > 192.168.0.0/16

Note that the s/m for this is 255.255.0.0

Edit: This will give you some odd, but valid **host IP addresses**.  Most won't think them correct eg; 192.168.0.255 is valid and 192.168.1.0 is too.  These are within a valid range  of a /16 network.

---

