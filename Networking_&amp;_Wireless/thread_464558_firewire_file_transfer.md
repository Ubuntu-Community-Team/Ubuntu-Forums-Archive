---
title: "firewire file transfer"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by srhlefty on 2007-06-04
I have two computers with firewire ports.  I've heard it is possible to use a firewire cable to transfer files between the computers, sort of like an ethernet crossover cable.  How do you set it up in linux, or even windows?

---

### Post by kidders on 2007-06-06
Hi there,

There are two ways of doing that. One, like you mentioned, is to set up an IEEE 1394 network, and transfer your files that way. The other involves putting one machine in "target disk" mode (assuming one of them supports doing that), to temporarily turn one of your boxes into a giant hard drive, which can simply be mounted and used as normal.

Since you mentioned the networking route, a *brief* summary (in Linux terms) goes something like this...[LIST]
[*]Install & configure a DHCP server on a "master" box. You don't *have* to do this, but it would allow you to connect any other PC to it without having to fiddle with network settings.
[*]Connect another PC to your box, and load firewire networking support into the kernel if necessary.
[*]Start your DHCP server.
[*]Start (or restart) whatever filesharing service you want to use (AFP, NFS, Samba, WebDAV, etc).[/LIST]Whatever way you choose to do it, you'll find that there's quite a lot of donkey-work to be done to create something that's actually useful. To avoid having to go through it all over and over, I would suggest...[LIST=1]
[*]Trying to take steps to avoid having to do any configuration on the "client" box, eg using DHCP over manual network configuration, and
[*]Once you've performed the configuration (and deconfiguration) procedure a few times, and you feel like you know your way around it, create a shell script to automate the process.[/LIST]That way, you'll be able to simply plug two boxes into eachother, and off you go. If you opt for Samba-based filesharing, a Linux box configured roughly as I described should be happy to talk to anything ... Linux, Mac, Microsoft, etc ... as long as it supports firewire networking.

[[SIZE=1][COLOR=Silver]UAResolved[/COLOR][/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")

---

### Post by cld71 on 2007-11-24
This link helped me.

[http://ubuntuforums.org/showthread.php?p=3830702#post3830702:](http://ubuntuforums.org/showthread.php?p=3830702#post3830702:))

But, I would suggest using your 100Mb ethernet card rather than firewire.:(

The transfers rates are more faster(7MB/s vs 12MB/s) and reliable(transfer stalled after 15 sec).:)

---

### Post by ryanVickers on 2007-11-24
if it's not working, make sure that inside the firewire port (probably labled "1394") is actually attached to the motherboard :p

Note: even though they are the same shape and everything, don't just put it into a free USB port lol

---

