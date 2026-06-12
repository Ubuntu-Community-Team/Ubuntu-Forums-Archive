---
title: "Keeping /ect/hosts Up to Date with DHCP"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by sjrlaw on 2008-07-11
I edited the /etc/hosts file on my workstation to add the ip address and host name for my server.  However, my router assigns ips thru dhcp.  Do I have to configure my server for a static ip address (and if so, how) or is there a way to change the hosts file so it updates the server ip if I have to reboot the machine?

Steve

---

### Post by chili555 on 2008-07-11
> **sjrlaw said:**
> I edited the /etc/hosts file on my workstation to add the ip address and host name for my server.  However, my router assigns ips thru dhcp.  Do I have to configure my server for a static ip address (and if so, how) or is there a way to change the hosts file so it updates the server ip if I have to reboot the machine?

SteveThere may be a way, but I'm not aware of it and I'm sure it's much harder than simply using a static IP address for the server.

Call me old fashioned, but I think all the computers in the network should be able to find the server instantly, either by name or IP address. That's easy to do with */etc/hosts*, as you know.

Using a static IP address is as easy as *sudo gedit /etc/network/interfaces* and make it look something like:```
auto eth0
iface eth0 inet static
address 192.168.1.115
netmask 255.255.255.0
gateway 192.168.1.1
```Use any other text editor if you do not have gedit. Nano, kate, kwrite or vim will work fine.

The address needs to be outside the DHCP range assigned by the router, and gateway is the address of the router. Proofread, save and close. Then do:```
sudo ifdown eth0 && sudo ifup eth0
```You have a static address!

Many routers are set to assign 50 or even more IP addresses through DHCP. Unless your house is very crowded, that's far too many. I suggest going into the router administration pages and changing the range to something sane, like ten. 192.168.1.100 to 192.168.1.109, for example. As you can see by the sample *interfaces* setup above, there will be no nasty collisions.

Now amend */etc/hosts* to include:```
192.168.1.115  mylilserver
```Substitute your details throughout.

---

