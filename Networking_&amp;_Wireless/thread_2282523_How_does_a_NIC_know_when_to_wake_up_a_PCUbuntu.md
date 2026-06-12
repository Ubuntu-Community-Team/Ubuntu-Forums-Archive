---
title: "How does a NIC know when to wake up a PC/Ubuntu?"
date: 2015-06-14
forum: Networking &amp; Wireless
---

### Post by legswilly on 2015-06-14
I would like to find out how I can query a network cards properties/capabilities.
The reason why is, that I would like to find out how a NIC wakes up a computer. No, I don't want to know about Wake-on Lan with a magic packet. For instance, I have a Synology NAS and it goes to sleep. When I turn on a PC or a TV it wakes up and is ready to serve. How does it do that? I had found the answer to my question of property query of the NIC, lost it and can't find it anymore. I have never found an answer as to how the NIC does it. I would like to set up a server, one of the obstacles is waking it up from sleep.

---

### Post by legswilly on 2015-06-15
Found what I was looking for, of all things on a Wake-on-Lan page: [https://wiki.archlinux.org/index.php/Wake-on-LAN](https://wiki.archlinux.org/index.php/Wake-on-LAN).
First query the driver to see if it's defaulted to 'on' by using ethtool: 
# ethtool net0 | grep Wake-on
        Supports Wake-on: pumbag
	Wake-on: b
The values define what activity to wake on: d (disabled), p (PHY activity), u (unicast activity), m (multicast activity), b (broadcast activity), a (ARP activity), and g (magic packet activity). 

Then I wanted to know what the difference between unicast, mulicast etc is. Found this page: [http://serverfault.com/questions/279482/what-is-the-difference-between-unicast-anycast-broadcast-and-multicast-traffic](http://serverfault.com/questions/279482/what-is-the-difference-between-unicast-anycast-broadcast-and-multicast-traffic)

Reading it, I thought multicast must be used with my Synology NAS. Could someone confirm this please.

---

### Post by tgalati4 on 2015-06-15
Send an email to Synology and ask them.  Unless you can open a terminal in the NAS (it does run a form of linux), you could experiment by setting up *etherape* and watching the traffic between the two devices.  You could also ask the question on the Synology NAS forums:  [https://forum.synology.com/enu/](https://forum.synology.com/enu/)

---

