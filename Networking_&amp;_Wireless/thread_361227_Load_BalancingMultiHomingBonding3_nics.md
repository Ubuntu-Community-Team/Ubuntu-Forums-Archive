---
title: "Load Balancing/MultiHoming/Bonding/3 nics"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by Neo321/genius321 on 2007-02-14
Hi friends,

I am struck with an assignment of optimizing my lan-network's internet speed by load balancing the two ISPs we are using.
Heres the scenario with current settings ::
******************************************************************************************************
1st ISP at 192.168.1.1
2nd ISP at 192.168.1.2
Half of desktops are using 1st ISP as gateway and half are using 2nd as gateway.
Problem --> If one ISP gets down then half of the desktops get disconnected.
******************************************************************************************************

And now heres the assignment ::
******************************************************************************************************
I would like to make a system as a server which will use 3 ethernet cards, two for connecting to two ISPs, and third for distrubuting internet to my network desktops.
This way the system ll decide itself about load balancing of the two ISPs, and if one gets down, the whole network ll be served by the other ISP.
Advantage --> Lets say only one system is running in network, then it should get the speed of both the ISPs, i.e., almost double.
******************************************************************************************************

I know there are hardware options for this like Nexland Pro800, or similar product from D-Link.
But I am not supposed to purchase any hardware, I have to use software based techniques like load balancing, multihoming, multilink, and all.
This is called 'Etherchannel' by Cisco, 'Trunking' by Sun, and 'Bonding' in Linux.
I can shift to any linux distros or in worst case can also shift to win provided it gives gud results(although I know windows wont be able to do that .. ;) )
So far I have tried fedora, suse, ubuntu, knoppix, so distro is not a problem for me, so please recommend me every possible wayout... :)


Please let me know if anyone has tried something like this.

Thanks in advance.

Regards
Rohit

---

