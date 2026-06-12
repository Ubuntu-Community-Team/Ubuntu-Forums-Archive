---
title: "Static IP Behind a Router"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by fmonjaraz on 2008-06-26
I am trying to set up a computer at home that I can connect to from anywhere.  It is connected to a router hooked to a cable modem.  I want a static ip for that computer and for any other computer I connect to that router. I already have an account from DynDns.com which I hear is where to start.

---

### Post by spd106 on 2008-06-26
You need to open System -> Admin -> Network in order to turn roaming mode off and configure the settings manually. 

It's usually a good idea to set the IP address to one outside the range covered by your DHCP server (router/modem) to avoid conflicts. But remember to keep it in the same subnet.

As an example if your router is at 192.168.1.1 and provides addresses in the range 192.168.1.2 - 192.168.1.100, then you could choose to set your server to 192.168.1.101 with the same netmask of 255.255.255.0.

If your router supports dynamic dns then you'll just need to forward the ports you want to open to the address you've just set-up. If not then you'll need still need to forward the ports, but you'll also need a dynamic dns client on the server. See [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by superprash2003 on 2008-06-26
> connect to from anywhere
do you mean like remotely accessing the desktop?remote desktop?

---

### Post by fmonjaraz on 2008-06-27
Not necessarily the Desktop, ssh would be fine, but yes remotely...

---

### Post by superprash2003 on 2008-06-27
have you installed ssh already? have you tried accessing by your external ip ( get ip info from [www.whatismyip.com](www.whatismyip.com))..

---

### Post by fmonjaraz on 2008-06-27
My Router stopped working (dl-604), I need to get on a windows machine to update the firmware or buy another router.  Is their any specific router that is recommended for setting up a server or for linux??

---

### Post by kpkeerthi on 2008-06-27
The best thing to do, IMO, is to remain in roaming mode (DHCP assigned IP) and configure your router to return a 'fixed' IP for your host based on mac address of the host. Very handy for laptops, expecially when you carry it around or to the cafes so you don't have to switch between DHCP and static mode.

---

### Post by fmonjaraz on 2008-06-29
How do I port-forward??

---

### Post by superprash2003 on 2008-06-30
the steps differ slightly from modem to modem.. try finding your router model no here to port forward [http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

---

### Post by fmonjaraz on 2008-07-01
I ssh-ed the result from whatsmyip.com and it connected me to my desktop.  I did this from my wireless laptop...

---

### Post by fmonjaraz on 2008-07-01
I am able to connect to my desktop using the DynDns service and the IP, but I also want to be able to connect to another machine that is connected to the router such as my laptop..

---

### Post by kevmitch on 2008-07-01
You can tell your router to also forward an other port other than 22 to port 22 on the ip address you give your laptop. Then, you would
ssh -p <port> <your dyndns name> to get to the laptop.

A less sophisticated way to do it, but one that requires no additional configuration is to ssh into your desktop and from there, ssh to the local ip of your laptop.

---

### Post by fmonjaraz on 2008-07-02
Since I can access my Desktop with my DynDns adress using 

sudo ssh [email]username@dyndns.com[/email], I can access any other computer connected to

that router by ssh-ing into my desktop then ssh-ing into my laptop.  AKA

connect to laptop via desktop.  I think this is sufficient.  Thank You!!!

---

