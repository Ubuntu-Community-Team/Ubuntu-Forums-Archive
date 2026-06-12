---
title: "trouble in setting up the network"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by ryansdistrict on 2008-04-05
Hi guys 
its my first hour using Ubuntu i am loving it
I got an important thing i was tring get internet on this OS 
how to setup the network on it and get the internet working 
i am sharing internet from another computer i have but i dont know guide me how to fix it on ubuntu (i already entered few IPs but didnt work for me )

 
here are my connection details on windows please can you 
> DHCP Enabled: No
IPv4 IP Address: 222.222.222.222
IPv4 Subnet Mask: 255.255.255.0
IPv4 Default Gateway: 222.222.222.111
IPv4 DNS Server: 222.222.222.111
IPv4 WINS Server: 
NetBIOS over Tcpip Enabled: Yes


Please can you tell me how to fix the internet on ubuntu knowing these are my details ?
i got wireless network

another issue i know about Wine  the program that runs .exe files
i downloaded it but i dont know how to install it ( its a ziped package)
Where to install such packages ?

Thank you :):)

---

### Post by m60dude5 on 2008-04-05
Ok. First things first, you have to find out if your wireless card is recognized. To do this, go to Systems, Administration, Hardware Info. (It might be systems, preferences, but try both). Once you click that, try to find the section for wireless cards or network adapter. Then look at the right panel and see if it names your card. If so, its recognized. Let me know if it is or not, and then I'll tell you what to do next.

---

### Post by m60dude5 on 2008-04-05
About WINE, look at this guide to help you extract the tarball to the right directry.
[HERE]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by ryansdistrict on 2008-04-05
> **m60dude5 said:**
> Ok. First things first, you have to find out if your wireless card is recognized. To do this, go to Systems, Administration, Hardware Info. (It might be systems, preferences, but try both). Once you click that, try to find the section for wireless cards or network adapter. Then look at the right panel and see if it names your card. If so, its recognized. Let me know if it is or not, and then I'll tell you what to do next.

yes i found it 
it recognizes my network card
what should i do next

---

### Post by superprash2003 on 2008-04-06
try this - go to system->administration->network .. click on properties and enter ip as 222.222.222.223 (since 222.222.222.222 is the gateway ip, your windows machine)..and set gateway ip to 222.222.222.222 ..
  also have you enabled ICS in windows?

---

### Post by superprash2003 on 2008-04-06
also go to the terminal and type ping google.com and post results here

---

### Post by ryansdistrict on 2008-04-06
what is ICS in windows?

---

### Post by m60dude5 on 2008-04-06
Sorry for the delay, I've been away for a while. Anyway, its good that it recognizes your card. That saves a lot of trouble later. To continue, we need to know some info. I will list what you need to know, and if needed, how to find it.
1. Your local, network IP address. It is almost always 192.168.1.XX. For example, mine is 192.168.1.11. To find it, you may need to open your router settings and see which IP's you assign to your computers.
2. Your router's ip address, again, usually 192.168.1.1, but check because it may be different.
3. You subnet mask, usually 255.255.something.xxx.

Let me know the answers to those questions and we can start setting them up in the network settings. 
One more question, when you click the computers, is your wireless network listed?
See the screenshot and I'll show you what I mean.

---

### Post by ryansdistrict on 2008-04-06
actualy my old window details were 
IPv4 IP Address: 222.222.222.222
IPv4 Subnet Mask: 255.255.255.0
IPv4 Default Gateway: 222.222.222.111
IPv4 DNS Server: 222.222.222.111


i can find my wirless network nearby like the picture

---

### Post by ryansdistrict on 2008-04-06
by the way how to find the router details
are they differant than the details i gave u

---

### Post by m60dude5 on 2008-04-06
Yes, they should be different than that, but I'm not sure. To find out, do the following:
On a computer with access to the internet and the network, i.e. a windows computer, type
192.168.1.1 in the url bar. Do you get a box asking for a password and username? If so, good. If not, type:
222.222.222.111 in the url bar. See which one gets you the box. Which ever one does, that's the network ip address set. Let me know which one works.
The reason we have to go through this is because it's imperative to know your ip and the router's ip in order to set up the network in the next step.
It's good that you can see your network in the menu like I showed you. Have you tried clicking your network name to see if that would connect you?
If you're sure that's your network info, then we can move on, but its helps to know before hand. Good luck and let me know.

---

### Post by ryansdistrict on 2008-05-02
ok the first one when i entered it in my firefox it timed out 222.222.222.111 for both
when i runned it via run \\IP nothing happened
but what i know is that this computer which got the internet on ip is 222.222.222.111 and i want to share its internet to ubonto laptop
whem i runed 192.168.1.1 i said it doesnt exist 

by the way when i enter other networks i put the config automatic the internet works fine but for me at home its not working \

----------------
today i tried to put it on roaming
i were able to connect to the network but no internet 
(how can i enter shared files on the network to check if i can see other computer on the network from ubunto)

---

### Post by ryansdistrict on 2008-05-07
anyone

---

