---
title: "need an ehternet switch"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by hyperhopper on 2009-03-08
what is a good price for one?
what is a good brand?
what is good speedwise?
are there certain features i should be looking for?

---

### Post by Iowan on 2009-03-08
Lotsa variables, but I have a couple of D-Link 5-port switches I got for $15 (each), and an 8-port that was on sale for $25.  These are 10/100 switches - Gigabit switches are still a li'l pricey for me... plus, I have no gigabit ethernet cards.

---

### Post by hyperhopper on 2009-03-08
10/100

gigabit

huh?

---

### Post by halitech on 2009-03-08
10/100 and gigabyte refer to how fast the switch can transfer the data. In order to answer you better, we need a little more info.

Will the switch be used for just an internal network? (LAN)
Connecting multiple computers to a highspeed internet connection?
How fast is your internet connection?
Do you have a router currently?

---

### Post by rafac24 on 2009-03-08
Go wireless! Lol

---

### Post by hyperhopper on 2009-03-08
if you want to know EXACTLY what it will be used for see [http://ubuntuforums.org/showthread.php?t=1010202](http://ubuntuforums.org/showthread.php?t=1010202)

Condensed version:

have a internet connection that comes into the house and goes into a router. from there, four computers are hooked up into the internet.

however, i have aqired 3 servers to scrrew around with.

i have no clue about what they will be used for, probably to set up a file storage for my house and for me to screw around with (small website maybe? probably not...)

but, my router has only 4 ports, and i need to connect 4 computers + 3 servers, meaning i need a switch....


btw just did a test, download speed is about 15 mbps, upload is 3mbps

---

### Post by markbuntu on 2009-03-09
Just get a cheap 10/100 fast ethernet switch. I got a Trendnet for $10.

---

### Post by handydan918 on 2009-03-09
Just FYI, there is a difference between a switch and a hub. Hubs are usually less expensive, and will usually do whatever you need to do on a small lan.

---

### Post by bmj2728 on 2009-03-09
If you intend to use the router listed in your other post get a 10/100 switch, the router's built in switch only handles the 10/100 connection. The reason to use a gigabit switch instead of the 10/100 would be for moving data quickly from machine to machine within the home network, assuming your machines have gigabit ethernet connections.

---

### Post by djsephiroth on 2009-03-09
> **hyperhopper said:**
> what is a good price for one?

Depends on what your needs are. Unmanaged 100 Mbps switches with, say, 4-8 ports should be around $50-70. Managed switches running a decent OS are about $500 and up. A good gigabit 4-8 port switch is in the $100-150 area.
> 
what is a good brand?
Cisco. Cisco makes the best network hardware, imho. Linksys is Cisco's home and small business brand, and I've found their products to be more than adequate for my needs. However, I don't think that Linksys switches are always as top-notch as Linksys' APs and "routers".

I personally avoid D-Link and NetGear: there are so many horror stories of their hardware failing (usually right around the warranty's expiration date... check the newegg reviews) that it is not even funny. For about the same price, you can get Cisco/Linksys. That said, some of D-Link's offerings are decent, especially if you only need a switch for something trivial like adding a few more ports to a network.
> 
what is good speedwise?

Most switches are 10/100, meaning that they support 10Mbps and 100Mbps. 100Mbps = about 12.5 MB per second, which is fine for Internet access but slow for copying files from one machine to another. 1Gbps (a.k.a. 1000Mbps) = about 125MB per second, which is faster than a drive-to-drive transfer within your PC. Gigabit switches are more expensive, especially if they have a lot of ports, but the smaller ones with only 4 or 5 ports are often comparable to the 10/100 versions in price.
>  
are there certain features i should be looking for?
You will probably only need an unmanaged switch. Managed switches have a nifty user interface and support a lot of advanced functions such as VLAN support, various security features, quality of service, logging, etc.

If you use GE (gigabit ethernet), you will want "jumbo frame" support. It will drastically speed up your file transfers between machines on the LAN if their NICs (network interface cards) support it as well.

I keep forgetting that some places even sell hubs in the year 2009, but just in case someone tries to sell you one, **do not even consider hubs. They are ancient, slow, and without even the pretense of security.** They are not really any cheaper than switches (the difference may be as much as $10-20 for a large one, or as little as nothing at all). Hubs should never be used, even for the most trivial things, unless (a) it's your only option and you already have one lying about, or (b) you want to set up a network with a hub so as to sniff/log all network traffic.

Here's a good switch for your needs:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833127083](http://www.newegg.com/Product/Product.aspx?Item=N82E16833127083)

---

### Post by hyperhopper on 2009-03-09
huh....

i am so confused.... 

my download speed is 14811 kb per second....

how ca 100mbps == 12 MB per second? isnt mbps megabites per second?

im so confused....

also, you say stay away from D-link, but give me a link to a d-link switch


i feel really stupid,.....

---

### Post by hyperhopper on 2009-03-09
bump

---

### Post by ssam on 2009-04-16
B is bytes, and b is bits (though often people interchange them). interfaces (ethernet, USB, sata etc) tend to get measured in bits per second because it makes sense to electrical engineers. but files are usually measured in bytes, because thats the smallest unit of a file.

so 100 Mb/s ethernet can carry 12.5 MB/s, and file transfer speeds would be a little lower due to overheads.

a typical broadband connection might be 8Mb/s which gives 1MB/s

can anyone explain what would happen if i have a 100Mb router/modem, then plug in a gigabit switch/hub, and plug several computers with gigabit network cards into the switch/hub. obviously they wont magically be able to talk to the router or internet at 1Gb/s, but can the talk to each other at full speed. or will everython bounce through the router and be bottlenecked there?

---

### Post by Iowan on 2009-04-16
> **ssam said:**
> ... but can the talk to each other at full speed. or will everython bounce through the router and be bottlenecked there?If the machines connect to the switch (instead of the router), then the switch should transfer data at 1Gb/s.

---

### Post by souta95 on 2009-04-16
While what has been suggested so far, there are a few things that should be noted:

There is NO need for a Gigabit (10/100/1000Mbps) switch unless you have network cards (NICs) that support the Gigabit speeds, or want its functionality for the future.

As far as brands go, I don't see too much difference in general between them as far as reliability goes basing on what I have heard from other people and my own personal experiences.  In my own experiences I have had the worst luck with Linksys.  I use an older Buffalo router at home with 4 LAN ports.

I agree that it is better to get a switch than a hub, but if you have a hub, then use it.

If I were looking for one, I would go to Newegg.com and get the cheapest one that meets my needs and has good reviews.  The Rosewill 5 and 8-port 10/100 Mbps switches have really good reviews, so does the Rosewill 5-port gigabit switch (though not a good compared to the 10/100 ones).  Rosewill is a Newegg brand that I have had good luck with in the past.  I have only had one Rosewill product go belly up, and that was a power supply that they don't even sell anymore.

You may want to see if a local school or your work has an old switch or hub they will give you for free, that is how I got most of my equipment.

---

