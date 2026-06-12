---
title: "Can't connect to router or server"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by salmendar on 2013-09-06
I have a server running with a router and i have the static ip. due to some power issues the system and the router reset at the same time. now system used to reset before and the router too many times but now suddenly i cant connect to the router or the server remotely and the connection does not respond. 

Static ip is can be given in case anyone wants to try out

I really need to get this running. all my projects and my friends dev projects are on this server and we all cannot connect. neither does it allow ftp .

---

### Post by ian-weisser on 2013-09-06
Does anyone have physical access to the router, server, and LAN?
Have you tried *all* services provided by the server?

---

### Post by salmendar on 2013-09-07
yes indded i have. the problem i think is that the dmz ip that i provided changed although it was static. that happens in Pakistan in PTCL. it may be because of that. is there any way that i can access the router?

---

### Post by ian-weisser on 2013-09-07
Depends on how you configured it.
For example, if you chose safe settings (no upnp, no WAN login), then only LAN access is possible.

I am a bit confused...
Are you saying that the IP assigned by your upstream provider changed?
Or are you saying that the IP assigned to your LAN server by your router changed?
Or are you saying that your your server and router are the same system? (Then why have a DMZ set up?)

---

### Post by salmendar on 2013-09-09
thats the problem . nothing changed. all are the same.
the ISP has assigned the ip to my router.  182.180.82.4
i have a static ip assigned to my system.   192.168.1.13
the static ip that i assigned to the system is added to the dmz. 192.186.1.13

---

### Post by ian-weisser on 2013-09-09
Does anyone have local access to those systems?
If so, are they turned on? Are they responsive locally?

Could someone have reset your router, wiping out your old dmz config?

---

### Post by salmendar on 2013-09-10
YES THEY DO 
YES THEY ARE
the server is the only one thats not responsive

tried to do that. i have remotely pinged the router(182.180.82.4 remote). it replies back. there is an issue that when i get into the router the ARP does not show the static ip that i have of the server in the list while when i enter the ifconfig of the machine i get the static ip
 shown. the browser of the server(192.168.1.13) shows there.

btw i have the most basic gui package of ubuntu desktop installed through the command

[COLOR=#000000][FONT=Tahoma]sudo aptitude install --without-recommends ubuntu-desktop

i really need to get this running[/FONT][/COLOR]

---

### Post by ian-weisser on 2013-09-10
In your previous post, please edit your IP address to obscure it.

On your server, since you wrote that you have local access to it, please post the entire result of each of the following commands:
```

ping -c 4 8.8.8.8
ip addr
sudo netstat -tulpn
sudo iptables -L

```

ping checks for connectivity from the server to the rest of the internet
ip addr checks that the server's IP address is really what you think it is
netstat checks to see which applications are listening on which ports
iptables lists your firewall rules

Most I-cannot-reach-the-server issues show up on one of those.

---

### Post by salmendar on 2013-09-16
Asked a friend to get to the server mechine and install teamviewer. had to guide him on the phone and even locate it for him. but got the job done

thanking the ubuntu team and specially[URL="http://ubuntuforums.org/member.php?u=1087323"][B][COLOR=#000000]
[/COLOR][/B][/URL][ 						 							 ]("http://ubuntuforums.org/member.php?u=1841707")[**[COLOR=#000000]ian-weisser[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841707") 
for help
THANK YOU all

---

