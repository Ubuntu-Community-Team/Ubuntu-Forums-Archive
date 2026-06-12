---
title: "network xp thru hub thru ubuntu to internet"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by maze1216 on 2007-10-30
Ok so there's alot of posts similar to this but not quite as far as i've seen. I have a laptop with XP pro connected thru a linksys hub to a desktop running dual boot xp pro/ubuntu and a couple other versions of linux that i'm still testing, which is connected to a cable modem thru one of the network cards. i have 3 network cards on my desktop but the onboard one doesn't seem to work, never has. With xp running on the desktop i can connect the laptop to the desktop with either a firewire 1394 cable or thru the network hub to my second ethernet card and either way connects my laptop to the internet and lets me share files. With ubuntu running i can't get either computer to see each other or get onto the internet on the laptop. i've tried the fixes of running "sudo apt-get install openssh-server" and editing the smb.conf file but neither have helped any.  This morning i edited the network card connected to the hub to be a static IP and set up the laptop tcpip settings to the same thing (kind of like a linksys router, "192.168.1.1 - 255.255.255.0 - 192.168.1.2" and that worked to my amazement. for a minute, i went off to set up the background picture and desktop settings (nothing to do with the network) and when i tested the internet on the laptop againit was down and i've gotten nothing from it since. if anyone could help i'd really appreciate it. I know I could do it the easy way an get a router instead of hub but i really want to learn how to run linux as a server, network admin type stuff. I can set up networks on xp all day with no problem but i haven't used linux since the early 90's and I really want to switch back over to it. I work for a computer repair shop and they're thinking of dropping microsoft support and switching all their customers to linux. (yea i talked them into it, not i'm not good enough with linux to pull that off yet.. but soon... : )

---

### Post by dad311 on 2007-10-30
> **maze1216 said:**
> Ok so there's alot of posts similar to this but not quite as far as i've seen. I have a laptop with XP pro connected thru a linksys hub to a desktop running dual boot xp pro/ubuntu and a couple other versions of linux that i'm still testing, which is connected to a cable modem thru one of the network cards. i have 3 network cards on my desktop but the onboard one doesn't seem to work, never has. With xp running on the desktop i can connect the laptop to the desktop with either a firewire 1394 cable or thru the network hub to my second ethernet card and either way connects my laptop to the internet and lets me share files. With ubuntu running i can't get either computer to see each other or get onto the internet on the laptop. i've tried the fixes of running "sudo apt-get install openssh-server" and editing the smb.conf file but neither have helped any.  This morning i edited the network card connected to the hub to be a static IP and set up the laptop tcpip settings to the same thing (kind of like a linksys router, "192.168.1.1 - 255.255.255.0 - 192.168.1.2" and that worked to my amazement. for a minute, i went off to set up the background picture and desktop settings (nothing to do with the network) and when i tested the internet on the laptop againit was down and i've gotten nothing from it since. if anyone could help i'd really appreciate it. I know I could do it the easy way an get a router instead of hub but i really want to learn how to run linux as a server, network admin type stuff. I can set up networks on xp all day with no problem but i haven't used linux since the early 90's and I really want to switch back over to it. I work for a computer repair shop and they're thinking of dropping microsoft support and switching all their customers to linux. (yea i talked them into it, not i'm not good enough with linux to pull that off yet.. but soon... : )

I not sure what you mean by "connect". 

Try setting Ubuntu and all other PCs to dhcp and let Ubuntu pull the network information from the Linksys router.

Write down the IP addresses of each PC in your network and try to ping each PC.

Only after being able to ping all PCs should you continue.

Next goto System>Administration>Shared Folders and enable file sharing and setup your workgroup and shared folders.

If you want to use ssh, then ssh will need to be installed on all Ubuntu PCs.  After installing type "ssh -l <username> <IP address>.

---

### Post by maze1216 on 2007-10-31
ok, you missed the part where i said I don't have a router, just a hub. it's dumb, no information comes from it.... i want my ubuntu to play router, to pass out IP's to any other computer i plug into the hub. by connect i mean get internet to my firefox... or be able to update my programs, or go to an ftp site... i'll explain my exact setup a little better.  i have cable coming in via coax to a modem that supplies 1 IP address. that internet is connected via ethernet to my desktop. which is connected via ethernet to an uplink port on a linksys hub which i can connect up to 4 other PC's to. I have my laptop connected to that via ethernet. Now. the ethernet coming into the desktop connects to ETH-2.  ETH1 is dead and ETH-0 connects to the hub that connects to the laptop. i get no information passed from the laptop to the desktop when i'm in ubuntu.  But, when i boot to windows I run the network setup wizard and tell windows that my desktop connects directly to the internet and all my other computers connect to the internet thru the desktop. at which point i get internet on my desktop and my desktop passes out IPs to anything on the subnet connected to the hub. like my laptop.  I also get the same results connecting my laptop to the desktop with a 1394 cable but lets not get into that since last year when i tried to set up linux with that type of connection everyone told me that it was impossible to use 1394 as a network connection to a laptop (even though i do it with windows all the time)

I can deal with the file sharing not working.... but i need the laptop to get internet. my wife uses the laptop to look things up online all the time and if i'm in linux testing an learning stuff I still need both computers to connect in case she needs to look something up right away.... eth2 is set to dhcp, gets me an IP for ubuntu from the cable modem. now i need to assign eth0 to allow other computers to connect to it and share eth2's internet connection with eth0.... so... the question is, how do i do that... i know it's possible....but how..

---

### Post by maze1216 on 2007-12-20
I'm still needing help with this. why can i share my internet connection thru windows and not thru ubuntu? ubuntu connects to comcasts modem thru eth2. i have another ethernet card that i have connected to a switchbox that i'd like to be able to connect several computers to and have my ubuntu computer act as a router and pass out IP's. like windows will do when you run the network setup wizard and say "this computer connects directly to the internet and all other computers connect to the internet thru this computer".  should i set eth0 to be ipv4 or static IP or what. I have eth2 set to dhcp and that connects my ubuntu system the the internet, if i set it to anything else. it doesn't work. i've tried all the setting to connect the laptop all to no avail. what am I missing????

---

### Post by maze1216 on 2007-12-22
ok, i'll make this simple..... 
linux desktop running ubuntu 7.10 connects to comcast modem via ethernet card 1.
4 port connects to linux desktop via ethernet card 2
XP home connects to linksys 4 port hub via ethernet
XP home can't share files or folders with linux running samba or vise versa.
XP home can't connect to WWW
XP home needs to connect to web.
XP home needs to share folders with linux desktop
How do i make this happen.

---

### Post by nightfrost on 2007-12-23
If I understand you correctly, what you want is a simple internet connection sharing?

There's a lot of information on how to do that scattered across the web, I tried to figure out the same myself not long ago. The problem was I couldn't really understand the "simple" guides, cause I didn't even get what I was looking for. You might be in a similar position. What you need is masquerading (this precise sentence is something I stumbled upon time and time again without understanding it).

Make sure you have this in /etc/sysctl.conf

```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

```
Run "sudo sysctl -p" to update with the new settings.

And then you start the masquerading by something like this:

```
sudo iptables -t nat -A POSTROUTING -o $WAN -j MASQUERADE
```
Where $WAN is the interface that connects you to the outside world (i.e. the internet).

Of course then you might have to set up correct ip addresses and so on for the client (in this case the hub, I guess) and the other interface that connects to it...



Here's for hoping that NetworkManager 0.7 brings easy networksharing a la Windows/Mac... It's really to complicated on linux as it is now :-/

---

