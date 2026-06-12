---
title: "Configuring IP address with wrt54gl"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by mrphud on 2008-01-25
Hi,

I am trying to configure my router so that I may open a port for azureus. However I am used to using windows and I don't know the networking components of ubuntu yet. If anyone can help I would appreciate it.

Thanks

---

### Post by chewearn on 2008-01-25
Opening a port in the router is OS independent.  It doesn't matter whether you have ubuntu or windows in your PC; the router can be configured by its web interface via any browser in any OS.

---

### Post by mrphud on 2008-01-25
Yes that is true. I guess the question I have distilled is how do I change to a static ip in ubuntu that starts with 192.168.... I have tried several methods but to no avail.

---

### Post by BrentC on 2008-01-25
> **mrphud said:**
> Yes that is true. I guess the question I have distilled is how do I change to a static ip in ubuntu that starts with 192.168.... I have tried several methods but to no avail.

Wait, are you trying to find the local IP address for your router's config GUI or are you trying to set the local IPs to be static from the router configs?

---

### Post by mrphud on 2008-01-25
Well I know how to set up the router. What I am new to is the networking stuff in ubuntu. I am in my /network/interfaces file and I am going to setup a static ip. I think this will work. The problem is is that I am new to setting up a static IP and mine is set to a loopback by default. I have no freakin idea what a loopback is or is not. I was going to do dchp but this means that I cannot be consistent with my portforwarding. I am pretty sure, after about 3 billion hours of research, that I know what to do but it has been a pain. At least I will know how to help others in the future. If you have any info on the loopback stuff I would like to learn about it.

Regards

---

### Post by chewearn on 2008-01-25
You don't have to mess with command line for this; simply go here via GUI:
Top Panel Menu > System > Administration > Network

You will be prompted for the admin password, then the "Network Settings" dialog will pop-up.  Select your network interface from the list, then click Properties, uncheck Roaming, and then specify your static IP configurations.

---

