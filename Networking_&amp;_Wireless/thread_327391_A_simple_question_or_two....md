---
title: "A simple question or two..."
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by adamonline on 2006-12-29
Hello everyone!  I look forward to being a part of this community...

I'm running Ubuntu 6.06.  I'm going on about a week and a half of toying with it (with the Ubuntu Forums open the whole time, of course!) and I've learned a lot, but it's time to bite the bullet and ask a few questions of my own.



After trying unsuccessfuly to get a DHCP server running, I'm hoping to resolve a couple other issues (which may or may not be related) before taking another stab at it.



One thing that's bothering me is that I no longer have an eth0.  I have eth1 and eth2; both of which were installed *after* the initial installation of Ubuntu.  The card that was in the computer *during* the initial install of Ubuntu is no longer... Naturally, that's where my eth0 went...

Could this potentially cause issues? Particularly in regards to running a DHCP server?  Most importantly, is there any way to change it?  I've heard of aliases, but are those just going to confuse me more, or are they something you can set and forget about? Should I just not worry about this whole "no eth0" thing?




My second 'simple' question:

I read all over that Ubuntu is secure as can be right out of the box.  But when I type:
```
sudo iptables -L
```
it prints:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

This seems like NOTHING's closed...  I did install Firestarter, and I felt it was causing more problems than anything so I uninstalled it... Did it take my security (aka, default restricted ports) with it? Am I correct in my understanding that Firestarter merely manipulates your iptables for you?




And one last question, if you have a moment, related to running a DHCP server:

In /etc/dhcp3/dhcpd.conf, where do I get the IP to use for setting "option-routers xxx.xxx.xxx.xxx"? Is it something I defined somewhere else? If you need to see my ifconfig, dhcpd.conf, or etc/network/interfaces, let me know, but I'm really just hoping for a general answer.  As it is, it seems like it's pulled out of thin air (albeit quite related to my subnet IP).  Is it related at all to the "gateway" definition in my etc/network/interfaces?



Thanks in advance, and sorry for the long-windedness!

-ADAM

---

### Post by Iowan on 2006-12-29
First off, WELCOME to Ubuntu!!!
My network hides behind another firewall/router, so I can't help w/ iptables.
I'm about 400 miles from my server (makes it kinda hard to check), but IIRC, I just set my router address as the gateway for the server, and all worked... Beginners luck??
You could check the **/etc/network/interfaces** file to see what is set up for eth0 - or if it shows up at all.

---

### Post by adamonline on 2006-12-29
Well, I have solved a bit of these, so I'll post my resolutions for future searchers:


QUESTION 1: **CLOSED**
> **adamonline said:**
> 
One thing that's bothering me is that I no longer have an eth0.  I have eth1 and eth2; both of which were installed *after* the initial installation of Ubuntu.  The card that was in the computer *during* the initial install of Ubuntu is no longer... Naturally, that's where my eth0 went...


I happened across the answer to this in [this]("http://www.ubuntuforums.org/showthread.php?t=315107") thread, which discusses **/etc/iftab**.  In iftab, you can "assign persistent names to network interfaces [by MAC address]".  I commented out my original eth0 and manually added my two current interfaces as eth0 and eth1.  I went to System > Device Manager to identify which card went with which MAC address, since ifconfig isn't too specific on that matter.



Question 2: **CLOSED**
> **adamonline said:**
> 
I read all over that Ubuntu is secure as can be right out of the box.  But when I type:
```
sudo iptables -L
```
it prints:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```



There's a nice, beginner-friendly HOWTO on iptables [here]("https://help.ubuntu.com/community/IptablesHowTo").  I can verify that I basically have no firewall at the moment.


I still don't understand why I keep reading that Ubuntu installs with all ports closed, though.  Am I missing something?

-ADAM

---

### Post by adamonline on 2006-12-29
> **Iowan said:**
> First off, WELCOME to Ubuntu!!!
I'm about 400 miles from my server (makes it kinda hard to check), but IIRC, I just set my router address as the gateway for the server, and all worked... Beginners luck??
You could check the **/etc/network/interfaces** file to see what is set up for eth0 - or if it shows up at all.

Thank you for the reply!  As you can see above, I've solved a couple of these already.


You helped me clarify my last question, though:

I intend to use my ubuntu machine as the router/firewall for my network, so should I set 'option-routers' to the IP my ISP assigns me?  Is that considered my gateway? Or is the ethernet card that points to the internet my gateway? Dang, life's gonna suck if I have to constantly update a configuration file because it has a dynamic IP used as an argument! ](*,) If that's the case, can I somehow assign a MAC address or eth(x) alias instead of a gateway address?


I guess I need to know what exactly a gateway is!

So, some bg info: eth0 will go to the internet, and eth1 will go to my network.

Which interface is considered the gateway?  The one facing the network, or the one facing the internet? Is my whole ubuntu machine considered the gateway?  If so, how do I give it a gateway address?

Thanks again!

-ADAM

---

### Post by Iowan on 2006-12-30
My opinion (for what it's worth)...
The gateway would be the network side address of whatever is attached to the internet - the "gateway" between your network and the world.  You should have control of this address - probably either static or static lease (wouldn't want a moving target for your client computers).  
Or... the dhcp server could pass the router's address as the gateway.

---

