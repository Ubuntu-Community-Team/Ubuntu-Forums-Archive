---
title: "Network manager with different wired and wireless networks"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by Duwi on 2006-11-30
Hi,

I have a problem with networking on my Ubuntu Edgy equipped T60 laptop.

I have network manager installed and it works fine for the wireless networks.

There are some problems with the wired networks.

What I would like to have is that I can choose what network device to use. That means either the wireless OR the wired one.
On the wired side I would like to use a fixed IP configuration for when I am in the lab. At home I would like a DHCP configuration for the wired card. Of course I would prefer not always to change the settings manually. Instead I was hoping to can select different network configuration with the networkmanager. 

I thought I managed to do so already, but the following problem occured.
The wired card was last connected to my office/lab network with a fixed IP. At home I connected wireless through the DHCP configured wireless card.
Now when I wanted to ssh into my Linux computer at work, I got the route to host error. 

This effect went away, as soon as I changed the configuration of the wired network card to DHCP. Although I was not using it, the IP configurations stored influenced the wireless networking.

My question: Is there a way to configure the entire networking stuff in a way that I can choose networks as I please and that only the configuration is used that I chose for the particular network?

Thanks a lot in advance

---

### Post by bernied on 2006-11-30
You could consider writing some scripts for this, but I don't know how they would integrate with the network manager magic.
So a script would 
- configure an adapter (wired or wireless) with either desired fixed IP address or dhcp
- take down other adapter and bring up the one you want

or maybe you create alternate sets of config files for the different locations, then the script just has to swap these about and restart networking.

Is there an easier way??

---

### Post by bernied on 2006-11-30
someone made a start of it here:
[http://www.ubuntuforums.org/archive/index.php/t-101223.html](http://www.ubuntuforums.org/archive/index.php/t-101223.html)

---

### Post by bernied on 2006-11-30
ok, here's something probably a bit easier, if it works
[http://muthanna.com/quickswitch/](http://muthanna.com/quickswitch/)
> QuickSwitch is a utility that lets Linux/Unix laptop users create and use roaming network profiles. Instead of individually reconfiguring the network card, changing DNS entries, hosts files etc. it lets you create one centralized file for all your different profiles. QuickSwitch has been around since early 2000 and is now the most widely used utility of its kind.

---

