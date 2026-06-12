---
title: "Another Network Issue Under Samba"
date: 2005-03-26
forum: Networking &amp; Wireless
---

### Post by kkathman on 2005-03-26
I had, in the past under Gnome, set up samba to be able to see all the windows boxes on my network. However, all of a sudden two of the windows boxes arent seen anymore. I havent changed anything, except installed a new desktop, xfce. 

There are actually three windows boxes on my network. Two of those boxes and the Linux box all go through a hub to the router. The third is a wireless connection to the router. Funny thing, is that the only windows box I DO see, is that wireless one.

I havent set up users on any of the windows boxes. The IPs are as follows:

Main Windows box:  192.168.248.103      Not seen   Workgroup = "WORKGROUP"
Wife's Computer:      192.168.248.101     Seen          Workgroup = "WORKGROUP"
Son's Computer:       192.168.248.100     Not Seen   Workgroup = "WORKGROUP"
Linux Box                  192.168.248.110     -                 Workgroup = "WORKGROUP"

interestingly enough, if I go to the Main Windows box, and look at the network, I can see AND peer into the Linux box just fine.

On my Linux box I am using xfsamba as the vehicle to see across the network under samba. I am wondering if this is a bug??  Any way I can find out?

Thanks.

---

