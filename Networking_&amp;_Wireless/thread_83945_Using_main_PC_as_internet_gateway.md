---
title: "Using main PC as internet gateway"
date: 2005-10-30
forum: Networking &amp; Wireless
---

### Post by ubuntufella on 2005-10-30
Hello everyone. I am still a Linux newcomer and I have to say if it weren't for Ubuntu I'd still be using Windows. Well, I still do.

Basically, I have 2 network cards in my PC (well I will have if I can pull this off) and I have my PC connected to the modem. What I was hoping to do is to use a cable to connect my (well it's mum's) laptop to the second card in my PC and be able to access the internet. And possibly network the two PCs for file and printer sharing etc. I am confident with the command line, and using apt-get/synaptic and will try to understand and learn from this. Thankyou all in advance.

---

### Post by greenway on 2005-10-30
Start with configuring your NICs (network interfaces) and use a crossover cable to connect your gateway to your mom's laptop. Since your only working with two workstations, I wouldn't go for DHCP (unless you are planning on plugging in more workstations later on) provide the two NICs (one in your own pc and the other one in the laptop) with static ip addresses.

You also need to know if your ISP is providing you with a static ip or a dynamic one, this is the ip your will be using for surfing the internet.

For sharing your internet connection and firewalling I suggest you use an easy to use interface such as firestarter (sudo apt-get install firestarter).

This should get you on your way, goodluck!

-greenway

---

### Post by ubuntufella on 2005-10-30
Thanks! I have to say though, I have a dynamic IP address from my modem, and NAT is turned off, too. So tomorrow or later I will purchase a CAT5 crossover cable and we should get under way. But, I might hold off, I have to repartition my hard drive so that i have more than 249mb free space on my linux ppartition.

Edit: I have used Firestarter in the past, and it disables all of the internet access from my pc. Virtually like unpluggin the cable. Is there a guide that I should follow? I will search other places too.

---

