---
title: "Shows connection but no page"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by Lord Funzo on 2007-08-16
I have just installed ubuntu, dual booted with vista.  I have a philips freevents computer with a realtek wireless card, the wirless connection is displayed but firefox just says "problem loading page", i cannot even get onto my router setup page with it.  Im sure it is probably just a checkbox somewere preventing it from working, can anyone help??

  Thanks
        Nick.

p.s. there is no encryption on the router.

---

### Post by chriscando on 2007-08-16
Could it be that you are connected to another router and not yours?
Verify by checking the essid with:
```
iwconfig
```

If you are indeed connected to your router, check for an IP address with
```
ifconfig
```

If you do not have an IP
```
sudo dhclient {your wireless interface: eth0, eth1...}
```

If its still not working, post back and well go from there

---

### Post by Lord Funzo on 2007-08-16
ok i sarted with iwconfig

ra0 --this came up with my network

eth0 -- no wirless extensions

lo -- no wireless extensions


next i did ifcofig

eth0-- link encap: ethernet HWaddr ........ ...(addresses)
UP BROADCAST RUNNING MULTICAST ....... .....(addresses)

sudo dhclient........

all it says is "error while getting interface flages: no such device"

over and over.

---

### Post by chriscando on 2007-08-16
Looks like your wireless interface is on ra0, as from iwconfig.
Does an IP address come up when you
```
ifconfig ra0
```

Also are you using dhclient with an argument? Since your wireless interface is on ra0, try
```
sudo dhclient ra0
```

This requests the router for an IP if you do not have one.

Another thing, it looks like from your last post that eth0 was listed as having an IP, is that correct? If you don't have an ethernet cable plugged in you should not have an IP listed there. That could be the problem. Sometimes when I would go from wired to wireless my arp table would still send traffic out on my wired interface even though it was unplugged, so my wireless connection was up but I wouldn't be using it.

You can verify this by typing:
```
arp
```

If you see an entry for eth0 (most likely your wired interface) and ra0 then bring down your wired interface with
```
sudo ifdown eth0
```

hope this helps

---

### Post by walkerk on 2007-08-16
```
iwlist scanning
```

do you see the specifics of your network?

also, what kind of wireless nic do you have?
```
lshw -C network
```

---

### Post by Lord Funzo on 2007-08-16
nothing relavent cam up on any of those requests apart from the iwlist scanning which listed my wirless network details.  Is there any command i can input to pull up the interface cards description??

---

### Post by Lord Funzo on 2007-08-16
never mind, i am online somehow, thanks alot you guy's, it must have been one of your commands that did it, thank you, i have been on this all day, thanks alot both of you!!

---

### Post by walkerk on 2007-08-16
Perhaps chriscando's ( sudo dhclient ra0 ) did the trick.

Next time its not working do the following in terminal to restart your network interface (this might help as some wireless cards, ralink and others require an ifup):
```
sudo /etc/init.d/networking restart
```

This will do an ifdown, iwup, dchclient.. the necessary steps. :)

---

### Post by Lord Funzo on 2007-08-16
ok it worked for like a full second, my router i can see is recogniced it in its client list however in the network tools manager, i have got a new ukown device:

originally it was unckown interface (ra0)

now it is that + this:

unknown interface (ra0:avahi)

---

### Post by Lord Funzo on 2007-08-16
ok, i can connect, but i keep on loosing my connection every few seconds to the internet, any idea how i can stop this?? if i click on my network then type "sudo dhclient ra0" then it connects me but i get disconected in under a minute.

---

### Post by walkerk on 2007-08-16
Is your ip 169.254.xxx.xxx?
```
ifconfig
```

I suspect you have a DHCP problem. If so, ensure that DHCP is enabled on your router. If your computer is looking for DHCP but does not recieve an address back from a client it will default to 169.254.xxx.xxx.

I actually helped one user with a similar issue and after a lot of trouble shooting a quick reset on his router (which enables dhcp by default usually) fixed his problems..

---

### Post by Lord Funzo on 2007-08-16
i dont think it is a dhcp error, ubuntu connects to it and uses the internet though it, it just disconnects after about a minute.  My dhcp defaults to 192.168 and if enabled.

---

### Post by Lord Funzo on 2007-08-16
Ok!! i think i have done it, i manually configured the wirless network in ubuntu, sorry to leave so many posts, i am literally working as i am posting, thanks for all of your help everyone, would have never done it without you!!  It might break again in 20 secs so i might be back.

---

