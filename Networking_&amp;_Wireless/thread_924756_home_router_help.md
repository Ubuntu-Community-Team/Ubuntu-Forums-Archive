---
title: "home router help"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by TreeFinger on 2008-09-19
This is what I'd like my setup to be.

Internet > Gentoo Router > Hardware Router > rest of computers in my network.

I am following this: [http://gentoo-wiki.com/HOWTO_setup_a_home-server](http://gentoo-wiki.com/HOWTO_setup_a_home-server)


First thing I did was turn off DHCP on my Hardware Router (Don't have access to a switch).

Going from the Gentoo Router to the Hardware Router I plugged it into the Uplink port. With this configuration I was unable to ping any of the computers on my network, along with the router. If I plugged the Gentoo router into a normal port on the hardware router I was able to ping the other computers but they did not have internet, while the gentoo router did have internet access.

The IPs of the gentoo router and hardware router were not the same throughout this process. What is going on here? Why can't I get that gentoo router to spit out internet to my network?

---

### Post by cariboo on 2008-09-20
If you give your hardware router a static ip address you should be able to connect the inter with the other computers on the network. I have virtually the same setup, except I use two hardware routers. 

My system is like this:

Cable Modem ->crossover cable->Linksys WRT54GS->crossover cable->SMC Barricade->crossover cable->8 port switch.

The Linksys is in the house, it only serves two computers via ethernet cable and wireless. The SMC is in my Garage serves up to 5 computers via ethernet cable plus wireless. the Linksys and the SMC are connected with a crossover ethernet cable via a regular port, the wan port on the SMC is not used. The SMC is setup with a static ip address and dhcp is turned off. The SMC and the 8 port unmanaged switch are connected via a crossover ethernet cable using regualar ports. DHCP is provided by the Linksys router.

The SMC basically just serves as a relay, or access point, and everything works without a hitch.

Jim

---

### Post by TreeFinger on 2008-09-20
> **cariboo907 said:**
> If you give your hardware router a static ip address you should be able to connect the inter with the other computers on the network. I have virtually the same setup, except I use two hardware routers. 

My system is like this:

Cable Modem ->crossover cable->Linksys WRT54GS->crossover cable->SMC Barricade->crossover cable->8 port switch.

The Linksys is in the house, it only serves two computers via ethernet cable and wireless. The SMC is in my Garage serves up to 5 computers via ethernet cable plus wireless. the Linksys and the SMC are connected with a crossover ethernet cable via a regular port, the wan port on the SMC is not used. The SMC is setup with a static ip address and dhcp is turned off. The SMC and the 8 port unmanaged switch are connected via a crossover ethernet cable using regualar ports. DHCP is provided by the Linksys router.

The SMC basically just serves as a relay, or access point, and everything works without a hitch.

Jim

Thank you for the reply. Do you mean under WAN settings I should set it up to be a static IP instead of using DHCP to obtain an IP address?

---

