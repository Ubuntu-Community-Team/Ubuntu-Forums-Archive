---
title: "How do I - serve same IP lease to 2 adapters on same PC?"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by antilog on 2006-08-10
I have a laptop getting an IP address from an Ubuntu box running a DHCP server.  I have edited the dhcpd.conf to reserve an IP address for the wireless adapter on the laptop.  How do I reserve the same address if the laptop connects via the ethernet adapter?  I tried making two host entries in dhcpd.conf for the same IP address for (2) different MACs, and I got the error:
```
/etc/dhcp3/dhcpd.conf line 24: host xxxx: already exists
}
^
Configuration file errors encountered -- exiting
dhcpd self-test failed. Please fix the config file.
The error was:
```
Not a big deal, but it would be nice to configure this, as the laptop needs to have the same IP due to port mappings on the NAT.

Thanks!

---

### Post by bonjun on 2006-08-10
Setup Static IP in all your pc.

---

### Post by antilog on 2006-08-11
No, using DHCP, not static IP.  I want to leave the laptop on DHCP, as it is a laptop and not always parked at my home network.

---

### Post by NetworkGuy on 2006-08-12
I don't think you can do this.   

Can you setup a different address for when you are using your Ethernet adapter and then create another set of NAT entries for the second address?

---

### Post by antilog on 2006-08-12
I do port forwarding to the laptop, and would like it to work regardless of wireless/ethernet connection.  It sounds like it might be asking for too much out of DHCP.

---

### Post by NetworkGuy on 2006-08-12
I agree.  You either need to use Static IP as bonjun stated above or see if somebody else has another idea.

The only other thing I can think of is to replace your wireless/ethernet router with a plain access point/low cost switch and another linux PC as your configurable DHCP/Firewall server.   With a fully configurable firewall, you should be able to do port forwarding to multiple IP addresses.

But that sounds like a lot more work and money than switching your interface from static to DHCP and back again.

---

### Post by antilog on 2006-08-13
That's funny you recommend that.

My router/firewall is a Ubuntu 6.06 box running guidedog and guarddog, connected to a switch, connected to a wireless access point.  My dhcpd.conf entry is listed above.

Now that I type this, I think I may have an idea to test.  The wireless access point is actually a wireless router with all software other than wifi turned off.  Maybe I could turn on DHCP on the wireless router, set it to serve my wifi MAC .xxx, then set the dhcpd.conf on my ubuntu router to serve my ethernet MAC .xxx.

I'll let you know how it works.

---

### Post by NetworkGuy on 2006-08-13
Be careful with two DHCP servers servicing the same subnet.  You will run into problems doing that.

---

### Post by antilog on 2006-08-13
> **NetworkGuy said:**
> Be careful with two DHCP servers servicing the same subnet.  You will run into problems doing that.

Yes, it doesn't sound good.

---

### Post by NetworkGuy on 2006-08-13
Can you put another NIC into your firewall?  Make that NIC responsible for your wireless network.  Assign the NIC a different subnet.  Add the subnet to your DHCP.  Change your firewall to allow the port forwarding to two addresses.    

I don't know about you, but I still think changing back and forth to stais/dhcp is still the quickest fix.. :)

---

### Post by eigma on 2008-02-28
This has worked for me with the following dhcpd.conf fragment. Of course, we're talking about a single network, where a given client may have one or the other Ethernet address, but NEVER both Ethernet addresses on the network at the same time:
```
host icarus {
hardware ethernet 00:16:aa:bb:cc:dd;
fixed-address 192.168.2.9;
}

host icarus-wireless {
hardware ethernet 00:13:dd:cc:bb:aa;
fixed-address 192.168.2.9;
}
```

(Note the same fixed-address but **different** host name.) This worked with ISC dhcpd V3.0.1.

Good luck, YMMV.

---

### Post by Mr. C. on 2008-02-29
You may also be able to change the MAC address of one of the devices.  A majority of the devices allow spoofing the MAC address.  You'll have to check to see if yours does.  Never have both devices enabled at the same time.

MrC

---

