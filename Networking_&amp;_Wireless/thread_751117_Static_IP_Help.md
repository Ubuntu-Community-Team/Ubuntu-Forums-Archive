---
title: "Static IP Help"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by JCGuitarist on 2008-04-10
Hello, I am just a new one at natively booting Ubuntu, i have never had a need for a static IP but now that it i am Dual booting my Ubuntu interferes with the static machines on my windows network. i would really like to know how to do this. all the guides on the internet say pretty much the same thing. but this is whats in the interface file.

auto lo
iface lo inet loopback

is this normal, i havent seen this on the guides. what to do?

Thanks

---

### Post by wieman01 on 2008-04-10
Start here:

[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")

---

### Post by Kebabman on 2008-04-10
You would normally have an entry in there for your other network cards as well. Below is an example of a static configuration for an interface 'eth0' :

auto eth0
iface eth0 inet static
address 10.0.0.5
netmask 255.255.255.0
broadcast 10.0.0.255
gateway 10.0.0.1

Using this information you have got a static IP set up and all the necessary information to connect. Hope this helps. (Obviously change all the information to be relevant to your network :))

---

### Post by JCGuitarist on 2008-04-10
thank you very much but i figured out how to do it from the interface, a bit tricky. thatnks tho

---

