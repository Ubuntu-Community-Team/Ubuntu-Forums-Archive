---
title: "Monitor mode and Managed mode at same time( two devices)"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by vtechstu on 2008-03-13
Hi,

I searched and couldn't find anything specific to my question so I decided to post. 

On a laptop I want to use the built in wireless card in conjuntion with the ipw3945 driver to monitor.  This works fine on it's own.

On the same laptop I want to use a PCMCIA wireless card to connect to the desired network so that I can still transmit packets out that device.   This also works fine on it's own.

Combining the two is where I run into trouble.  I believe the system is choosing the wrong device when trying to communicate when the onboard card is monitoring.

Is there a special way to do this?  Much appreciated for any help. Thanks


Running Kubuntu Feisty

---

### Post by Paris Heng on 2008-03-13
Hi, I in your situation before. But it seen do not have problems with my Linux box. I have two interface running in two different modes. One is in Master (PCMCIA), one is in Managed (USB). It run very well. But for my case all the two interfaces are external NIC, not the built-in. I think built-in NIC may have little bit conflict when it come to selecting only one card to run.

-------------------------------------------
[http://parisheng.110mb.com/]("http://parisheng.110mb.com/")

---

### Post by vtechstu on 2008-03-13
Thanks for the response.  Yes, I believe I may have had it working at some point but not sure.

I think that the order of the devices in the routing table may have something to do with this.  For this I tried bringing down the devices and back up, in mixed order, with still no luck.  

Can anyone verify how this needs to be done?

Thanks

---

