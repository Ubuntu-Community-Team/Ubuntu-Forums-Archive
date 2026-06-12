---
title: "Can not use Port forwarding"
date: 2014-10-05
forum: Networking &amp; Wireless
---

### Post by john303 on 2014-10-05
Hi everyone,
I want to access to a computer run ubuntu (PC2) from a computer run Windows (PC1), via SSH remotely.
My external IP of PC 2 is pcexaddr, and internal IP is 192.168.0.100. I also config port forwarding for PC2 by the following:
Please view attached file :'bet.JPG'
from PC 1, I use putty ssh , and 
Please view attached file :'b121.JPG'
Host Name is: pcexaddr.
But I can not see PC2, please help me to solve this problem!
Thanks in advance!

---

### Post by Doug S on 2014-10-05
From your description, it is a little difficult to understand your exact situation, at least for me.

Are you running openssh-server on your Ubuntu computer? Example:```
doug@s15:~$ [COLOR=#ff0000]ps aux | grep sshd[/COLOR]
root      1645  0.0  0.0  61364  3060 ?        Ss   Oct04   0:00 [COLOR=#ff0000]/usr/sbin/sshd -D[/COLOR]
root      3037  0.0  0.0 272112  8180 ?        Ss   Oct04   0:00 sshd: doug [priv]
doug      3087  0.0  0.0 272252  3256 ?        S    Oct04   0:03 sshd: doug@pts/0
doug     17622  0.0  0.0  11748   912 pts/0    S+   14:30   0:00 grep --color=auto sshd
```If not, see [here]("https://help.ubuntu.com/14.04/serverguide/openssh-server.html").

---

### Post by Michael_McKenney on 2014-10-05
Are you trying to SSH from inside the network or from outside through your router?  If through the router, you need to setup port forwarding rules on the router for the SSH port to the NAT IP address of your server.

---

### Post by john303 on 2014-10-05
Dear [**[COLOR=#DD4814][B]Doug S**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1245983"),
I still not install ssh server in my PC2, please help me why I have to install it. I also read that I must config NAT rules ? is it my problem?
Thank you.
Dear [**[COLOR=#000000]Michael_McKenney[/COLOR]**]("http://ubuntuforums.org/member.php?u=1945953"),
I have accessed inside the network, now I want to access outside network but I can not do it.
Have I must install any software or set up in linux ?
I'm a newbie so please help me to explain.
Thank you so much

---

### Post by Vladlenin5000 on 2014-10-05
So, if you need access from outside then > you need to setup port forwarding rules **on the router** for the SSH port to the NAT IP address of your server.

---

### Post by Doug S on 2014-10-05
> **john303 said:**
> Dear [**[COLOR=#DD4814][B]Doug S**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1245983"),
I still not install ssh server in my PC2, please help me why I have to install it.If you do not have ssh server, then you can not connect via an ssh client (i.e. PuTTY). However...> **john303 said:**
> I have accessed inside the network, now I want to access outside network but I can not do it.If you are able to establish an SSH client to / from server connection from within your local area network, then you must be running ssh server already.

---

### Post by john303 on 2014-10-06
So, please tell me what step I must do to access from a outside network (PC1- windows - ssh client) to a internal computer (PC2-ubuntu-SSH server) ?
Thanks so much!

---

### Post by Vladlenin5000 on 2014-10-06
As commented before, NAT is what you need: [http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation) (no, you don't need to understand everything in that page, just the basic concept).
Setting it up depends on the router make/model you have but generally you should be looking for NAT or port forwarding at the router's settings page. Being there just create a new rule or rules to **open **the required port(s) and direct any external request made to the specific port(s) to the internal IP of the machine you want access to. By default and for your safety, all except the common ports and the ports required by apps supporting UPnP - the router must support it as well - are closed.
This setup allows any connection to your external (public) IP, the one given by your ISP (usually dynamic and as such it'll change sooner or later), to be redirected to one (and only one) of your internal IPs, like 192.168.0.100 in your example.

---

### Post by Michael_McKenney on 2014-10-06
Most home routers use NAT internally.  NAT is a private address range that is not routable on the internet.  You want to use SSH.  On the router of the computer you want to access you have to setup port forwarding rules.  I have my Ubuntu web server at home.  In order to access it I had to do two things.

On Godaddy's site, I had to setup a URL of [www.scsiraidguru.com]("http://www.scsiraidguru.com") and [www.michaelmckenney.com]("http://www.michaelmckenney.com").  Under that I added www entry for the IP address of the WAN side of my router.   This is the DNS entries for the URLs.   On my router, I went into the port forwarding table and said port 80 goes to the IP address of my Ubuntu web site workstation.   SSH is port 22.  You will need to port forward 22 to the IP of your computer.   You will also need the WAN address of your router.   This address is what you will SSH.  You connect to your router and it port forwards you to your computer.

---

### Post by Vladlenin5000 on 2014-10-06
NAT is the method to access it, SSH is the network protocol.
No need to add a layer of complexity and difficulty. The OP won't probably need Godaddy anyway.

The main point is as long as one can ssh into other machine from inside the home network, access from the outside depends only on the home router being properly setup to explicitly allow such traffic. NAT "translates" the request directed to the WAN address via a specific port to the PC's internal IP on its home network, 192.168.0.100 in this scenario.

> SSH is port 22.  You will need to port forward 22 to the IP of your  computer.   You will also need the WAN address of your router.   This  address is what you will SSH.  You connect to your router and it port  forwards you to your computer.

^^^^
This, and only this. The home router's settings address is its IP address. In this scenario the typical would be 192.168.0.1. Then login, then find where to add the rule to direct traffic of port 22 to 192.168.0.100. Typically the form for the rule presents a port interval -> enter the same - 22 - on both. Confirm/Save & reboot router. Done!

---

### Post by john303 on 2014-10-07
Thanks everyone for your sharing.
I realized that I still not reboot my router, is it reason for my fault?, I have config port forwarding on my router as the picture. any config in my ubuntu computer ?[ATTACH=CONFIG]257016[/ATTACH]

---

### Post by Michael_McKenney on 2014-10-07
You need to add it and save it and verify you did.  It should not need to be rebooted.  You can test it by using the external WAN IP address of your router with your SSH tool like Putty.  You can check the logs to see if you have any errors on your router.

---

### Post by Vladlenin5000 on 2014-10-07
A reboot is in order each time you change such settings in a router. No further settings in the PCs required. Again, this assumes you can already connect one from another in your home network. Setting up the port forwarding rule should be enough to also access it from outside (Remember: Always use/connect to the WAN IP, not the internal one you use to connect at home).

---

### Post by john303 on 2014-10-08
Thank everybody for your help!
Much appreciated!
I have reboot my router, It's demonstrate a better status, I have connected to my PC (I check by using a computer in LAN but using a external address of router), but only one time. In the next time, I connect and entering username and then it show a notification "network connection refused". Please give me the reason of my situation.
Thank you so much!
This is my error after a short time since I was connected (attached file)

---

### Post by Doug S on 2014-10-08
> **john303 said:**
> I check by using a computer in LAN but using a external address of routerThat's odd. It has been my past experience, and I tested it again just now on my system, that such a method of test does not work in cases of port forwarding. Of course, your system is different than mine. However, my suggestion is that you test via trying to create a new SSH connection from the WAN.

---

