---
title: "Ehternet Interface changes on each reboot"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by njparton on 2007-10-27
I have an annoying issue on a fresh gutsy install (AMD64).

Each time I restart, the ethernet interface increments by 1 (etho, eth1, eth2 etc etc) - I'm now on eth9!  I'm trying to configure a static IP so that my router always assigns my ubuntu  PC address 192.168.1.10, but the router is getting confused and sees two unbutu PC's I think because of these constant changes. It assigns one the static IP address above an one  the next available free IP address, even though there's only one ubuntu PC connected.

I can't then connect to the internet.

I'm using an onboard realtek nic on an nforce 630a chipset.

Any ideas anyone?

**edit** I've also just noticed that the mac address of the nic keeps changing after each reboot. How's *THAT* possible?

---

### Post by njparton on 2007-10-27
OK, I've found a post elsewhere that tells me that the last 3 octets of the mac address are administered locally so I'm thinking this is a driver or OS issue?

Will swapping to 32 bit gutsy help?

My last resort will be to buy an Intel Pro/1000 PT or GT card (I was only planning on this if the onboard nic doesn't support wake on lan...).

Is there a startup script somewhere I can edit to stop the random mac address re-assignment?

Anyone?

---

### Post by lptr on 2007-10-27
Having a problem that is somewhat different, but is based on same thing (at least I believe this).

I installed a machine on a machine A and running it now on a completely different hardware on machine B.

Machine B of course has another MAC. Machine started fine - immediately found router and gateway and I was pretty safe that manually changing IP address will be a snap. But: Far away!

Neither configuring it through knetwork nor manually changing things in /etc/network, like I did in the past (at least in 5.10 it was possible) when things went nil, worked out. When doing the later one, I recognized when using ifconfig really strange results. No ip4 addresses assigned and such. Never saw something like this before.

So I started searching over in /etc. Well, first stop: /etc/iftab
yes a MAC address was there but commented out.

There I found the hint to look into /etc/udev/ruels.d/70-persistent-net.rules
Another MAC address there, and: Yes a secondly added NIC interface eth1. Obviously that one that is currently active, but only via DHCP.

I believe that there are some glitches in knetwork that does not recognize things like removing / exchanging NICs or such. Or - if like in your case this is a no name NIC that has some sort of hm.. 'weak' MAC addresses? I have heard that noname NICs having no fixed MAC address. They easily can be reconfigured in MAC address. Usually black heads using such cards, it has been told. I admit I never held such a card in my hands - so maybe this is false. I don't know. Maybe you having a problem based on this? 

Question to others:
What I would like to know from our experts here in forum is: Need I simply change /etc/udev/ruels.d/70-persistent-net.rules eth0 line to my new MAC address to stop this stupid knetwork thing fiddeling around and confusing network config? The point is I currently only having remote access to machine. And therefore there is not much space for experiments :(.

If there is a howto (I did not find, yet) I would highly appreciate to know the link to it. 

Thanks in advance.

rob*

---

### Post by njparton on 2007-10-27
I'll have a look into that myself, otherwise we both need an experts help!

---

### Post by njparton on 2007-10-27
I have 4 entries in that file: eth0 to eth4 - each detecting the same PCI device but the drivers are stated to be: "?*" (forcedeth) which may be causing the issue?

Otherwise, how do I stop this happening?

In the meantime I'm going to give Gutsy 32 a try...

---

### Post by njparton on 2007-10-27
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/145382](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/145382)

Just remove the mac address entry from the 70-persistent-net.rules file apparently...

---

### Post by njparton on 2007-10-27
That will get around the issue of your ethX changing afer every reboot, but its mac address still changes making wake on lan etc a pain in the behind (I have to look up the mac address in my router before I can send a magic packet!).

This is definitely a bug that needs sorting please.

---

### Post by njparton on 2007-10-28
To get around the changing mac address bug, add the following line to your /etc/network/interfaces file:

hwaddress ether XX:XX:XX:XX:XX:XX

where  XX:XX:XX:XX:XX:XX is the mac address you'd like to use :)

---

### Post by lptr on 2007-10-29
Rehi again,

I searched under /etc file contents (find grep...) for old wrong MAC address and found, that this:

/etc/udev/ruels.d/70-persistent-net.rules 

is really the central control file.

Here I removed wrong eth0 lines and replaced remaining eth1 entries with eth0. Rebooted. Configured with that networking tool provided by KDE - done. No errors anymore all working fine.

 :)

greetings rob*

---

### Post by njparton on 2007-10-29
Thanks for putting me on to that file in the first place - it was the start of the solution to my problems :)

Now to try and cure S3 sleep problems...

---

