---
title: "VNC, SSH, and my router."
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by ntowakbh on 2008-02-10
I have a computer, that I would like to be able to access remotely.  This computer is connected to a router, which is connected to the internet.  I am having problems with it.

[Note, this is my first time messing with anything like this so please forgive me for using wrong terms, and correct me if I do.]

According to my friend, the reason I can't connect is the router.  I have the IP of the router, and the IP for my computer on the network, however, the computer itself does not have a public IP address.  Is there some way that I could still remotely access it?

Any help received is greatly appreciated and i thank you in advance.

---

### Post by pdub on 2008-02-10
You will need to use NAT or Port Forwarding.

If this is a consumer level router then i likely only supports port forwarding.

You will need to login to your router and find the forwarding section. Then forward port 22 to the IP address of your computer.

There may even be documentation on the router vendors site.

Be careful exposing VNC directly to the Internet. You may wish to tunnel VNC inside of SSH.

---

### Post by ntowakbh on 2008-02-10
> **pdub said:**
> You will need to use NAT or Port Forwarding.

If this is a consumer level router then i likely only supports port forwarding.

You will need to login to your router and find the forwarding section. Then forward port 22 to the IP address of your computer.

There may even be documentation on the router vendors site.

Be careful exposing VNC directly to the Internet. You may wish to tunnel VNC inside of SSH.

I assume that I would want to tunnel through ssh, how would I do that?

---

### Post by The Cog on 2008-02-10
To do it with Putty on windows, see this threada:
[http://ubuntuforums.org/showthread.php?t=11808](http://ubuntuforums.org/showthread.php?t=11808)

To do it with ssh from linux, use this command:
ssh -L 5900:127.0.0.1:5900 user@host
and then VNC to 127.0.0.1.

---

