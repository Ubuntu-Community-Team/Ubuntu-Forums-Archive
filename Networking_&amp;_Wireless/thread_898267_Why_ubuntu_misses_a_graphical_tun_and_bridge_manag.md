---
title: "Why ubuntu misses a graphical tun and bridge manager?"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by angyel on 2008-08-23
Hi everyone, 
I need to easily manage my network configuration.

After about 4 month since my first search and 4 month spent in a own-made-script-patch, I have done another search to see if such a network manager has been developed. 
YAF - Yet another failure...

I use ubuntu 8.04 as Host system for Virtualization with VirtualBox. My hw is a laptop and I have to say I am working well on the guest system with good performances.

But the lack of all this situation is the networking. On the host system I have two interfaces, one wired and one wireless. For working with the guest system I have to create a bridge for the wired one, while for the wireless I have to create a tap adapter.
I have to move frequently (at least once per day) from one office to another where configurations differs.
Creation and setting through command line is not a problem, but it takes too much time for the whole amount of commands I have to type (even if many say I am a very fast typing guy...).
I don't own on my dna linux command line like a geek would, for I come from windows environments and am using linux since a couple of years.
Now GUIs like NetworkManager, firestarter, wicd can't permit me to easily manage such configurations and store them for I can ready switch from one configuration to another like I would on windows.

So my question becomes, why Ubuntu do not still include a tool to graphically manage bridges and virtual adapters, or each interface an ifconfig would show?

Kind regards to everyone, Angelo Maragna

---

### Post by scotty64 on 2008-11-07
> **angyel said:**
> Hi everyone, 
I need to easily manage my network configuration.

After about 4 month since my first search and 4 month spent in a own-made-script-patch, I have done another search to see if such a network manager has been developed. 
YAF - Yet another failure...

I use ubuntu 8.04 as Host system for Virtualization with VirtualBox. My hw is a laptop and I have to say I am working well on the guest system with good performances.

But the lack of all this situation is the networking. On the host system I have two interfaces, one wired and one wireless. For working with the guest system I have to create a bridge for the wired one, while for the wireless I have to create a tap adapter.
I have to move frequently (at least once per day) from one office to another where configurations differs.
Creation and setting through command line is not a problem, but it takes too much time for the whole amount of commands I have to type (even if many say I am a very fast typing guy...).
I don't own on my dna linux command line like a geek would, for I come from windows environments and am using linux since a couple of years.
Now GUIs like NetworkManager, firestarter, wicd can't permit me to easily manage such configurations and store them for I can ready switch from one configuration to another like I would on windows.

So my question becomes, why Ubuntu do not still include a tool to graphically manage bridges and virtual adapters, or each interface an ifconfig would show?

Kind regards to everyone, Angelo Maragna

I agree and I have the same problem, but I wonder if Virtualbox would be the primary target for a feature request. I am using vmware since several years and you can set up a bridge without the "tinkering" with your network settings that you need to do with Virtualbox. Vmware does it all in the kernel module and this does not even interfer with the WiCD network manager I am using.

---

