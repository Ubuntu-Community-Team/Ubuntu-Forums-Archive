---
title: "networking problems after hard disk upgrade"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by jonhewer on 2008-06-20
hello,

i recently switch the hard disk in my kubuntu 7.04 system. i used dd to clone the partition with my os and data to the new drive, installed the new drive, used rescue mode to install grub, fixed fstab, and booted up. everything appeared to be fine.

whether this is the reason behind the following problems, i have no idea.... but after booting up my machine was unable to get an ip address using dhcp. i have tried running ifdown and ifup, but still no luck. i get the following:

"No DHCPOFFERS received"

i decided to configure a static IP to see if that works. it did to some extent, i could ping the computer, and my router showed it as connected to the network. however, i could not ssh in from my other computer, it timed out. ssh is definitely working - locally, i can successfully ssh into 127.0.0.1.

also, when running an apt-get update on the machine, and it took a very long time to download the headers. the connection was perfectly fine on my other computer though.

when booting up the machine, the avahi-daemon failed to start up - is this related in any way?

i haven't yet had much time to investigate, hence the lack of information, but if anyone has any ideas or could point me in the right direction, i would be very grateful.

thanks,
jon

---

