---
title: "wicd and my wicked failure"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by il-luzhin on 2009-06-11
I have no internet on my Desktop 9.04

I installed wicd but got no connections.  The few moments before wicd hangs i notice it sees the connetion but won't connect.  When I begin to check settings it hangs.  

I said forget it then and tried to install Network Manager -0.7.0 from a tarball but the ./configure produces an error.  

configure: error:  wireless-tools >= 28pre9 not installed or not functional

which is fine because it's my desktop, no wireless card.  

So how do I bypass this error so I can please, oh please lord, have an internet connection again.  

thanks

---

### Post by kevdog on 2009-06-11
Do you need a wireless or wired connection?

Can you post
lshw -C network

---

### Post by sdennie on 2009-06-11
Didn't your machine initially come with network manager 0.7.0?  Was that not working?

---

### Post by il-luzhin on 2009-06-16
Sorry for the slow reply, IT access has been a pain.  

Yes network manager was originally installed however wicd removed it to install itself.  I was attempting to setup a static IP to work with mythtv.

---

### Post by gn2 on 2009-06-16
Have you tried ```
sudo apt-get install network-manager
```

---

### Post by sdennie on 2009-06-16
The Pink Floyd fan above is correct.  Alternatively, you can just use the wicd from the repos:

```

sudo apt-get install wicd

```

---

### Post by tarps87 on 2009-06-16
> **gn2 said:**
> Have you tried ```
sudo apt-get install network-manager
```

> **sdennie said:**
> The Pink Floyd fan above is correct.  Alternatively, you can just use the wicd from the repos:

```

sudo apt-get install wicd

```

In the intiall post he states that the computer does not have an internet connection and therefore this will only work for wicd if the packages have been cached. I believe network-manager is on the install cd so if you point synaptic to the cd this should work

If you want to set a static ip try
```
sudo nano /etc/network/interfaces
```
Add the lines:

iface **eth0** inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.254

Replace **eth0** with you interface name, ifconfig should show you this and replace the address, netmask and gateway with the correct values for your network.

If you have any problems with this just post back

Edit is you are assigned an ip using dhcp enter
auto eth0
iface eth0 inet dhcp

This may be overridden by wcid

---

### Post by gn2 on 2009-06-16
> **tarps87 said:**
> In the intiall post he states that the computer does not have an internet connection ~

Don't need one, because:

> **tarps87 said:**
>  network-manager is on the install cd 

If the command I quoted earlier is run and the network-manager package isn't found with the CD in the drive, it's a simple matter of opening Synaptic Package Manager and ticking the relevant box in 
Settings > Repositories > Third Party Software and running the command again.

---

### Post by il-luzhin on 2009-06-16
Thanks folks.  I managed to pull network manager off the Live CD.

And thanks for the suggestion on a static ip tarps87.

---

### Post by gn2 on 2009-06-16
If you enabled the CD as a software source in the Synaptic Repository Settings, un-tick it or when you run apt you'll get error messages that the CD can't be found.

(apt = Advanced Packaging Tool)

---

