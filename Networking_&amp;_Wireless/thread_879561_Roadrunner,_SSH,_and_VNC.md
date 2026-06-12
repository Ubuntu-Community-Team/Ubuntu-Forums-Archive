---
title: "Roadrunner, SSH, and VNC"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by wefojoij on 2008-08-04
Hi,
     I have a roadrunner connection at home and 3 PCs running Ubuntu. I would like to connect the roadrunner to a minihub and the hub to each of the PC's ( to share the connection).
     I also want the ability to SSH and then VNC into the main PC. Is this possible and if so how? Are there any step by step guides?

Thanks.

---

### Post by superprash2003 on 2008-08-04
does your connection currently require a dialer?? or do you get internet access as soon as you switch on your modem?

---

### Post by wefojoij on 2008-08-04
thanks
The internet works as soon as modem is switched on.

---

### Post by superprash2003 on 2008-08-05
connecting to the hub is possible..just like how you said..for ssh,vnc you need to have port 22 and 5900 open.. you would have to open these ports in your modem..

---

### Post by wefojoij on 2008-08-06
Thanks for your reply.
Any guides about how to do this? I am new to this.
Many thanks for the great support.

---

### Post by xc3ll on 2008-08-06
Theres a bunch of guides to help you out.

First of all, I'm guessing that you have a router somewhere in you connection, cuz you need a DHCP server somewhere.  

To open up port 22 find out the IP address of your gateway. Type "route" on any of your boxes. It should be 192.168.1.0 or something.  If you're not sure, you can also do ifconfig.  Your router's will be your IP address will be the same as yours except the last digit will be a 0 (this holds true for almost any normal home setup).

Here's a tutorial for getting started on ssh:

[http://kimmo.suominen.com/docs/ssh/](http://kimmo.suominen.com/docs/ssh/)

I can help you get the vncserver up as well, although I suggest getting help from someone who currently runs a vncserver on ubuntu. I run one on CentOS, and I'm using realVNC's vncserver. You can install it on ubuntu, if you'd like to try it out.

NOTE: Ubuntu comes with a VNC Server built in, but there's a bug that makes it useless in most situations :(

---

### Post by wefojoij on 2008-08-07
Can you provide more details about this bug and how to get around it?

Thanks.

---

### Post by xc3ll on 2008-08-07
As far as I'm aware, there's really no way around it.  You can check it out for yourself, as well as read about other VNC servers here:

[https://help.ubuntu.com/community/VNC#VNC%20Servers](https://help.ubuntu.com/community/VNC#VNC%20Servers)

---

