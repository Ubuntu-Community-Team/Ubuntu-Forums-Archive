---
title: "Multiple network profiles?"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by Ck.asdf on 2008-09-02
This mainly pertains to IP address configuration.

I connect my laptop to several different networks, all with different IP structures. 
Home: 192.168.1.*
Work: 192.168.0.*
Church: I can't remember, but it's different too.

My computer is on dynamic IP right now, which is fine, I can get to the Internet, but I'd like to be able to connect to my laptop from other computers, if I hook it to the network, and having a static IP from each network would be handy.  So, is there a way to make the computer say "okay, I'm home, let's give it this IP address.  Now I'm at church, this IP address should be used."  and all that?

Thanks for any help you might be able to help!

---

### Post by iwc5893 on 2008-09-21
I'm in a similar situation.  I'm an installer/tech for my WISP, and I am constantly having to change between IP address configurations.  The IP address ranges I use are:
192.168.*.* - router configs
169.254.*.* - antenna programming initial
10.10.*.* - antenna programming final
10.1.*.* - DHCP assigned ranges

Is there any way to easily switch between these on the fly?  I've tried to configure the network config tool with wildcards, but that doesn't seem to work.  The roaming mode doesn't work consistently either.

---

### Post by fdk21069 on 2009-05-18
Hi everybody,

I got similar situation. I have wired connection at workplace and wireless connection at home.
Does anyone know how better to handle this sort of things in perspective of network profiles?
:-k

---

### Post by Ck.asdf on 2009-05-19
might there be some kind of script that can be created?
I know with *ifconfig*, I can set the address of the interface, and
the default gateway can be changed with *route*, 
but what about DNS servers? Will those automatically be retrieved from the router?

```

ifconfig wlan0 address 192.168.0.243
route add default gw 192.168.0.1 wlan0

```

Those two commands look proper, right?  I read in the man page of ifconfig that the netmask address is automatically set to a default based on class A, B, & C network defaults (here, it'd be 255.255.255.0 right?)


Again, where would DNS come from? Would it be automatic? If I put the above two lines into a text file, chmod'd it to an executable, then ran it, maybe with root privileges, it'd change automatically, right? Would I need to add another line, "/etc/init.d/networking restart" or would that be necessary?  After that, I could make a few different "batch" files for the different locations I frequent.

---

### Post by superprash2003 on 2009-05-19
ubuntu 8.10 handles that for wireless..should for wired also i think

---

### Post by Ck.asdf on 2009-05-19
Where do I go to deal with that stuff? And I'm not talking about DHCP, here.  I'd like to set my laptop as static at each place I go simply by clicking one of the profiles.  That way, I can go to it from the network on another computer, wherever I am, without having to find whatever the DHCP assigned IP address is - I'd just remember what I had set for that particular network.

---

### Post by superprash2003 on 2009-05-19
system->preferences->network configuration . you set it once when you get connected and the next time it would use those settings by recognizing the SSID

---

### Post by Iowan on 2009-05-19
> **fdk21069 said:**
> Hi everybody,

I got similar situation. I have wired connection at workplace and wireless connection at home.
Does anyone know how better to handle this sort of things in perspective of network profiles?
:-kWhat version? Jaunty seems to handle it pretty well.

---

### Post by Ck.asdf on 2009-05-19
This worked! And now that I think of it, I think I MAY have seen this setting in the past, but had never really messed with it, maybe not sure what I could use it for.

Thanks for pointing it out! It shall be quite helpful. :)

---

