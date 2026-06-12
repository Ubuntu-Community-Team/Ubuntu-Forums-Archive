---
title: "Feisty - No DHCPOFFER anymore"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by MALEADt on 2007-07-03
Hi all,

I've recently installed Ubuntu 7.04, and have been tweaking it for some days. All those days, I could access my local network and the internet without any problem. But suddenly, after a boot, all network connectivity totally disappeared... When looking closer, I found that dhclient can't recieve any DHCPOFFERs anymore.

However, this doesn't seem to be the actual problem. Normally, even when no network is set up, the led's on my NIC does flash when any packet is sent. Now, this isn't happening. So I verified the installation of my NIC (an onboard RTL8139C), without finding any problems though. Modprobing the driver again (8139too, iirc) doesn't help either.

Also I tried some basic stuff I found on the internet (including this forum), like commenting out the ipv6 alias in /etc/modprobe.d/aliases, restarting the network (by executing *init.d/networking restart*, or by doing *ifdown eth0, ifup eth0*, or *ifconfig up/down*), removing the avahi-daemon (read the PS to understand why), restarting the network after removing the dhclient pid, ... etc.

Now, do I miss something fundamental, or does anybody has another suggestion? I'd be happy to hear them :)

Thanks in advance,
maleadt.


P.S.
During the last session when I got internet, I can't remember doing something exotic. I did however, install some updates from the ubuntu-backport repository (and i don't remember if that was during that last session :? ) which could have broken network connectivity. I know there was an update for libavahi, that's why I disabled the avahi client, with no result however. Secondary question: is there a way to see, chronologically, which updates have been installed? Thanks :)

---

### Post by jpeddicord on 2007-07-05
While I am not entirely sure about your post as a whole, you can check which updates have been installed by opening Synaptic (System > Administration > Synaptic) and going to File > History. Hopefully from there you can figure out which update broke the networking.

Jacob

---

### Post by sadhaka on 2007-07-06
I am having a very similar problem, with an Acer laptop. Unfortunately, I have found that when one really needs specific technical help, forums like this often don't provide it. In fact, questions posed by users that are either too difficult or too simple frequently get ignored altogether. I'm hoping that I'll find something useful through Google...

Best of luck to you. If I find something out, I'll post it here.

---

