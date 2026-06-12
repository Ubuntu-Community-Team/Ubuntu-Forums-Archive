---
title: "Registering client name when using DHCP"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by dallingham on 2007-07-25
I have a network of 7.04 machines on a inhouse network. I am using DHCP to acquire an address from the system. The problem I have is that the machine names are not getting registered with the network name server (running Windows Server 2003). All the machines get their IP address and other networking information, but the name never gets registered.

$ ping myhost
ping: unknown host myhost

I've tried explicitly setting the host name in the /etc/dhcp3/dhclient.conf file:

send host-name "myhost"

But this does not seem to have any effect.

Any help would be greatly appreciated.

---

### Post by reckless2k2 on 2007-07-25
How to resolve Netbios hostnames

    * Read #General Notes
    * System -> Administration -> Network
    * Network settings 

sudo gedit /etc/nsswitch.conf

    * Find this line 

hosts:          files dns

    * Replace with the following line 

hosts:          files dns wins

    * Save the edited file 

sudo apt-get install winbind

i think that's what you mean. that's how i got it to work. it's from this page:

[http://easylinux.info/wiki/Ubuntu:Feisty](http://easylinux.info/wiki/Ubuntu:Feisty)

---

### Post by dallingham on 2007-07-25
Unfortunately, that did not seem to help. The linux boxes are still not registering their names with the local DNS server. Linux boxes cannot resolve the name. Windows boxes cannot resolve the name.

I've tried adding the line:

send host-name "myhost" 

to the /etc/dhcp3/dhclient.conf file, but it doesn't seem to have any effect either.

---

