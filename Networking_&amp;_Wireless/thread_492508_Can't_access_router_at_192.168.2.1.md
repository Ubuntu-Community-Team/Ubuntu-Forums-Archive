---
title: "Can't access router at 192.168.2.1"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by juxtaposed on 2007-07-04
Not an ubuntu problem, but I changed some setting in my router (to give it a greater range of IPs I think) and now I can't access the settings at 192.168.2.1. Also no ports seem to be forwarded anymore. I also tried 192.168.0.1 and 192.168.1.1 but neither work. It is a speedstream 6520 router.

Any ideas on how to get it working? Internet access works fine.

---

### Post by ubuntu.daemon on 2007-07-04
hold the reset button for like 20-30 secs and it should go back to default settings

:popcorn:

---

### Post by juxtaposed on 2007-07-04
Would that mess up the wireless network thing? Its not really a network, just one computer is hooked up to the router wirelessly and I remember having to configure something to get it working.

---

### Post by ubuntu.daemon on 2007-07-04
Are you on dsl or cable?? all it would do is just reset all your settings, and you would have to configure your wireless network

---

### Post by juxtaposed on 2007-07-04
DSL.

The only problem is that I am not sure about the wireless thing -  I think the ISP person configured it. I could probably do it, I just don't want to mess something up that I havn't done before :P

---

### Post by ubuntu.daemon on 2007-07-04
lol then call them get your info, bc usually there is an email address/passwd then yo uhave like to put in 2 options and your done configuring, well then your wireless, so call your provider and tell them you want to reset your router and what you will need to do to set it up.  or wait is it a combo router/modem?  if not, like its just a router and your modem connects with and ethernet cable to your router then your fine, you just have to worry about the modem part os the only thing you would need your provider for

---

### Post by juxtaposed on 2007-07-04
I know what the username and password are, and it is a router and modem.

I don't want to call my ISP. I'll just reset it and hope everything works...

---

### Post by cux on 2007-07-04
Maybe the problem is that somehow your router change his ip address. A quick solution to that is to connect a pc to to your router, just as normal to get internet access. When you have internet access, check your DNS ip address. It's very probable that your DNS ip is the same as your router. That's because your router typically will function as a DNS resolver. You can obtain the ip of your DNS with the following command on a shell:

cat /etc/resolv.conf

These command will display the contents of the resolv.conf file, which contains your DNS ip. You will see some line like (the ip will vary):

nameserver 192.168.1.1

That's the ip of your router. Then just go to your regular browser and access your router via his ip address.

Hope it helps.

---

### Post by juxtaposed on 2007-07-05
> **cux said:**
> Maybe the problem is that somehow your router change his ip address. A quick solution to that is to connect a pc to to your router, just as normal to get internet access. When you have internet access, check your DNS ip address. It's very probable that your DNS ip is the same as your router. That's because your router typically will function as a DNS resolver. You can obtain the ip of your DNS with the following command on a shell:

cat /etc/resolv.conf

These command will display the contents of the resolv.conf file, which contains your DNS ip. You will see some line like (the ip will vary):

nameserver 192.168.1.1

That's the ip of your router. Then just go to your regular browser and access your router via his ip address.

Hope it helps.

Thank you very much, that worked =D

It was 172.16.0.254

I went back to the place that I changed and it was "Select your range" and I changed it from "192.168.254.0 / 255.255.255.0" to "172.16.0.0 / 255.255.0.0" hoping that it would give me more different IPs when I changed my IP.

Now I can fix everything, and I now know how to find that in the future. Thanks alot again :)

---

### Post by gunmonkey11 on 2008-04-13
every time i try to get on it asks me to long on any 1 wanna tell me what the user and the password is for  192.168.2.1:)

---

### Post by superprash2003 on 2008-04-13
depends on which router you use!!some standard username and password are
1)username=admin and password=admin
2)username=admin and password=password
3)username=(blank) and password=admin
4)username=admin and password=(blank)

---

