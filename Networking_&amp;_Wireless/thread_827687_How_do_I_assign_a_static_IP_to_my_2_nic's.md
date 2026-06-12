---
title: "How do I assign a static IP to my 2 nic's?"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by tuproxy on 2008-06-13
I am setting up a firewall/router.  I have two nics installed.  during the OS installation the primary NIC was recognized and installed. When I did an ifconfig, only eht0 came up.  I went into /etc/network/interfaces and added:

```
#this is the secondary NIC
auto eth1
iface eht1 inet dhcp
```

I thought this is where I setup the NIC to be recognized automatically.  Upon reboot and another ifconfig, only eht0 was listed.  I did a 
```
sudo ifconfig eht1 up
```
and eth1 now shows with an ifconfig, BUT it doesn't have an IP address. Why is this?  Did I do this in the wrong place?  What am I doing wrong?

Finally, I decided that I want to change my setup to a static setup so how do I change that?


Thanks a lot!

Also, I installed the server edition, no GUI. Is there another editor other than vi, because I'm having a hell of a time using vi with putty.  Why can't I use the normal delete, backspace, up, down, right left arrow keys? It's all messed up.  Frustrating!!

---

### Post by chili555 on 2008-06-13
You told your machine to set up eth1, but you haven't yet told it to actually use it. Try:```
sudo dhclient eth1
```If you want a static IP address, amend your interfaces file so that the eth1 part looks like:```
auto eth1
iface eth1 inet static
address 192.168.1.116
netmask 255.255.255.0
gateway 192.168.1.1
```Substitute your details here. Select an address outside the range of IP addresses given by the DHCP server, typically in your router.

---

### Post by tuproxy on 2008-06-13
Thanks for the info!  That's exactly what I needed to make this work correctly!

I added the static IP info for eth0 and eth1.  I ran

```
sudo /etc/init.d/networking restart
```
and get this message:
>    *  reconfiguring network interfaces...
Ignoring unknown interface eth1=eth1.

Is there something else I need to do besides change the etc/network/interfaces file and run dhclient?

---

### Post by issih on 2008-06-13
```
sudo /etc/init.d/networking restart
```

That will restart things

alternatively ifdown -a then ifup -a will probably do you too

Not entirely sure this will fix things, as I suspect your 2nd nic might not be being registered by the system, could well be wrong though.

Oh and editor wise you could try using nano, its a lot friendlier than vi, or emacs if thats your kind of thing, I'd expect those to be available in the server version.

---

### Post by issih on 2008-06-13
Reading your posts a bit more carefully, its hard to know if the second nic is being registered (it probably is really most just work these days).

ifconfig -a will list all recognised physical interfaces whether up or down

ifconfig on its own only lists those that are up.

Your info from /etc/network/interfaces is not right however.

you probably just mistyped, but you need:

auto eth1
iface eth1 inet dhcp

NOT eht1.

with things set like you have them the physical interface eth1 was being brought up, but as there is no direct match or a mapping command in the file nothing else was done, hence no dhcp etc.

make it all use eth1 and you should find dhcp or static will work

---

### Post by tuproxy on 2008-06-13
> **issih said:**
> Reading your posts a bit more carefully, its hard to know if the second nic is being registered (it probably is really most just work these days).

ifconfig -a will list all recognised physical interfaces whether up or down

ifconfig on its own only lists those that are up.

Your info from /etc/network/interfaces is not right however.

you probably just mistyped, but you need:

auto eth1
iface eth1 inet dhcp

**NOT eht1.**

with things set like you have them the physical interface eth1 was being brought up, but as there is no direct match or a mapping command in the file nothing else was done, hence no dhcp etc.

make it all use eth1 and you should find dhcp or static will work

I guess I need to be more careful. :) I changed it and now I run a restart fine!  Thanks a lot!

---

