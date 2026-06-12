---
title: "how do i &quot;reset&quot; my wireless settings?"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by djberndt on 2007-02-10
hi everyone!

I'm having trouble with my wireless lan again on my laptop (ipw2200). when i have made the settings for the router essid in /etc/networks/interfaces, the small network icon shows poor (yellow colour) connection to the router, but when I for example start and exit kismet, the icon goes green. the same if I make changes in iwconfig, ie 'sudo iwconfig eth1 essid any'. It pops green, but i don't know why. the thing is, that even if the network icon is green and the signal is at least 95% i cant connect to anything.

this happened after i tried to redirect internet to my girlfriends computer. I made some changes, and I followed some guides, but I dont know which changes I made.

So, my question is as follows; how do i "reset" the network configurations as it was when ubuntu was newly installed? I'm greatful for any help.. soon i will go crazy.. my windows using friends is making fun of me because of "nothing works" in ubuntu, and i really don't want to use my windows installation. at least not when i'm working in school ;) 

cheers /daniel

---

### Post by daou on 2007-02-10
I'm not sure if I understood the question correctly, but here goes...

Does the router use DHCP? Ubuntu network devices are conffed to use DHCP by default. So if this is the problem, you could try:

sudo dhclient eth1

And don't worry about your friends. Let them spend their time fixing malware and updating anti-virus apps, while you take the same time to learn about how the computer actually works. In fact, I recently got a job interview because I started using Linux :wink:.

---

### Post by djberndt on 2007-02-10
hi, and thanks for your answer!

the router use dhcp, and with 'sudo dhclient eth1' it says: " no dhcpoffers received, no working leases in persistent database -sleeping"

BUT, when i use 'sudo kismet' or 'iwconfig eth1 essid any', the network icon pops green, and 'sudo dhclient eth1' works fine. but the internet still don't work. and i don't understand what the problem is.. =( i've also tried with other wireless routers, the problem remains.

SO, therefore i want to reset all network settings, since it worked just fine before i started to configure stuff :( 

cheers

---

### Post by djberndt on 2007-02-11
bump.

come on.. this is a very easy one for all pros out there! feels like i have tried everything..

please.

---

### Post by djberndt on 2007-02-15
:confused:  no one?

---

### Post by chili555 on 2007-02-15
If you want to reset the old-fashioned way, sudo gedit /etc/networks/interfaces and change eth1 to read:

```
auto eth1
iface eth1 inet dhcp
```

Save the file, and then do sudo ifdown eth1 followed by sudo ifup eth1.

Let us know.

---

### Post by spd106 on 2007-02-15
Kismet requires that the card is in rfmon or monitor mode. While in this mode you will not be able to connect to an access point. So make sure that it is back in managed mode. You can see which mode it's in with iwconfig.

If you have replaced the ipw firmware with some from another source then you will need to either find the originals through retracing your steps or simply re-install the kernel-image packages. The one you want is probably linux-image-2.6.17-11-generic.

I also suggest that you remove kismet for the time being. You can always put it back after.

In future it's probably a good idea to write down what you are doing and keep backups of important files. I must admit though, it's a lot less fun that way.

---

