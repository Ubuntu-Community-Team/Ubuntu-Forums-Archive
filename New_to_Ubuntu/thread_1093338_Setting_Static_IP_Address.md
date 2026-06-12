---
title: "Setting Static IP Address ?"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-11
I want to try to set a Static IP to see if it helps from dropping my internet connection.  Was hoping for a little help with the following,

I'm looking at the pocket guide's instructions to configuring a static ip. Hoping someone can help me out with a few questions. 

"click the IPv4 Settings tab, and select
Manual from the Method dropdown list. Click the ADD button and enter
your IP address, [COLOR="Red"]subnet mask, and gateway (router)[/COLOR] details by clicking
the entries under relevant headings. Add the [COLOR="red"]DNS addresses [/COLOR]in the
DNS Servers text field (separate each address by a comma). You can
leave the Search Domains field blank. Click OK when done and reboot
the computer."

Where can I find the Subnet mask, gateway (router) and DNS address?

Thanks, JS

---

### Post by albandy on 2009-03-11
Edit your /etc/network/interfaces, and fill it with something like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 172.16.194.1
netmask 255.255.240.0
gateway 172.16.192.1
network 172.16.194.0
broadcast 172.16.207.255

Then edit /etc/resolv.conf, it should look like this:

domain mydomain.es
search mydomain.loc
nameserver 172.16.32.215
nameserver 172.16.32.177
nameserver 172.16.32.214

---

