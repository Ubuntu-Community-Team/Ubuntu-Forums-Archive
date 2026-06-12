---
title: "view my network"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by soryu on 2009-12-24
how do i view my network?
when i click  network  in (places) i get windows network .i click it to open it,but
get a  unable to mount failed to retrieve share list from server.
 im trying to view what is connecting to my router and allow or block some connections
 i see the wireless  light blinking  but both my  computers are off.:confused:

---

### Post by Morbius1 on 2009-12-24
That's a rather confusing post. I'm assuming that
> im trying to view what is connecting to my router and allow or block some connections
 i see the wireless  light blinking  but both my  computers are off.is a unrelated to this:
> when i click  network  in (places) i get windows network .i click it to open it,but
get a  unable to mount failed to retrieve share list from server.Anyway, please post the output of the following commands:

Open **Terminal**
Type **smbtree**
Type **findsmb**

Also, you might want to temporarily disable the windows firewall to see if the firewall is preventing access. If you're uncomfortable doing that then post the output of the following command from the Terminal

[B]nmap -sT 192.168.0.100/22
[/B][COLOR=Blue][I]Change 192.168.0.100 to the ip address of the Mint box
[/I][/COLOR]

---

### Post by terry_gardener on 2009-12-24
if you think that someone is connected to your wireless network without your knowledge. 

try the following. 

logon to the router. open firefox and enter the ip address of router in the url field and press enter, type in the username and password of router and then find the connected devices section. and compare the ip address and/or hostnames with your computers and you will be able to tell if there is someone else on network.

---

### Post by soryu on 2009-12-24
linux@linux-desktop:~$ smbtree
Enter linux's password: 
linux@linux-desktop:~$ smbtree
Enter linux's password: 
linux@linux-desktop:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
linux@linux-desktop:~$ smbtree
Enter linux's password: 
linux@linux-desktop:~$ 




here it is.

---

### Post by Morbius1 on 2009-12-24
Yikes!

Um.... you don't have a network.

You either:

(1) Don't have Samba installed - or at least at a minimum smbclient

(2) You have firewalls enabled on both machines and they aren't letting anything through.

What about the nmap command. nmap doesn't require samba so does it display any output?

---

### Post by soryu on 2009-12-24
i have this ubuntu and a mac both accesss internet. mac's wireless, ubuntu ethernet.
my router has a built in firewall (says verizon) i enabled ufw in ubuntu yesterday.
don't know about the mac.

---

### Post by soryu on 2009-12-24
> **terry_gardener said:**
> if you think that someone is connected to your wireless network without your knowledge. 

try the following. 

logon to the router. open firefox and enter the ip address of router in the url field and press enter, type in the username and password of router and then find the connected devices section. and compare the ip address and/or hostnames with your computers and you will be able to tell if there is someone else on network.



i just need to get my username and pass. thank's

---

### Post by terry_gardener on 2009-12-24
are you trying to connect both computers together to share files and services. 

or are you trying to find out what computers are connected to the router at a point in time. 

i have noticed that in ubuntu, network function in places only works if there is a shared folder or services(ie printer) on the network. 

i have 2 computers which cant see each other unless i share a folder or service.

if you just want to find out what computers are connect to the router, to see if anyone is connected when they shouldn't be. try what i suggested above.

---

### Post by Morbius1 on 2009-12-24
(1) Turn off ufw and see if you can enable your network. By network I mean your LAN not the internet.

(2) I thought for some reason you were trying to access a Windows machine not a mac. Unless you enabled sharing on your mac you will never see anything from linux.

That last comment about the mac is based on the 2 hours my wife has allowed me access to her new MacBook Pro. :) There's a very good chance I'm wrong about that but I'm clearly not the right person to post on a linux mac networking issue.

Sorry

---

### Post by soryu on 2009-12-24
> **terry_gardener said:**
> are you trying to connect both computers together to share files and services. 

or are you trying to find out what computers are connected to the router at a point in time. 

i have noticed that in ubuntu, network function in places only works if there is a shared folder or services(ie printer) on the network. 

i have 2 computers which cant see each other unless i share a folder or service.

if you just want to find out what computers are connect to the router, to see if anyone is connected when they shouldn't be. try what i suggested above.


correct, connected at one point. 
need to contact verizon. thank's.

---

### Post by soryu on 2009-12-24
> **Morbius1 said:**
> (1) Turn off ufw and see if you can enable your network. By network I mean your LAN not the internet.

(2) I thought for some reason you were trying to access a Windows machine not a mac. Unless you enabled sharing on your mac you will never see anything from linux.

That last comment about the mac is based on the 2 hours my wife has allowed me access to her new MacBook Pro. :) There's a very good chance I'm wrong about that but I'm clearly not the right person to post on a linux mac networking issue.

Sorry



thank's for you're input.

---

