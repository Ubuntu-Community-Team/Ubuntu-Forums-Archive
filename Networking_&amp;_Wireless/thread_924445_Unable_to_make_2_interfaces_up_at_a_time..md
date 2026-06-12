---
title: "Unable to make 2 interfaces up at a time."
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by Prad on 2008-09-19
Hi All,

I have a ubuntu 6.06 system with 2 NIC's.I configured
one interface with private IP and another interface with
public ip.

The problem is when the system is started after a power shutdown,
it is not able to up both the interfaces.The eth1 interface is not
getting up automatically.Interestingly,when I again reboot the system,then it is able to up both the interfaces.The DNS for both the interfaces is different.

Iam using a start up setup script to configure the system instead 
normal interfaces file.I am not able to find out the problem.Is it the problem of the script?

Any help will be greatly appreciated.....


--
Cheers
Paddy

---

### Post by Friek on 2008-09-19
Well, I guess that depends on the contents of your script :)
Why are you using a separate script instead of the regular interfaces way?

---

### Post by Prad on 2008-09-20
Hi,

Thanks for the reply.Basically we installed asterisk based
software on the ubuntu system.The present ubuntu system
doesn't contain any user interface.The software has the GUI
which has setup tab for configuring interfaces.We carry this system
from one place to different networks.

Like we are asking the user to input the values of eth0 and eth1
ip address from GUI and storing them in a file.Later we are running
the setup script passing this file as command line argument.We kept this
script in /etc/init.d/ to automatically configure and add routes during
start up.It is working fine with one interface,but with 2 interfaces,it is
working sometimes and not working sometimes.

If you want i can post the script...

---

### Post by Friek on 2008-09-20
Can you tell me if it is giving any error messages when the interfaces aren't coming up?

---

### Post by Prad on 2008-09-22
nope.I didn't see any.This we noticed recently.We are unable 
to ping the ip configured on eth1.Later we restarted the system
and then the interface was up.Then we monitored and we are facing the same problem.

Cheers
Prad

---

