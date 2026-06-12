---
title: "Howto: Automatically bring up an ethernet interface at boot with no IP address"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by adrianlewis on 2008-06-15
Just thought that I'd share this having searched for the answer for some time:

My problem was that I wanted to use multiple network interfaces on my Hardy box but for use with VMware server. I only wanted a single IP address to be used on a specific NIC and for all other NICs to simply be physical connectors to the vmnet interfaces in vmware with no ip addresses.

My interfaces showed up nicely during the vmware config and I figured that all was well. However, no traffic seemed to pass. On looking at the output of...

sudo lshw -C network

...I could see that the eth1 interface had a bit of text next to it that said "DISABLED"

When I forcibly used the...

sudo ifconfig eth1 up

...command, the interface came up and everything started to work. However, on reboot, the interface was down again.

I then turned my attention to the /etc/network/interfaces file and tried a wide variety of options but each time I saved the file without specifying an IP address (static or DHCP) and issued...

sudo /etc/init.d/networking restart

...I found that I would get a "Ignoring unknown interface eth1=eth1" message.

So anyway - the solution was to add/edit the following section to my /etc/network/interfaces file:

auto eth1
iface eth1 inet manual
up ifconfig eth1 up

This basically tells Ubuntu (any Debian type system apparently) to configure the interface manually (note - this is different to statically) and the third line says what to do. In this case, on bringing the interface up, use the command "ifconfig eth1 up" and that alone.

Hope this helps someone.

---

### Post by mr_waters on 2008-08-23
Good if your using "ATA Over Ethernet" and need to automatically bring up an interface without giving it an IP address.

Thanks, this was very helpful.

---

### Post by gniltaws on 2008-11-12
Also good for Snort and Wireshark configs.  Thanks.

---

### Post by jdmcmillian on 2012-10-13
Just wanted to say, thanks... 4 years later this post is still helpful.

---

### Post by overdrank on 2012-10-13
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

