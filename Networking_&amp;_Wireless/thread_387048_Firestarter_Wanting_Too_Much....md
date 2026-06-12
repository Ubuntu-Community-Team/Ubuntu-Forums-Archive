---
title: "Firestarter Wanting Too Much..."
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by ComputerGuy56 on 2007-03-17
I'm trying to use the Share Internet Connection thing from Firestarter. I went on the website, read everything, tried it. (I have two Ethernet Cards)I set eth1 to the IP Address 192.168.0.1 then Subnet Mask 255.255.255.0, and Default Gateway to Nothing. I restarted my computer and even my eth0 didn't have a Internet connection. My usual gateway is 192.168.0.1 so that might mess stuff up. I tried stuff but couldn't think of anything.

---

### Post by Austin_KW on 2007-03-18
You still need your default gateway so that internet traffic will be routed through eth0. So leave the default route to 192.168.0.1 


What you are trying to do is create 2 subnets, then route and foward internet traffic between them.

Your eth0 is on subnet 192.168.0 so you can not use this for the subnet on eth1

Choose a different subnet like 192.168.1 for the subnet on eth1. So eth1 might be 192.168.1.1 and the first PC sharing the connection might be 192.168.1.2 

I think there is an option in firestarter to run a dhcp server to assign addresses on the eth1 subnet. If you assign static addresses then on the first PC sharing the connection you will have to configure it as  (address= 192.168.1.2, mask= 255.255.255.0, default route= this subnet address of the internet computer  192.168.1.1)

---

### Post by ComputerGuy56 on 2007-03-18
Current Info:

My Computer:
eth0: DHCP
eth1: IP 192.168.1.2
Subnet: 255.255.255.0
Gateway: 192.168.1.1

Other Computer: (Windows Computer)
So far running wireless for Internet.
Wired connection:
IP: 192.168.1.3
Subnet: 255.255.255.0
Gateway: 192.168.1.1

My question now is:
How do I get the Windows computer to connect to mine. All the cables are secured but Windows doesn't show any signs of the other computer... I haven't ran any Network Setup Wizards yet. I was hoping somebody would back me up on it. One last thing, Firestarter keeps showing these logs of *"Internal"* IP's. Do I have to allow these IP's? But which one's since there's log 10  of them. The ports they're trying to connect to are Samba(SMB).

---

### Post by Austin_KW on 2007-03-18
Firesstarter default policy is to allow the eth1 subnet to connect to the internet but not to the computer itself. 
If you want to allow samba add a policy rule for inbound traffic to allow traffic from 192.168.1.3 or the network 192.168.1.0/24

---

### Post by ComputerGuy56 on 2007-03-18
So I have to get Ubuntu and Firestarter on the other computer as well JUST to do Internet Connection Sharing through eth1?

---

### Post by Austin_KW on 2007-03-18
no, change the policy on the ubuntu computer, firestarter is blocking samba access to the ubuntu pc

---

### Post by Austin_KW on 2007-03-18
> **ComputerGuy56 said:**
> Current Info:

My Computer:
eth0: DHCP
eth1: IP 192.168.1.2
Subnet: 255.255.255.0
Gateway: 192.168.1.1
this Gateway dont look right to me should be blank, this is saying to route back on eth1

> 
Other Computer: (Windows Computer)
So far running wireless for Internet.
Wired connection:
IP: 192.168.1.3
Subnet: 255.255.255.0
Gateway: 192.168.1.1
this Gateway should be eth1 192.168.1.2

---

### Post by ComputerGuy56 on 2007-03-19
I don't know what else to do. My Windows computer keeps saying Network Connection Unplugged. Here is the info:
Ubuntu Computer:
eth0: DHCP
eth1:
IP: 192.168.1.2
Subnet 255.255.255.0
Gateway: 

Windows Computer:
Wired Connection:
IP: 192.168.1.3
Subnet: 255.255.255.0
Gateway: 192.168.1.2

Ubuntu Computer, opened Samba Port, Allowed Connections From 192.168.1.3
Windows Computer, allowed connections to 192.168.1.2

---

### Post by Austin_KW on 2007-03-19
Unplugged?/
Are these computers connected via a switch or directly? If directly are you using a path or crossover cable?
But, I thought you were getting traffic across this link and firestarter rules were dropping & logging the samba traffic?

---

### Post by ComputerGuy56 on 2007-03-19
I'm using a Ethernet Cable. Don't know anything about crossover cables. And it is a direct connection.

---

### Post by Austin_KW on 2007-03-19
It is probably a patch or straight thru' cable. You probable need a crossover cable so that the transmit pair on one end is crossed to the receive pair on the other end. I dont think any PC  ethernet adapters do auto MDI-X (crossover).

But I thought that firestarter was showing dropped samba trafic in the logs

---

### Post by ComputerGuy56 on 2007-03-19
Oh, I don't have a crossover cable then. I'll look at places to buy one.

---

### Post by ComputerGuy56 on 2007-03-25
I found a dusty WRK54G V1.1 Router with four port switch at home. I'm hoping now I would be able to do the Internet Connection Sharing thing. Can anybody guide me through the WHOLE process. I'm stumped.(Not stupid, stumped.)
For the internal computers, I would have to use 192.168.1.100-192.168.1.254 because that's the way the router's set up. The wireless is disabled in the WRK54G because my main Internet gateway has a wireless thing. And is my eth1 supposed to go into the Internet port of the router or a computer port 1-4?

---

### Post by ComputerGuy56 on 2007-03-25
Any help?

---

### Post by dmizer on 2007-03-25
if you've purchased a router, why are you still trying to do internet connection sharing?  your router is going to have a better firewall than firestarter anyway.

configure your network like so:

dsl/cable modem -> router -> computers.

this will eliminate the need for internet connection sharing which is (at best) an undesirable network configuration.

---

### Post by ComputerGuy56 on 2007-03-25
You do have a point I guess. It would be pretty confusing though.

---

### Post by dmizer on 2007-03-26
in what way would it be confusing?

there's nothing to set up in such a configuration.  plug the cables in and go.  you don't have to install drivers, tweak firestarter or anything.

connect ethernet cable (regular ethernet cable) from the modem to the "internet" slot in the router, and connect ethernet cables (again ... regular ethernet cables) from the router to each computer, and off you go.  both computers will then be able to be online at the same time.

---

### Post by ComputerGuy56 on 2007-03-26
The whole story is that I don't use a modem, I use a Gateway. Much difference. It's like connecting two totally different routers. I got them working after about 1 hour.... So stop saying I have a modem. But it's solved now.

---

### Post by dannyboy79 on 2007-03-26
could you please explain how you got this working. whenever you solve something it's always beneficial for all of us for you to provide the way you solved so that another individual doesn't have to go through what you just went thru. could you explain what your gateway does, I think I have the same thing. where does your internet service come from? a cable from the outside? is it a big or small phone plug (that's just what I call them) or is it a coax cable?

---

### Post by ComputerGuy56 on 2007-03-30
Okay, my first Gateway has a wireless and 1 Wired Slot thing. All I did was plug the Internet thing from the Gateway to my router. I disabled the Wireless on my router so it doesn't mess up my other wireless. Though getting the Internet through is sorta weird. I had to run the Router's Disc about 3 times. Then I went into each router's Web Management thing and switched some things.(It would take too long to explain it all) You might encounter problems with port forwarding. I just DMZ'd the Gateway for my Router's IP. Now my router(not Gateway) takes care of all the ports and things.

---

