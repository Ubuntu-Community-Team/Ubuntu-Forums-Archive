---
title: "Is this setup possible?"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by Arbiter on 2007-10-03
Hi everyone :)

I'm looking at redoing my home network - I want to finally get all the machines in my house on fixed IPs to simplify stuff.  I just want some opinions as to if this configuration will work...crude diagram follows...i'm an experienced computer tech, but haven't done serious network stuff in a while, so please pardon my ignorance...


INTERNET
    |
    |
CABLE MODEM
    |
    |
LINUX BOX
    |
    |
8-PORT GIGABIT SWITCH
    |
    |
VARIOUS PC's


The Linux box (running Ubuntu of course ;) ) would be performing the duties of a router/firewall/DNS server (for the local domain, not internet domain - is this relatively simple to achieve?) and would be passing packets directly to an 8 port Gigabit switch.  is this all looking feasible?

---

### Post by scruff on 2007-10-03
Anything is possible :)

Check out this link:

[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

---

### Post by npumcrisz on 2007-10-03
> **scruff said:**
> Anything is possible :)

Check out this link:

[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

The link was informative. 


Scruff is it also possible to configure load balancing in-bound and out-bound on an Ubuntu or any Linux box?

---

### Post by Arbiter on 2007-10-03
> **scruff said:**
> Anything is possible :)

Check out this link:

[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)


excellent, thanks! :)

---

### Post by scruff on 2007-10-03
npumcrisz:

I know you can easily employ QoS (quality of service) that allows some decent control over in/out bandwidth allocation based on protocol, IP and/or MAC address. 

I use a Linksys WRT54g that I run this open source firmware (based on Busybox Linux), DD-WRT. It is very f'ing cool. It turns a $50 Linksys into a very high end product and all the work is already done for me. I get SSH access, as much control as I want with iptables, onboard non-volatile storage space for writing and storing scripts, and a hundred other cool features. 

[http://www.dd-wrt.com/wiki/index.php/Quality_of_Service](http://www.dd-wrt.com/wiki/index.php/Quality_of_Service)

---

### Post by scruff on 2007-10-03
True load balancing: [http://www.linux.com/articles/60871](http://www.linux.com/articles/60871)

Since the 2 of you seem interested, here's a few more advanced linux-router links that I've used in the past:

[http://www.gentoo.org/doc/en/home-router-howto.xml](http://www.gentoo.org/doc/en/home-router-howto.xml)

[http://www.skullbox.net/smoothwall.php](http://www.skullbox.net/smoothwall.php)

[http://www.stanford.edu/~fenn/linux/](http://www.stanford.edu/~fenn/linux/) (based on older kernel, but still useful info)

---

