---
title: "DNS -problem after using DHCP on eth0"
date: 2006-10-06
forum: Networking &amp; Wireless
---

### Post by ked on 2006-10-06
Hi all,

I've been running Breezy on an Acer Laptop flawlessly for a long time now. Here at work we use static IP-adr and everything has just worked out of the box. A couple of days ago on a journey, I connected to a wire LAN with DHCP. I configured my eth0 for DHCP and everything worked fine. When coming back to my office I can't get my DNS to work proper (it is for sure a problem with my setup since I've got a second linux box working just beside me). Everything works fine when surfing in a web browser, but ftp, telnet, ssh etc. does not work (unless I just use IP-numbers).
I've looked through critical files:

/etc/resolv.conf
/etc/network/interfaces
/etc/hosts

and even changed to backup files, but without any luck.
What other files involving DNS may have been corrupted or overwritten?
I've been using the bit buggy Gnome "network-admin" tool, but I've never been as stuck as now.

 
Ked

---

### Post by kamazu on 2006-10-06
Hi Ked,

We had a similar problem here with the gnome network-admin, but altering it manualy and restarting the network /etc/init.d/network restart, did the job.
Can you post the content of the 3 config files you mentioned?

kamazu

---

### Post by ked on 2006-10-06
Thanx for helping me out here :)

Everything with the network works fine except the DNS part. I have loads of scripts and stuff relying on a working DNS... I'm more and more sure it lies deeper than these three files... Does this Gnome network-admin add any config stuff which is not visible???

##########################################

/etc/resolv.conf looks like this

nameserver 128.39.66.2

##########################################

##########################################

/etc/network/interfaces looks like this:

# The loopback network interface
auto lo
iface lo inet loopback


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 128.39.66.57
        netmask 255.255.255.0
        network 128.39.66.0
        broadcast 128.39.66.255
        gateway 128.39.66.254
        # dns-* options are implemented by the resolvconf package, if
        # installed
        dns-nameservers 128.39.66.2

########################################

########################################

/etc/hosts look like this:

127.0.0.1 localhost.localdomain localhost phd
128.39.66.57 phd

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


########################################


Thanx in advance.

Ked

---

### Post by ked on 2006-10-10
Problem solved!
Our SUN server did have problems talking with my Ubuntu laptop (and several other PCs) for unknown reasons. Obviously it was a dns issue, most probably on the sever side. Rebooting the SUN server solved all problems so I think SUN has a dns buffer problem or something...
:p

---

