---
title: "Can't access router, network or internet."
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by Jarbilong on 2006-08-21
I've installed Ubuntu on a pc.
and it just doesnt go on the network.
its connected through a liksys router. but i tried connecting directly to the broadband modem. still didnt work.

i also tried assiging a static ip. didnt work. 

but under network tools  it shows that im recieving packets. 

please help
thanks.

---

### Post by birdbrain on 2006-08-22
1. Does it work on windows?
2. Have you got a firewall stopping the traffic?
3. Have you entered in your DNS numbers into /etc/resolve.conf?
4. Can you access the web interface of your router from linux?

---

### Post by Jarbilong on 2006-08-22
It could access the internet and everything on windows.
I don't have a firewall
My DNS numbers are in there.
And I can't access the web interface of the router.

my network device is RTL-8139/8139C/8139C+

Does ubuntu have problems with that? or is it something else.

---

### Post by RichardSchollar on 2006-08-22
What do you get from typing

sudo ifconfig

into a terminal?

---

### Post by Jarbilong on 2006-08-22
im not going to type it all . 

i get  

eth0 
link encap: ethernet. stuff.
inet address:[my ip address] bcast: 192.168.1.255 mask: 255.255.255.0
RX packets: 310097 

more of that

then another bit saying

lo

link encap: local loopback
inet addr: 127.0.0.1 mask: 255.0.0.0

then a bit more writing

tell me if theres something specific from it you need.

---

### Post by xiko on 2006-08-23
I've had this problem with Dapper x86. My pc is a x64 so I downloaded the x64 version and it just started working.

My guess is that there are some drivers in the x64 version that aren't at the x86 one.

---

### Post by Jarbilong on 2006-08-23
I just installed Suse 10.1 to see if it would fix it .
but has the same problem. so i'm guessing its a problem with linux not liking my network card. :mad: 

unless anyone has any ideas.

---

### Post by declaration on 2006-08-23
I had the same problem. The internet would work on Windows etc but not on Ubuntu.

It might seem like a ridiculous solution but just try it-

turn off your PC and switch it off at the socket on the wall (not on the back of your PC). Also make sure to switch anything else which is connected which is connected to your PC off at the wall.

Then turn back on and boot Ubuntu.

If I run windows, I have to do this every time I then want to boot up Ubuntu. But if I just run Ubuntu then restart and run Ubuntu again it works.

This genuinely works for me and is not too inconvenient so might be worth a try.

---

### Post by Jarbilong on 2006-08-23
> **declaration said:**
> I had the same problem. The internet would work on Windows etc but not on Ubuntu.

It might seem like a ridiculous solution but just try it-

turn off your PC and switch it off at the socket on the wall (not on the back of your PC). Also make sure to switch anything else which is connected which is connected to your PC off at the wall.

Then turn back on and boot Ubuntu.

If I run windows, I have to do this every time I then want to boot up Ubuntu. But if I just run Ubuntu then restart and run Ubuntu again it works.

This genuinely works for me and is not too inconvenient so might be worth a try.

didn't work.

---

### Post by RichardSchollar on 2006-08-24
Have you amended the ipv6 setting in your browser? Open up FireFox and type:

about:config

into the address bar.

Press return and then type ipv6 into the bar that appears.

In the information returned, I think it's the first line that should read a True setting, so if it's False, you need to amend this to True.  

Sorry, rubbish explanation, but this did sort out my internet problems (after I installed a new network card 'cos my nForce 430 wasn't recognised).

Richard

---

### Post by koala114 on 2006-08-24
I have ridiculous solution, just use DHCP.
After you get ip address, issue sudo /etc/init.d/network restart

---

### Post by cat5 on 2006-08-24
Here are a few options to verify:

Ping the router. Do make sure that your router and your IP are within the same network, and have the same netmask, ie: 255.255.255.0 or /24.

- Change the cable..
If you see traffic sent, but not received, or traffic received, but not sent, it's a bad cable.

- after a ping, verify that you see your routers MAC address in the arp table:

```
sudo arp -na
```

Just some simple things to test/try out.

- Cat5

---

