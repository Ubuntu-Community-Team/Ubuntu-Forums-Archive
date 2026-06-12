---
title: "Static IP on a local machine"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by TheOrangePeanut on 2007-08-01
I'm trying to follow the instructions here ([https://help.ubuntu.com/7.04/server/C/network-configuration.html](https://help.ubuntu.com/7.04/server/C/network-configuration.html)) but I can't get it to work. The contents of /etc/network/interfaces is as follows:

#loopback network interface
auto lo
iface lo inet loopback

#the primary network interface
iface eth0 inet static
............address 192.168.1.105
............netmask 255.255.255.128
............gateway 68.53.129.129

The address is what I want the IP to be, obviously. The netmask and the gateway came straight from my router.

The contents of /etc/resolv.conf are as follows:

search hsd1.ky.comcast.net
nameserver 68.87.68.162
nameserver 68.87.74.162

Those values were already there. I'm not sure what should be in the search line so I can only assume that hsd1.ky.comcast.net is correct. I looked up the primary and secondary DNS servers in my router's config to double check the accuracy, and those are both correct.

I'm a complete newbie to networking, and I'm still not very good with Linux. Can anyone spot what I'm doing wrong? When I look at the DHCP clients table in my router's status software, the Linux PC still shows up as 192.168.1.101, the IP the machine had when it was autoconfigured when I installed the OS.

I'm on Ubuntu Server btw, so recommending programs that are in a GUI probably isn't gonna work :)

---

### Post by palintheus on 2007-08-01
If your router supports it you could set it up to reserve a certain IP address for the MAC address on the machine. This would keep you from having to set up a static IP on your machine.

---

### Post by PaulFr on 2007-08-01
Question time:
1. Do you have a static IP allocated from Comcast, or a dynamic IP address ?
2. Do you have a cable modem, or router, or wireless access point or any other networking device upstream of your Ubuntu Server system ? What make,model,brand ?
3. Assuming you do, what are the IP addresses on that device ?
4. Does that device have a feature of being a DHCP server (i.e. can it serve out IP addresses to downstream systems like your Ubuntu server) ?

General comment: Your gateway has to be reachable directly from your system, i.e. it should be in the same subnet. So for example, a valid entry would be:```
#the primary network interface
iface eth0 inet static
............address 192.168.1.105
............netmask 255.255.255.0
............gateway 192.168.1.1
```This assumes your upstream network device has an **internal** IP address of 192.168.1.1.

**Update** Never mind about the questions, I did not read your post properly :-) Yes, you have DHCP, so the simplest solution is to use as suggested above ```
auto eth0
iface eth0 inet dhcp
``` and then set up your router to always hand out 192.168.1.105 to your ARP address (**ifconfig|grep HW** to find out your ARP address). On the other hand, my example above will also work, if you update your gateway address to the internal IP address of your router (I'm guessing you do not have to change it :-) ).

**Update**: **ifconfig|grep HW** is to find out your MAC address, not ARP address. Thanks splintercellguy.

---

### Post by splintercellguy on 2007-08-01
You mean MAC address. ARP is simply the mechanism to find a MAC address.

---

### Post by TheOrangePeanut on 2007-08-01
*1. Do you have a static IP allocated from Comcast, or a dynamic IP address ?*
Dynamic

*2. Do you have a cable modem, or router, or wireless access point or any other networking device upstream of your Ubuntu Server system ? What make,model,brand ?*
Upstream?  I assume you mean between the internet connection and the ubuntu server.  I'm using a Linksys Wireless G router, model WRT54G.

3. Assuming you do, what are the IP addresses on that device ?
The IP addresses of the machines attached to the router?  I92.168.1.100 - 192.168.1.102 (3 machines)

4. _Does that device have a feature of being a DHCP server (i.e. can it serve out IP addresses to downstream systems like your Ubuntu server) ?_
Under the basic setup tab, I can choose between "Automatic - DHCP" and "Static IP".  The static IP selection requires a static IP issued by the ISP, but like I said, I'm on a dynamic IP connection.

I hope that helps.

---

### Post by TheOrangePeanut on 2007-08-02
I figured it out.  I was about to post something to the effect of "its sort of like it doesn't recognize eth0" when it hit me.  When I ran ifconfig it showed the loopback interface but not eth0.  That's because I removed the line "auto eth0" when I went from "iface eth0 inet static ... gateway 192.168.1.1".

I'd assume that it didn't configure eth0 at all, right?  And since eth0 wasn't available then of course I couldn't do anything with it.

Thanks for the help.

---

