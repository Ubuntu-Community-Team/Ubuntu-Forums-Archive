---
title: "Static DHCP by computer name, not MAC?"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by atfrase on 2007-06-17
Is it possible to configure an ubuntu-based DHCP server to assign static IP address according to computer name (linux machine name or Windows NetBIOS name), rather than by MAC address?

For example, I would like to be able to tell the DHCP server that 'term05' (i.e. 'term05.my.subnet') should always have IP address 192.168.0.105/24.  Then, whenever any computer named 'term05' requests a DHCP lease, it should be given this IP address (and appropriate gateway, DNS, etc), no matter what network card it is using.

For context, I have many interchangable terminals deployed on a subnet, with a few backup terminals configured for rapid replacement, which will naturally have different MAC addresses (being different physical computers).  Right now, I hardcode name/IP pairs in DNS and hardcode corresponding machine name/IP addresses on each terminal, but this is a pain.  If 'term05' dies and I need to deploy a backup as a new 'term05', I'd like it to be given the correct IP address via DHCP just by renaming it 'term05' and plugging it in, without having to update and reload the DHCP server's MAC assignment for the 'term05' IP, and without having to hardcode network configurations on the terminals themselves.

---

### Post by arvevans on 2007-06-17
Most WiFi Hub/Routers that do DHCP services can assign static IP addresses based on the computer's network name.  My Netgear WiFi Hub/Router does that.  Unless your list of DHCP clients is quite large, it seems that an inexpensive Hub/Router with DHCP server capabilities could be more cost effective and easier to administer than running DHCP on a Linux computer on your LAN.
_._

---

### Post by atfrase on 2007-06-17
Thanks for the reply!

Unfortunately, for the sake of clarity and privacy I have simplified the situation a bit: this is not a small home LAN.  There are many, many machines in question, and the network itself is divided into several subnets with various security levels.  So, a home-LAN router will not be sufficient.

But, the fact that any device can do what I'm looking for in the context of DHCP gives me hope; I just need to figure out how to emulate that behavior on a full linux server.

Any ideas?

---

### Post by nixfaced on 2007-06-17
Your question got me curious, so I did a bit of playing around with my network.  I'm not 100% sure that I did this correctly, but it seems to get the correct results, so YMMV.

I've been using mac-to-IP mappings in dhcpd, like so:

host mylaptop {
  hardware ethernet <mac goes here>;
  fixed-address 192.168.1.5;
}

Which I assume you're doing similarly.

The man page for dhcp-options indicates that we can specify a dhcp client identifier within a host declaration, which I take to mean that we can set it to something other than the mac address, which is usually used for that purpose.  I also checked the man pages for dhcpcd and dhclient, and both provide methods for sending a dhcp client identifier field.

So I changed dhcpd.conf:

host mylaptop {
  option dhcp-client-identifier "mylaptop";
  fixed-address 192.168.1.5;
}

and I added the following line in the laptop's dhclient.conf:

send dhcp-client-identifier "mylaptop";

For dhcpcd, the way to soecify a dhcp-client-identifier is to start it with the -I "foo" switch.

I restarted my dhcpd server and the dhcp client on the laptop, and it gave me the correct IP.  To ensure that I wasn't simply requesting the original IP, I specified a different IP in dhcpd.conf and was again given the correct IP.  

Unfortunately, I was unable to test this on other OS's because all I only run Linux machines on my network at the moment.  But hopefully this gives you a place to start and you are able to work out the dhcp client details for the various OS's you deal with.

Depending on your exact needs and setup, you may also want to look into dynamic dns updates, where instead of giving out IPs based on hostnames, the dhcp server updates a local dns server with the hostname of the computer given a lease, so that you can still do forward and reverse dns lookups for dynamically configured clients.

---

### Post by kaffe_02 on 2008-01-08
Does anyone have any ideas how to do this with windows clients?  I unfortunately have a few of them that are connecting to my network and would like to hand them out the same IP address by their host name ever time.

---

