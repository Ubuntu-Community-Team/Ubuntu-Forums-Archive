---
title: "wan/lan hostnames"
date: 2005-08-11
forum: Networking &amp; Wireless
---

### Post by kook44 on 2005-08-11
Hi.  I have two (related) questions-
I have a WINXP desktop w/ a PCI ethernet connection, and an Ubuntu laptop using a wireless card. both are connected to a Netgear WGR614 router.

When I view the "attached devices" screen on the router's admin site, I see both computers.  The WINXP displays it's name as "DESKTOP" as it is named in My Computer - as well as the hardware MAC addess and assigned IP.  However, the ubuntu laptop only has a mac address and IP.  The name comes up as "--------".  The laptop's hostname is "ubuntu-laptop".  All of the terminal prompts will dispaly: "user@ubutu-laptop".  Executing the hostname command will output "ubuntu-laptop" and if I open up the networking administration app in gnome, "ubuntu-laptop" is listed as my host there.  Im able to ping both boxes from each other using their IP addresses.  I can even ssh into the laptop from the desktop using it's IP.
Since I'm using DHCP, how can I use only hostnames to communicate?

My second question:
I would also like to be able to ssh into the laptop from outside my home network.  How can I address a particular host specifically, using a service like DynDNS?  I don't want to use port forwarding, because what if I add more boxes, and would like to remotely log into any of them?
I'm thinking I have to have some sort of internal DNS, correct?  Does anyone have any experience setting one up with a standard cable/dsl router?

Thanks

---

### Post by heimo on 2005-08-11
One way would be to edit hosts file on your XP and add your Ubuntu computers name and IP address.
[http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prjj_ipa_cilb.asp](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prjj_ipa_cilb.asp)

If you're using NAT (only your router has public IP address) port forwarding is the way you want to go. You *could* portforward different ports to different computers (still same port on lan), but I would probably just forward one port, always log into that computer and then use internal IP addresses to ssh into the computer I really wanted to use. It's a workaround. Otherwise you'll need more public IP addresses.

---

### Post by kook44 on 2005-08-11
ok, I understand about the port forwarding thing-

But Im confused about the internal hostnames.  I've been on various corporate networks where you can just use the hosname of a machine to acces it.  Why can't I do that on my home network?

---

### Post by heimo on 2005-08-11
[QUOTE=kook44]ok, I understand about the port forwarding thing-

But Im confused about the internal hostnames. I've been on various corporate networks where you can just use the hosname of a machine to acces it. Why can't I do that on my home network?[/QUOTE]

You most probably have used net bios names. I don't know if it would work that way if you would setup samba (probably). Or you could setup your own DNS (perhaps BIND) to do name resolving, but for couple computers it's probably easiest to just add hosts to hosts file (on your linux box this file is /etc/hosts).

---

### Post by mojorising on 2005-08-24
I am having the same problem. There has to be a way to do this the way we want to, kook44 -- where any user from any host on a network can resolve the hostname to the correct ip address (ping hostname, for example) without modifying host files on each machine. 

When I find out how, I'll try to remember to post it here.


Mike

---

### Post by s_p_a_r_k_y on 2005-08-24
you want to turn on samba : ) this will give you a netbios name which is what windows uses for lans. in samba type in a 

netbios name = myCompName

under the [general] and restart it, then you can ping myCompName form windows

---

