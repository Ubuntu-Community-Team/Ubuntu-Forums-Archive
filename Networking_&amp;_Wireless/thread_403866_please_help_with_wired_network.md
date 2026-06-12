---
title: "please help with wired network"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by meomike2000 on 2007-04-07
please help me.

I have set up samba server to ba share and a dns server. I can log on to the ubuntu computer from the windows computers.

I use etho0 set up as my internet connection. Uses DHCP from the cable company. works fine

I have set up etho1 with a static ip that is connected to the network.

I use static ip on both of my windows computers.

I have set up my samba server and used bind to bind it to etho1.

all my shares work and i can log onto the ubuntu box from the windows computer and see all my shares and add or remove.
I set it up to use individual profiles per user.

Can somebody help me to get etho0 setup as a shared connection so my windows computers can get to the internet.

I am still new to linux and ubuntu. plz plz plz help.

Thanks in advance,
mike

---

### Post by 0x29a on 2007-04-07
Hi,

This sounds like a routing problem. Since you have two interfaces on you ubuntu box -- etho0 and etho1 -- you have to tell these interfaces where to forward their respective packets. This involves creating static routes. So any packet received on etho1 for the internet at large gets forwarded out etho0. Take a look at this post linked below and let me know if it makes sense. 

[http://ubuntuforums.org/showthread.php?t=113474](http://ubuntuforums.org/showthread.php?t=113474)

I'll be happy to help you interpret that post in greater detail if need be, but seeing that you've configured samba, this shouldn't be much of a challenge. ;-)

Andrew

[Edit]

Here is another great post. It's rather long but contains a lot of great information, and good discussions. 

[http://ubuntuforums.org/showthread.php?t=391312](http://ubuntuforums.org/showthread.php?t=391312)

---

