---
title: "Port Forwarding Issue (Minecraft server seen locally but not externally)"
date: 2014-02-05
forum: Networking &amp; Wireless
---

### Post by AdeJczr on 2014-02-05
I have a Minecraft server running on Ubuntu Server 12.04 and am having problems connecting to it. Here's what I have done so far:
[LIST]
[*]I have setup my Netgear router to forward TCP traffic to port 25565 on 192.168.1.4 (server).
[*]I have enabled ipv4 forwarding using the sysctl command and
[*]have opened port 25565 in ufw.
[/LIST]

I can connect to the MC server via my LAN, but I cannot connect to it remotely. 
[B]
NOTE[/B]: I haven't actually had a MC client on a remote machine to test the direct connection. When I use an online port scanner, port 25565 shows that it is closed since the packets are being FILTERED (eg firewall). I have allowed traffic to the port through ufw, so I dont know what is going on. 

HALP

---EDIT---
Is there something Linux specific that I am missing? Maybe im missing an iptables/ufw rule? Ive followed numerous guides to set up the server, but nothing. Also, ive heard of a program called Active Port Forwarder ([http://freecode.com/projects/actfor](http://freecode.com/projects/actfor)) that helped the guy out in this thread ([http://ubuntuforums.org/showthread.php?t=1913507](http://ubuntuforums.org/showthread.php?t=1913507)), but I dont think i need it since my server has internet access

---

### Post by fdrake on 2014-02-05
on the Netgear router try changing the forwarding from TCP to Both and check if that solves it . Also you must have a static ip

---

### Post by AdeJczr on 2014-02-05
I believe I had the router set to handle both TCP and UDP traffic and had the same issue. I'll double check when I get home. Also, my server has a static internal IP

---

### Post by AdeJczr on 2014-02-05
Just checked and confirmed that the router is set to forward TCP and UDP traffic.

---

### Post by Michael_A_Garner on 2014-02-05
Sometimes a reboot of the router can fix port forwarding issues. Oftentimes the setting is 'saved', but won't go into effect until after a reboot. Maybe you have already done that idk, but another thing to look into is you port config again. Do you have the ability to configure a start and end port range? Or do you have just external and internal port configuration? I would make sure that you have both the external and internal ports the same and routing to your specific server machine. It won't be enough to allow the incoming port you also have to tell it which port to use once it is in and where to go.

---

### Post by AdeJczr on 2014-02-06
I rebooted the router (hadn't tried that yet) and still nothing. The router has options for start and end ports, both of which are pointed to 25565. The "Server" field has my server's ip, 192.168.1.4 Here's a view of the port forward screen:


  [TABLE="width: 100%"]
[TR]
[TD="colspan: 2"][h=1]Ports - Custom Services[/h][/TD]
[/TR]
[TR]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2"][TABLE="width: 100%"]
[TR]
[TD="width: 37%"]Service Name[/TD]
[TD="width: 63%"][/TD]
[/TR]
[TR]
[TD="width: 37%"]Service Type[/TD]
[TD="width: 63%"] 				                TCP/UDP 				                TCP 				                UDP[/TD]
[/TR]
[TR]
[TD="width: 37%"]Starting Port[/TD]
[TD="width: 63%"](1~65535)[/TD]
[/TR]
[TR]
[TD="width: 37%"]Ending Port[/TD]
[TD="width: 63%"](1~65535)[/TD]
[/TR]
[TR]
[TD="width: 37%"]Server IP Address[/TD]
[TD="width: 63%"]. . . [/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD="colspan: 2"] [/TD]
[/TR]
[TR]
[TD="colspan: 2, align: center"] [/TD]
[/TR]
[/TABLE]

We're close. I can feel it

---

### Post by AdeJczr on 2014-02-06
I may have figured it out. I just realized that my ISP gave me a fancy modem with routing/wireless capabilities. My wireless Netgear router is behind this modem. Perhaps there are firewall/port forwarding settings already set up on the modem that are dropping packets before they reach the netgear. Ill get in touch with my ISP to get the login for the modem

---

### Post by AdeJczr on 2014-02-06
Turns out my modem was not set to forward traffic to my wireless router. Works now!

---

### Post by fdrake on 2014-02-07
congrats. Can you mark the thread as "Solved" please!

---

