---
title: "Ethernet Cable Unplugged then Plugged in now no internet"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by brian_utd7 on 2008-06-17
Hey, today I unplugged the Ethernet cable on my desktop that is running Ubuntu and now I can't get the wired connection to run again on the computer? Any thoughts?

---

### Post by WSmart on 2008-06-17
You have a router, yes?  You should look at the router configuration and see what it says,the browser interface..  And, or, power down the router for thirty seconds, cycle the power.  Some routers have a sequence they like when you plug in;  you have to wait for the green light and then plug the computer side in, something like that-mine pretty much just works.

Also, you  might need to manually configure the connection in Ubuntu by clicking on the double computer display icon on the menu panel.  Go into the properties section on the wired connection, hit the button, and choose DHCP, if that's the case.

---

### Post by wadesmart on 2008-06-17
I have seen this same problem lately on linksys and ubuntu computers. A linksys router running dhcp allowing only 5 ip's has three WinXP's and two ubuntu fiesty computers connected. The XP's are wireless and the ubuntu are wired. If I unplug the wired ones for say 1 min or more, when I plug them back in they cannot get immediately back on the net. Lease time is usually 12 hours so Im not sure why this is happening. Those IPs arent being assigned to anything else and as far as I can tell, everything is working fine. 

However, if I reboot the Ubuntu machines they receive their ip's and get right online. 

One note: the power went out here recently and my client called worried they couldnt get online. After the power came up, the modem, router and machines came on, booted up and got right online. So I wonder if the IP problem is specifically and only with the ubuntu machines. Since I do not think that this is so - Im still looking for another answer. 


brian_utd7, this is obvious I know but, make sure that the cables are plugged all the way in and have clicked in place. If you are running DHCP make sure you have enough IPs open for your network. And if you are doing any type of security, like mac filtering, make sure you put in the right mac address.

---

### Post by brian_utd7 on 2008-06-17
Hey thanks for the help. I am running a linksys router. I also have 3 other computers running xp or vista and 1 dual booting ubuntu and vista. All of the other computers are up and running fine with the internet on any of the 3 OS's. I have rebooted the desktop numerous times and still no internet. Ubuntu is running fine on my laptop that i have dual booted but i'm connected to my router wirelessly with that computer. I'm not doing any mac filtering or anything like that i only have a wpa key on my network which doesn't effect the wired desktop that is having the problems. Once again thanks for the help.

---

### Post by devils302 on 2008-06-17
> **brian_utd7 said:**
> Hey thanks for the help. I am running a linksys router. I also have 3 other computers running xp or vista and 1 dual booting ubuntu and vista. All of the other computers are up and running fine with the internet on any of the 3 OS's. I have rebooted the desktop numerous times and still no internet. Ubuntu is running fine on my laptop that i have dual booted but i'm connected to my router wirelessly with that computer. I'm not doing any mac filtering or anything like that i only have a wpa key on my network which doesn't effect the wired desktop that is having the problems. Once again thanks for the help.

Depending on what firmware you're running on the router, login and restart the dhcp server (or just unplug the power from it for 30 seconds).

When it's not going in with a cable, check the NIC on your computer (ping 127.0.0.1), change switchports on the router and replace the cable. If a network connection is detected, upon booting or running:

$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 up

Your computer should send a DHCP broadcast across the Ethernet so the DHCP server can hand you an IP address.

---

### Post by brian_utd7 on 2008-06-19
Hey, thanks again for all the help. Somehow I got this all to work. I opened up terminal and then did sudo ifconfig eth0 up and then sudo ifconfig down and was able to get an ip address and connect to the internet only my connection speed was extremely slow. For the next 2 hours I played around with all of the computers I have an they all were extremely slow on the internet as well, it took minutes to load Google. So I went and brought out my router from college plugin it in and set it up and everything is working now. I think it might have been from a power outage that we had had the night before this all happened and that coupled with the unplugging of the ethernet cable really messed things up.

---

