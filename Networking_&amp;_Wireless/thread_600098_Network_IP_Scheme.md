---
title: "Network IP Scheme"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by Meson on 2007-11-01
If my router has a local IP address of 192.168.1.1 and a subnet of 255.255.255.0 Will it be be able to talk to computers with another address such as 192.168.200.1?  What if you change the subnet to 255.255.0.0.  Does it matter what the client subnets are?

I'm not really experienced with subnetting and ip address schemes, so I hope knowing these things will help.

---

### Post by SpiritIsReality on 2007-11-02
howdy
I think it would take a router or a linux box with 2 nic cards to bridge you from the 
192.168.1.1 to the 192.168.200.1
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)
[https://help.ubuntu.com/community/InternetAndNetworking?action=fullsearch&context=180&value=router&titlesearch=Titles](https://help.ubuntu.com/community/InternetAndNetworking?action=fullsearch&context=180&value=router&titlesearch=Titles)
[https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28internetconnectionsharing%29](https://help.ubuntu.com/community/InternetConnectionSharing?highlight=%28internetconnectionsharing%29)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[http://linux-ip.net/html/](http://linux-ip.net/html/)
[http://www.google.ca/search?hl=en&q=linux+networking&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+networking&btnG=Google+Search&meta=)

if you went to 255.255.0.0 I think you'd have to be runnin a 172.16.0.1 through 172.31.255.254.
from aboutdebian.com
The internationally-established private IP address ranges that can be assigned to internal network computers are as follows: 
        * 10.0.0.1 through 10.255.255.254
              o 16,777,214 addresses
              o 16,777,214 computers on 1 network
                (10.x.x.x)
              o Uses a subnet mask of 255.0.0.0
              o First octet must be the same on all computers
              o A Class A address range 

        * 172.16.0.1 through 172.31.255.254
              o 1,048,574 addresses
              o 65,534 computers on each of 16 possible networks
                (172.16.x.x to 172.31.x.x)
              o Uses a subnet mask of 255.255.0.0
              o First two octets must be the same on all computers
              o A Class B address range 

        * 192.168.0.1 through 192.168.255.254
              o 65,534 addresses
              o 254 computers on each of 256 possible networks
                (192.168.0 to 255.x)
              o Uses a subnet mask of 255.255.255.0
              o First three octets must be the same on all computers
              o A Class C address range 
trails

---

### Post by froy02 on 2007-11-02
NO, since your dchp gateway is 192.168.1.1, the  addresses you have to use must be 192.168.1.xxx where .xxx must be higher than 1.  The first 3 sets should be the same 192.168.1.

Check your dchp by typing 'htttp://192.168.1.1.' in your browser and it would show you the range of ip adresses that you could use. Best way to set it up is by autmatic assignment of ip address.  Less hassle.

So you could probably use this range from 100-200, 
e.g  192.168.1.100,  192.168.1.101, 192.168.1.102 and so on.

---

### Post by tkharris on 2007-11-02
Don't use a bigger IP range than you need! *says the one with the 10/8 network at home*

---

### Post by Meson on 2007-11-02
Well the reason I'm asking is because I have a main router, and then a wireless router attached to it.  I wanted to make a setup so the two networks couldn't talk to eachother.  And also be able to hae another setup where they have two different address schemes but can talk to each other.  Like 192.168.1.x for wired and 192.168.2.x for wirless.

---

### Post by alvinmaker on 2007-11-02
try making your network mask 255.255.255.128.

make you wired router have and ip of 192.168.1.0. For every computer that connects using the wired connection assign an ip of 192.168.1.1 to 192.168.1.127

for your wireless router assign an ip of 192.168.1.129. For every computer that connects using the wirelss connection assign an ip of 192.168.1.130 to 192.168.1.254

---

### Post by SpiritIsReality on 2007-11-02
> **tkharris said:**
> Don't use a bigger IP range than you need! *says the one with the 10/8 network at home*

howdy.
could you give us more information on how you set up  your network?
edit:doh! lol
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)
> 255.0.0.0 	        	/8

10.0.0.1 through 10.255.255.254

    * 16,777,214 addresses
    * 16,777,214 computers on 1 network
      (10.x.x.x)
    * Uses a subnet mask of 255.0.0.0
    * First octet must be the same on all computers
    * A Class A address range 

trails

---

### Post by SpiritIsReality on 2007-11-02
> **alvinmaker said:**
> try making your network mask 255.255.255.128.

make you wired router have and ip of 192.168.1.0. For every computer that connects using the wired connection assign an ip of 192.168.1.1 to 192.168.1.127

for your wireless router assign an ip of 192.168.1.129. For every computer that connects using the wirelss connection assign an ip of 192.168.1.130 to 192.168.1.254

howdy
what would the netmask of the wireless router be?
isn't 192.168.1.0 the network designation? so the wired router would need to bump up one to 192.168.1.1 ?
thankyou for your post. I've been trying to figure out how to subnet a 192.168.0.0 network
for an ltsp server.
[http://en.wikipedia.org/wiki/Subnetting](http://en.wikipedia.org/wiki/Subnetting)
trails

---

