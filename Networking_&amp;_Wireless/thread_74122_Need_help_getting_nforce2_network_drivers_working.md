---
title: "Need help getting nforce2 network drivers working"
date: 2005-10-10
forum: Networking &amp; Wireless
---

### Post by ordered_chaos on 2005-10-10
Hi everyone, I have a nforce 2 chipset and onboard lan card. I downloaded the newest linux drivers from nvidia.com, installed the Ubuntu 5.04 Source, and successfully installed the drivers onto the system without any errors. 

I then added the following line to modules.config, which the nvidia release notes said to do.
alias eth0 nvnet

Unfortuantely when I configure and active the card, I get no hardware address or IP address in my network tools when I have this card selected. I've spent many many hours trying to get this to work, I've searched google, this site and asked my friends for help. This is my last resort. I reallly want to be an ubuntu user, I want to use it as an apache server, so networking is vital to me. I'm a linux newbie btw, does anybody have any ideas, or can you direct me to a reliable network card I can buy that works on Ubun

---

### Post by Zelut on 2005-10-11
Honestly I haven't had any issues with ANY network cards (other than wireless, of course) so I'm not sure why you would be having that problem.  I'm sure we can try to help though.

Can you post the results of the following?  ifconfig, /etc/network/interfaces

---

### Post by ordered_chaos on 2005-10-11
Thank you for replying, here is the output from ifconfig:
eth0 Link encap: Ethernet HWaddr 00:11:2F:7F:8D:F2 inet6 addr: fe80::211:2ffff:fe7f:8df2/64 Scope: Link UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric 1 ... a bunch of information ... Interrupt: 22 Base Address: 0x1000.

Here is the output of etc/network/interfaces
auto lo
iface lo inet loopback

mapping hotplug
script grep
map eth0
iface eth0 inet dhcp
auto eth0

Any suggestions?

---

### Post by doood81 on 2005-10-11
I've got Breezy working with no extra assistance (drivers), on an Asus A7N8X-E, also nForce2. The nvidia NIC, as well as the Marvell GigE NIC onboard are both detected and function flawlessly, 32MB/sec across the wire, using some old ide drives. Like I said no drivers from nvidia etc.. it all worked out of the box.

my 2cents.

---

### Post by ordered_chaos on 2005-10-11
Thanks for the reply doood, 
I guess I'll install breezy and hope I can get it too work. What must I do to improve my linux karma!

---

### Post by Biased turkey on 2005-10-12
I can only confirm what other posters mention: onboard ethernet works right out of the box with Ubuntu 5.04 Hoary hedgehog for both Nforce2 and Nforce4  chipsets.

Did you enable it in the BIOS ?

---

### Post by fourhead on 2005-11-04
Perhaps somebody can help me here. The in-kernel module for the NForce ethernet works, but it has a bug that makes uploads to the Samba server extremely slow. I've installed the nvnet driver from nvidia.com, and if I manually load it it works (and uploads are fine), but I can't get it to load automatically at boot. Well, it's loaded, but it's not used.

Although I've put 'forcedeth' into /etc/hotplug/blacklist, this driver still gets loaded. From several threads here I was told to do this:

Put 'nvnet' into /etc/modules
Put 'alias eth0 nvnet' into /etc/modules.d/nforce

But both didn't work. I even moved forcedeth.ko out of the /lib dir, but it STILL gets loaded!?!? Can anyone help me??? What's the correct place in Ubuntu to load/not load modules?


Tom

---

### Post by Stelmate on 2005-11-08
I would advise you to try the official ubuntu supported drivers that can be grabbed off of synaptic.  I use those for my 6600GT and they work like a charm.

[QUOTE=ordered_chaos]Hi everyone, I have a nforce 2 chipset and onboard lan card. I downloaded the newest linux drivers from nvidia.com, installed the Ubuntu 5.04 Source, and successfully installed the drivers onto the system without any errors. 

I then added the following line to modules.config, which the nvidia release notes said to do.
alias eth0 nvnet

Unfortuantely when I configure and active the card, I get no hardware address or IP address in my network tools when I have this card selected. I've spent many many hours trying to get this to work, I've searched google, this site and asked my friends for help. This is my last resort. I reallly want to be an ubuntu user, I want to use it as an apache server, so networking is vital to me. I'm a linux newbie btw, does anybody have any ideas, or can you direct me to a reliable network card I can buy that works on Ubun[/QUOTE]

---

