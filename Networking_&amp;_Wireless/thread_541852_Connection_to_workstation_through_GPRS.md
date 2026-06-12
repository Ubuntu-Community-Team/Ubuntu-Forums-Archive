---
title: "Connection to workstation through GPRS"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by rklauco on 2007-09-03
Hallo everyone.
Thanks to how-to I was able to connect with my laptop to internet using GPRS.

I need to be able to connect to the laptop from remote location. The problem is, that the IP address of the connected ppp interface is withing the local range (10.X.X.X).
And, therefore, it is unreachable from the internet.

I read a few months ago a simple how-to for this, but, unfortunately, I am unable to locate it again.
What I'd like to do is to connect the workstation to my home router.
The home router does have a fixed IP address, so I know where to connect.
The how-to I read before was working with virtual interface on the laptop, tunneled (with encryption, probably) to the endpoint (home router in my case). At the endpoint, there was second virtual interface and it was possible to work from each end on the second machine - the transport network seemed to be transparent for the virtual interfaces.

Can anyone, please, point me to some how-to with similiar problematics? I already tried google, but I do not know exactly what to search for, so I am kinda lost in the results :-(

---

### Post by rklauco on 2007-09-03
OK, so I found it directly on [**_Ubuntu help_**]("https://help.ubuntu.com/community/SSH_VPN") ;-)

---

### Post by rklauco on 2007-09-25
So, I need aditional help anyhow :-(
The how-to helped and it works, but, actualy, only using 7.04.
But, on the server I need to connect, there is 6.06.1 LTS version.
And ssh daemon installed is 4.2.
There is no version 4.3 available for the LTS.
Can anyone help me with getting the nevest version od openssh to the server?
Thanks...

---

