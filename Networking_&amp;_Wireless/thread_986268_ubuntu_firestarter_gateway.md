---
title: "ubuntu firestarter gateway"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by jamesjeffries1 on 2008-11-18
having some trouble with setting up my ubuntu computer as a gateway. its connected wirelessly to the internet via a router. i now want it to act as a gateway through my wired connection to another computer. the other computer is running puppy linux (very very old).

I have tried using firestarter, I have now got it connected via DHCP with my first pc acting as the dhcp server. however when i tick the share internet button, it says "eth1 is not ready. please check your network device settings and check you are connected to the internet"

any help would be much appreciated
James

---

### Post by aikiwolfie on 2008-11-18
Is Firestarter the right tool for the job? I thought Firestarter was a fire wall?

---

### Post by lifestream on 2008-12-30
How about a BUMP? :P
You can use Firestarter for sharing:
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

I'm following that guide, but I'm having trouble with the DHCP part too. I just don't understand it ^^;;;;;


The other laptop (client) is not connecting to mine.
I forgot how to bring eth1 up, so if somoeone could tell me...
It was something like* ifconfig eth1 up*.

---

### Post by travelinman81 on 2008-12-31
you bring etho up by doing ```
sudo ifconfig eth0 up
```
then run ```
ifconfig
```
to verify it is up.
I have my Ubuntu server acting as an Access Point and router for my network. I am not sure if you have to```
 sudo ifconfig eth0
``` up I usually just get into a limited root session when I am working on my server with ```
sudo -i
```
I have the wireless NIC and wired NIC bridged and then I use DHCP3-server to serve out DHCP address to the other computers on my network that connect wirelessly and wired. Are you using to NICS to do what you are trying to do? I think you have to have to NICS to do that.I have eth1 set to DHCP from my ISP and then br0 is set to assign DHCP leases to the rest of the network I have that all set up with firestarter until I learn more about IPtables.

---

