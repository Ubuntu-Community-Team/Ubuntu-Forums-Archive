---
title: "Can not connect to Internet"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by wxm505 on 2006-09-10
Hi guys:

I am new to Dapper. I installed it today and I am using a local Network with static IP address
I set up "Networking" with correct IP addres, Mask and gateway address. As well DNS was set up correctly.
The weird thing is that I can not ping the gateway. For example,
if my IP is 172.16.7.1 and gateway is 172.16.0.1
I can ping 172.16.7.1 but 172.16.0.1

I doublt whether there is anything wrong with the driver of the network adapter. It worked just fine in Hoary.

I am using a Toshiba Satellite A30

Any ideas or what I did wrong?

---

### Post by 0be1 on 2006-09-10
wxm505;

I just posted another topic along the lines of this same problem. Check it out here and see if that helps you or not.

[http://www.ubuntuforums.org/showthread.php?t=254625](http://www.ubuntuforums.org/showthread.php?t=254625)

regards...

0be1

---

### Post by linuxusr50 on 2006-09-10
I can think of a couple of possibilities.

1.   The modem has stopped passing IP traffic.  Usually caused by powersurges or the like.  I have seen several modems maintain a link but lose the ability to pass IP traffic.  You can try to powercycle the modem and in worse case do a 60 second reset on it.  If you try to reset your modem, it will go back to default values and you may need to configure it.  If you are not familiar with the modem and your ISP settngs, then I would not do the reset.

2.   Something has happened to the static route on the ISP end.  Check with someone else on the same ISP and see if they are able to ping the gateway you were assigned.  If they can and you cannot, have the ISP check your static route to make sure nothing altered it.  They should be able to ATM ping your modem from their router to make sure it is responding.

Note: The reason you can ping your static IP is that it lives in your equipment.  The Gateway lives on the first hop router which belongs to the ISP.

---

### Post by Iowan on 2006-09-10
Probably a naive question, but...
Does the gateway need to be in the local subnet mask?

---

### Post by linuxusr50 on 2006-09-10
**Iowan:**

The IP, Subnet Mask, and Gateway are three different pieces of information that should be provided by the IPS when they give you your IP address.

The IP is your distinct address.

The Gateway is your portal to the next hop router (ISP).

The Subnet mask is a number that is assigned by the ISP to 
determine how many Hosts belong to the subnet your are assigned to.

All three item need to be entered exactly as give for the connectiong to work.

You will in addition need to know your ISP's nameservers.  Those should have been given as well but if not they can be found with command line resorces like dig, or you can go to public websites like [http://www.dnsstuff.com](http://www.dnsstuff.com) to obtain them.

---

