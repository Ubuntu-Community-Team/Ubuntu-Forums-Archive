---
title: "Cannot ping private addressess"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by gedden on 2007-09-21
I have full internet access on both of my computers, 1 laptop(ubuntu) and 1 desktop(xp home) I have tried to set up a vpn session and couldn't connect.So I tried to ping the desktop 198.168.1.100 and didn't receive any packets. Is this a computer config problem or a router issue? any help or nudges in the right direction would be appreciated.

so 
linksys cable modem=linksys wrt54g==laptop( wireless) and desktop(wired)

---

### Post by digen on 2007-09-21
Are you able to ping the Linksys WRT54G ? 

What the network settings on the laptop and the desktop network interfaces ? IP address, subnet mask, default gateway, route etc.

---

### Post by gedden on 2007-09-21
I should have known better and posted more info in my 1st post :redface: anyway 
Desktop: XP home SP2 
ip: 192.168.1.100
Subnet: 255.255.255.0
Default gateway: 192.168.1.1


for the laptop
feisty fawn with ubuntu studio
Wifi on eth1
ip: 192.168.1.101
netmask: 255.255.255.0
Broadcast: 192.168.1.255 (this one is new to me. Im a wifi/linux/networking newbie) 


Router
login: DHCP
subnet mask: 255.255.254.0 (hmmm never noticed this)
default gateway: 67.162.142.1
Comcast internet.

I am attempting to use RealVNC to remotely control my windows box from my laptop, in the other room. As far as I know this is the only way to do remote desktop on XP home. All the online sources I found told me to set a custom rule on the router to port map 5900 to my windows box, but at this time I have no need to access my XP box from outside my LAN.

Thanks for the help!

andy

---

### Post by spd106 on 2007-09-21
This sounds more like a firewall issue. Do you have a software/personal firewall on the Windows PC? You will have to check that it isn't dropping the packets and perhaps allow your LAN/subnet access. Have you tried pinging both ways?

I have not tried RealVNC, but I know TightVNC works.
[http://www.tightvnc.com/](http://www.tightvnc.com/)

---

### Post by Synflux on 2007-09-21
Hi,
> **gedden said:**
> So I tried to ping the desktop 198.168.1.100 and didn't receive any packets. 
I'm guessing that 198 was a typo in this post and you actually tried to ping 192.168.1.100?

> **gedden said:**
> Is this a computer config problem or a router issue? 
It's a computer problem (assuming both computers are correctly connected to the router which they must be if you're getting internet access on them both), in your scenario the router is just being used a switch .

As spd106 suggested the most likely reason for this is a firewall, either on the xp machine or the packets are being blocked on their way back to your laptop (less likely).

If you are using the built-in xp firewall then try these steps:

1) Click Start
2) Control Panel
3) In the top-left hand corner click on 'switch to classic view' (if it says 'switch to category view' then leave it as it is)
4) Double click 'Windows Firewall'
5) Click the Exceptions tab.
6) Click Add Port
7) Type in whatever name you like, something like 'vnc' would make sense I guess.
8 ) In the port number box type 5900 (this is the default vnc port, you can change it if you like)
9) Leave tcp selected and click 'Change Scope'
10) Choose 'My Network (subnet) only' and press OK twice.

For ping to work:
11) Click the Advanced tab
12) Click the Settings button in the ICMP section
13) Ensure that 'Allow incoming echo request' is ticked 
13) Press OK
14) Press Ok

And then try again. If you're using a third party firewall like Norton or Mcaffee then you'll need to dig around in the settings. Either way, if you wanted to confirm that was the problem, you could disable the firewall for 5 minutes to test it.

Hope that helps. :)

---

