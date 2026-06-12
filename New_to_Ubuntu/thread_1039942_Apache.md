---
title: "Apache"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Pakia on 2009-01-15
I have a dedicated ip from my ISP 203.xxx.xxx.xxx
I have set my router to subnet 10.1.1.1
Subnet mask 255.0.0.0
I connect to the subnet with a static ip 10.1.1.13 via wireless on a acer laptop
The machine i am running the apache server on is connected to the laptop via cable as it does not have wireless
Here I created another subnet 192.168.1.100 on the laptop and 192.168.1.103 on the desktop connected via cable.
(this was all done due to the router being to far from the desktop to lay a cable)
My router has port forward for the laptop and the laptop to the desktop  port 80

I have set up 3 virtualhosts on the desktop (192.168.1.103) via webmin
If I type in my browser localhost I get index of/ (nothing listed)
If I type in the desktop Ip 192.168.1.103 all virtualhosts are listed

If i type in one of the domain names of the virtualhosts either with www or without in the browser my dns (open dns) cannot find it

Any suggestions would be helpful:confused:

---

### Post by ken22 on 2009-01-15
I think you can't resolve the dns because you are behind the static address your ISP gave you. Please try your static IP 203.xxx.xxx.xxx from a computer outside of your network i.e. work or someone else's house.

I assume when you're typing in to the browser you are on the desktop. Is this correct?

---

