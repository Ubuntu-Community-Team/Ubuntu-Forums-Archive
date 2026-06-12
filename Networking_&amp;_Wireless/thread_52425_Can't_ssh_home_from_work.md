---
title: "Can't ssh home from work"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by word_virus on 2005-07-27
Hey, folks!  I've got a teensy network problem that has me mystified and was hoping that someone out there could maybe please tell me what I'm doing wrong.

I'd like to be able to ssh into my home computer from work.

I moved last week, which meant a new ISP and a new dsl modem.  I've got everything plugged in (modem, router, ubuntu box) as so:

my dsl modem's ip: 192.168.1.1  

WRT54G router: 192.168.2.1

/etc/network/interfaces :
auto eth1
iface eth1 inet static
address 192.168.2.60
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1

whatismyip.com lists my current ip address as: 71.48.135.53

I've got the router set to forward port 22 to 192.168.2.60 (my ubuntu box)

Firewall is set to "allow" port 22 for everyone

This worked just peachy with my previous ISP, but for some reason now when I type the whatismyip address (71.48.135.53, for those of you still playing along at home) into Putty I get "Network Error: Connection refused". 

Consulting auth.log shows no attempted connections.

Anyone have any ideas?  I'm sure I'm simply overlooking something, but I don't know what.  Any help would be greatly appreciated!

Thanks!

---

### Post by crispingatiesa on 2005-07-27
I have the same problem, don't know what's happen but I think is some blocked ports in the firewall at work . Check that maybe i'll help.

---

### Post by word_virus on 2005-07-27
Thanks for your reply.  

Looks like the culprit is my Sprint Zyxel modem.  Put my router into the modem's DMZ, will see if that helps.....

---

### Post by skyboy on 2005-07-28
you can try 2 things to see what is the problem:

1 - remove any firewall from your computer
to list the rules $sudo iptables -L -v


2 - create a DMZ (demilitarized zone) on your computer with the router, it will tell if the problem comes from the router or not. Beaware, when you make a DMZ to your computer, all the services are forwarded to your computer, so think security.


hope this helps

---

### Post by word_virus on 2005-07-28
> 
2 - create a DMZ (demilitarized zone) on your computer with the router, it will tell if the problem comes from the router or not. Beaware, when you make a DMZ to your computer, all the services are forwarded to your computer, so think security.


I've gone ahead and put the router into the DMZ, basically a double-NAT setup.  So the modem does NAT, forwards everything to the router, then the router will forward to the pc those services that have been specifically enabled.  Kind of a pain but the best I could do for the time being.  

I've read several posts in other forums about people having luck bridging their Zxyel modems and routers together so they appear as a single device, but I'm gonna give this DMZ setup a try first and see if that does the trick.

Thanks for your reply!

Lucas

---

