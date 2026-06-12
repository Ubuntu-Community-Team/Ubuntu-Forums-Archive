---
title: "[SOLVED] Can't SSH- don't know the ip!"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by bcn17 on 2008-09-19
I have a old computer that I installed 8.04 server ubuntu on. I then installed openssh-server. I was able to ssh into it just fine at home. Then I packed up my stuff and went to school. I am now trying to ssh into it but I don't know the ip adress! When I was at home I just looked at my router and it told me the DHCP clients.(dd-wrt v24 sp1) Then I knew the ip address. However, it is not popping up on DHCP clients. I am wondering if this is becasue it isn't logged in. However in order for me to log in (remotely) I need the ip! *I don't have a keyboard or a monitor for it. Just a power cable and Ethernet cable. So i can't log into the machine normally and see if it will pop up on my router.

---

### Post by Dr Small on 2008-09-19
Attempting to login to your SSH server from a remote location relies on many things. First off, is your router forwarding port 22 to the SSH server? Secondly, you don't need the IP address of your box that is behind the router. You need your external IP address.

Dr Small

---

### Post by bcn17 on 2008-09-19
Sorry- I didn't explain well enough- I am remote as in "in the other room remote." The server is plugged into the router and I am through the wireless. So, i don't need to port forward seeing as both computers are on the same side of the router. I just need the internal ip address.eg. 192.168.1.x   In fact I know that my router only leases between 192.168.1.100 and 192.168.1.149.

---

### Post by Iowan on 2008-09-19
Forwarding port 22 (or whatever SSH port you've chosen) might be a bit more difficult for a DHCP client.

[edit] Oops, you type faster...

---

### Post by jcwmoore on 2008-09-19
what router do you have?  different routers provide different ways of viewing the devices connected to them.

---

### Post by bcn17 on 2008-09-19
wrt54GL flashed with dd-wrt v24 sp1-

Is there some sort of tool that will scan the network for all devices and give info like ip, mac, etc. ??

---

### Post by jcwmoore on 2008-09-20
you have a linksys router, right? sorry, but my experience is with a 2wire router and my netgear router.  i could log into them and there was a way to view all the connected devices (machine names and ip address) but i am not sure exactly how to do that with a linksys router, the best i can offer is to point you to a guide to log into your router (and i don't know how good that will be) and hopefully the UI will be easy to navigate and you will find what you need...
[http://www.haxial.com/faq/routerconfig/linksys/]("http://www.haxial.com/faq/routerconfig/linksys/")

---

### Post by bcn17 on 2008-09-20
I understand how to log into my router, it's just that the router isn't noticing the server and showing a "DHCP lease client". I was thinking that maybe because the username and password hadn't been typed in it wasn't registering. However, I can't type in the username and password on the computer physically because I don't have a keyboard for it. I would like to just ssh into it however I don't know the ip. I'm not sure if something is wrong in my logic or if something is malfunctioning but I was thinking some sort of tool that can scan the network would help me find the computer's information so that I can ssh it.

---

### Post by Iowan on 2008-09-20
Try **ping -b 192.168.1.0** or **ping -b 192.168.1.255**.  It won't give absolute results - but will narrow the field to who's playing.

---

### Post by anubhavrocks on 2008-09-20
try this
```
nmap 192.168.1.*
```

---

### Post by bcn17 on 2008-09-20
Thanks for recommending the ping and nmap tools. They are great. I am successfully scanning the network using nmap however I am not seeing the pc I plugged in. My guess is that it is not getting an ip adress because it is not logged in. -I guess I'm just going to need to get a keyboard so that I can type in the user/pass. Then I could try nmap and see if it registers.

---

### Post by TreeFinger on 2008-09-20
> **bcn17 said:**
> Thanks for recommending the ping and nmap tools. They are great. I am successfully scanning the network using nmap however I am not seeing the pc I plugged in. My guess is that it is not getting an ip adress because it is not logged in. -I guess I'm just going to need to get a keyboard so that I can type in the user/pass. Then I could try nmap and see if it registers.


You should set your server to use a static IP.

---

### Post by bcn17 on 2008-09-20
I was looking into doing that and i was having trouble finding a straight forward way- do you have a good solid method of doing it? i ended my search early because I ended up using router with dd-wrt v24 sp1 to set a static ip via the mac adress. So it's like a static dhcp lease.

---

### Post by Iowan on 2008-09-20
> **bcn17 said:**
>  So it's like a static dhcp lease. The static lease is an equally viable (sometimes preferred) alternative to a static address - it allows you to administer server addresses from one location... assuming you have access to that one location.

---

### Post by TreeFinger on 2008-09-21
> **bcn17 said:**
> I was looking into doing that and i was having trouble finding a straight forward way- do you have a good solid method of doing it? i ended my search early because I ended up using router with dd-wrt v24 sp1 to set a static ip via the mac adress. So it's like a static dhcp lease.

Hmm, I have never done it on an ubuntu distro. It is weird because on my gentoo server it is very very simple. I would do some research on it, here is what I found from google: [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

or maybe this?
[http://snipplr.com/view/1737/how-to-set-a-static-ip-in-ubuntu-from-the-shell/](http://snipplr.com/view/1737/how-to-set-a-static-ip-in-ubuntu-from-the-shell/)

I believe you just need to add the following information to your /etc/network/interfaces:

```

#
# The primary network interface
#
auto eth0
iface eth0 inet static
   address 192.168.178.50
   netmask 255.255.255.0
   network 192.168.178.0
   broadcast 192.168.178.255
   gateway 192.168.178.1
   #optional
   #dns-nameserver 102.168.178.1

```

but edit it for your specific network. You must also add your DNS server to /etc/resolv.conf:
```

nameserver ip.address.here.yea

```

---

### Post by bcn17 on 2008-09-30
Thanks for all the help everyone- I managed to get a keyboard- I plugged it in- (without a monitor) typed in my username/password and then my router noticed it an instantly gave it a DHCP lease. From there I was able to set it to a static IP remotley because I could at least ssh it's dynamic IP. So, it seams that:

If it is the first time a server connects to a particular router you need a keyboard to physically log into the server to make it be "registered" with the router.

Then unplug the keyboard and next time you turn the server on without logging on it should listen for the ssh port and you can ssh it because you know the ip. :)

---

