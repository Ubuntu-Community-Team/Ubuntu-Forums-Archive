---
title: "eth0 won't connect - possible to reset?"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by KyleYankan on 2008-01-29
Hi everyone,
 I have a few questions I was hoping you could help me with. I have an ubuntu server machine, that ran for a few months, no problem, hooked to a DD-WRT router.

Wel, that router died a few weeks back, and the server's just sat here because it's had no connection. I just got a new router, and set it all up, and now my server won't get an IP from it. I check everything, even working with a static IP (inside the router's range of IP's), and still no connection.

Is it possible to completely and utterly reset your network connections? To a Just-installed state?

---

### Post by CheShA on 2008-01-29
when you connect with a static IP, you say you get no connection - do you mean no internet connection or have you been able to prove that there is no connection to the LAN?  
i.e. can you ping the router's IP address ? IP address of another PC on the LAN? An external IP address (e.g. 216.239.59.104 ) ?   An external site name (e.g. ping [www.google.co.uk](www.google.co.uk))

In orger to get an internet connection you would need to do both:
```
sudo ifconfig eth0 up 192.168.0.1
```
(replace with your static IP)

as well as:
```
sudo route add default gw 192.168.0.250
```
(replace with router's IP)

You might also need to put your router's IP in /etc/resolv.conf in order to get DNS resolution.

---

### Post by Iowan on 2008-01-29
> **KyleYankan said:**
> 
Is it possible to completely and utterly reset your network connections? To a Just-installed state?

Dunno if it's a "just-installed" state, but [this thread]("http://ubuntuforums.org/showthread.php?t=680870n") mentions ```
**sudo ifdown eth0**
``` followed by ```
**sudo ifup eth0**
```

What do you mean by: > a static IP (inside the router's range of IP's) 
If you mean "inside the router's range of DHCP  IP's", you'll either want to set up a static lease or move your static address OUTSIDE the DHCP range (but still inside the subnet).

---

### Post by binary00mind on 2008-01-29
i just installed my Ububtu 2 days ago. I came here for general info/answers. instead i am giving answer myself, but I had a 2 day battle to set it up, the very same settings, You going thru... I did the same thing as previous member mentioned. iv6 tunnel ¨module¨ it helps.the worst thing is if you are connected to the very same router,by wire and air..Here is the wire case..                           the static IP address You can tackle several ways.. the first one is is look into help..it is explained very well and simple to understand..The second is calling Your IP provider for the address to IP...if you have another OS (windows) there is a fantastic utility ¨Lan Calculator" it is a freeware. I can´t say where, did not read all the rules here yet) also eth0 is a first choice connection as an cable thru Ethernet Card..in this case...Look at that help page.and play a little..(restarting each time) the default Gateway is very much connected to the static IP address. .they move by a digit, but in several variables..to much to explain.The key is the mask, which you can reverse sometimes and it works ; example (0.0.0.255)....Formula for a static IP is most of the times=192.168...but after this it complicates it could be 0.1 or 1.0 or 100 or 0.2 etc,,,The Range means the space of addresses 254 of them..1+254=255. that&#347; whyn the mask...but it is not a rule... I Would follow help examples are included there..and cross-referenced them, with the log from the boot..You Find Your answers there...Check if the system assigned a host that look like this ( ::1 ) it is praimarly used in shared firewalls, but list is long,AOL use this fort example  ( in Windows, but the principle is the same)...Also if you have, a TV Modem, plus a router..Reboot them as Well..I hope as a green rookie, I did not go overboard

---

### Post by binary00mind on 2008-01-29
[PHP]I just read my own post and I have got scared, Please do not uninstall iv6 module..If You do not know which one, You will mess it up..iv6 is the next generation of TCP-IP protocole,(it is not new, but new enough) and it could be useful in many different ways. You might lower Your capapbilities as an a Networker..You future packages or even present ones might depend on them..They are very powerful...Thanx [PHP]

---

### Post by shad0w_walker on 2008-01-30
Disabling ipv6 isn't going to have a noticeable impact on your access unless you are directly connecting your computer to an ipv6 network, which there is very very very very very little reason to do. It is something only really needed for the sake of having enough IPs to support the growth of the internet. Internal networks have no use for it and ISPs have rarely switched to it.

---

### Post by binary00mind on 2008-01-30
In principal I agree with You,.but I was not saying about disabling.iv6..¨iv6tunel¨(often it shows under different names) is not the whole iv6.TCP-IP protocol..there are more modules. Believed or not it worked for me..In my case there was a conflict occurring in the system,.Depending what applications I had installed at that time.As a result the IP address could´t get resolved. This is an interesting subject for me. Previously in Win-s, where OS´s heavily depended on iv6.in communication with M-soft home-base, and now here one of the network sniffing packages I am planning to install .





















 As a result the IP address could not be resolved...There could or could not be a conflict, depending what applications, I had installed at the time

---

