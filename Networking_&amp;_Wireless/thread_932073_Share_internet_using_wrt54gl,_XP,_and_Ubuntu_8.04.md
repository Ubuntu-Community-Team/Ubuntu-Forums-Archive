---
title: "Share internet using wrt54gl, XP, and Ubuntu 8.04"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by Ubuk2008 on 2008-09-28
hi guys, I'd really appreciate it if you guys can help me with this. So I have a wrt54GL linksys router running DHCP on a XP SP2 machine. I installed 8.04 ubu on another machine. I connected the network cable from Ubuntu machine to the router. Now all I want to do is to surf the net on both machines and I have no idea how to go about doing that. I don't know what gateway, dns, proxy are...but I do know that if i type in 192.168.2.1 into the url bar, I can access the router setup page. 

Please help?

---

### Post by Ubuk2008 on 2008-09-28
Please help?

---

### Post by superprash2003 on 2008-09-28
so is xp set to ICS(internet connection sharing)?? if so, go to the terminal and type ifconfig and post output.. also type ping google.com and post output

---

### Post by Ubuk2008 on 2008-09-28
Thanks for the tip superprash2003. Here`s how I solved it so some others who might come across this problem (in Ubuntu 8.04) will find this helpful:

Assumptions: 

1. You should have Windows XP Pro SP2 setup on your Windows computer
2. Your XP PC is connected to a router and that router is connected to a modem and the modem is connected to a telephone jack (I use DSL)
3. Router is DHCP and modem is NOT
4. You have your Ubuntu PC connected to your router through a crossover network cable

Solution:

1. Find out your ROUTERS IP. It should be something like 192.168.x.x
2. type it in your browser on your XP PC
3. Find out the DNS servers that is listed in the routing info. I have a Linksys WRT54GL and once I go to 192.168.x.x and click on `status` button at top, I am able to see my dns servers.
4. In Ubuntu, click on the icon besides the speaker at the top which looks like two computers. In the drop down menu that follows, click on manual configuration
5. Click `wired connection` and go to properties
6. The IP address is something that you can assign. If you have a Linksys WRT54GL try to assign something between 192.168.2.103 to 192.168.2.149
7. Then, press tab and your subnet will be auto populated
8. The gateway is your router`s IP. So you`ll put in 192.168.x.x which is from step 1 above where you had to find your routers IP. Normally this can be done on XP by going to Start, Run, type in `cmd`, then type `ipconfig`
9. a line should read `gateway` and it will have an IP number. That is your router`s IP assuming your router is DHCP
10.take that number and type it in your gateway field for Ubuntu properties for wired connection
11.then click OK and then go to the tab that says `DNS`
12.then add the DNS you found from step 3, save everything, click ok, restart, and it should work

I`m no IT tech so my terminology and method may seem quite brutal and unsystematic, but I hope it is helpful. Please correct it as you see fit.

Cheers!

---

