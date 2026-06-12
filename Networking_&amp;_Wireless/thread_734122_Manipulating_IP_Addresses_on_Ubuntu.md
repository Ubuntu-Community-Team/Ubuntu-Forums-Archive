---
title: "Manipulating IP Addresses on Ubuntu"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by mohammad_abs on 2008-03-24
I am trying to download a movie with 8 Parts from rapidshare and each time I download 100MB i need to wait for about 95 min. for the next session to be allowed.

Is their a way in Ubuntu to disconnect and connect with a new IP other than the one I had before my first download session.:confused:

---

### Post by seeker1458 on 2008-03-24
I think rapid share references your public IP (assigned by your ISP).  Regardless of what you change you private IP address to, rapid share is gonna see the same address.  Is your public IP static?

---

### Post by mohammad_abs on 2008-03-24
No it is Dynamic but I need to Disconnect and then connect again

---

### Post by mohammad_abs on 2008-03-24
In Windows I simply Disconnect and then Assign A dummy IP to my System Then I Choose "Obtain IP Automatically" And then obtain a new IP To Be Able To Download.

Now I simply "Restart" My Desktop and a new IP is Assigned to me By My ISP and I can download, but it seemed like a lame way to do so if I want to dowload 8 parts i would need 8 "Restarts" or to wait for a whole week

---

### Post by seeker1458 on 2008-03-24
you can reassign a static ipaddress in *nix just like in windows.  Either go to:
system>administration>network. Then select properties for the appropriate network adapter and just assign an ip address.

or 

Configuring Static IP address for your network card

If you want to configure Static IP address you need to edit the /etc/network/interfaces and you need to enter the following lines replace eth0 with your network interface card

you can use whatever editor you want, this example just happen to use vi, personally i like gedit. to use gedit:

```
sudo gedit /etc/network/interfaces
```

```
sudo vi /etc/network/interfaces 
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.3.90
gateway 192.168.3.1
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255
```

---

### Post by mohammad_abs on 2008-03-24
I tried to assign a new IP in the Networking Properties what happend is that have been disconnected fro the Internet and was not able to reconnect:(
 but surprisingly when i "Restarted" my system the net became normal.

how can i "Connect" to the internet by will, the first time i configured my connection was through 

pppoeconf and the connection was automated not like in windows where i actually choose to connect:) can this be done in Ubuntu?

---

### Post by DaV|d on 2008-03-24
To connect:
```
pon dsl-provider
```

To disconnect:
```
poff dsl-provider
```

The default is "dsl-provider". In case it's different, just type either pon or poff in a terminal and pres <tab> twice in succession to get all the different options.

---

