---
title: "PPPOE stopped working"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by chiok on 2005-10-14
Howdy.  To get networking up in Hoary, I had to run pppoeconf once and then comment out make_resolv_conf() in /etc/dhcp3/dhclient-script to stop it from disconnecting after five minutes.  It was fine after that initial setup.

I upgraded to Breezy a week before it was official and networking continued to work.  In the last 24h, it stopped working.  I can run pppoeconf to get it working again, but I have to do it after every reboot.  Apache2 and Samba are, of course, still down.

I did a fresh install, but I still have to run pppoeconf after every reboot.

Any ideas?

---

### Post by Jst on 2005-10-14
I have the same problem. After every rebbot I have to do *ifconfig eth0 up* and *pon dsl-provider*. Sorry that I'm not helping you but I sympathise with you :P I would be happy to get a solution two.

---

### Post by chiok on 2005-10-14
It's good to know that I'm not the only one with the problem.  It lets me know I'm not crazy.

The weird thing is that *sudo ifconfig eth0 up* and *sudo pon dsl-provider* doesn't really work for me.  Sure I get connected, but the connection is so slow it is unusable.

---

### Post by Jst on 2005-10-14
ok here's the problem.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=10080](https://bugzilla.ubuntu.com/show_bug.cgi?id=10080)

The patched version is already in breezy so I had to edit /etc/network/interfaces and it works now. But I still don't know hot did the interfaces file get broken if I did a fresh install of brezzy which already has the patched pppoeconf. Here's my interfaces file:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
#iface eth0 inet static
#	address 192.128.1.2
#	netmask 255.255.255.0
#	network 192.128.1.0
#	broadcast 192.128.1.255

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth0
	iface eth0 inet manual

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

```

comented out that *iface eth0 inet static* section and added the line *iface eth0 inet manual* after *auto eth0*. Hope it helps.

---

### Post by chiok on 2005-10-14
Sweet!  It works now.  Thanks!

---

### Post by hanzj on 2005-10-15
[QUOTE=Jst]commented out that *iface eth0 inet static* section and added the line *iface eth0 inet manual* after *auto eth0*. Hope it helps.[/QUOTE]

My interfaces file doesn't have that *iface eth0 inet static* section, and the  *iface eth0 inet manual* is already there. But still, every time I reboot/restart, I have to do some pppoeconf. ANd usually, I can't simply go run "sudo pppoeconf" after a bootup. I'd get a message that says:

> Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason  for the scan failure may also be another running pppoe process which controls the modem.                 

So what my newbie mind tells me to do is to kill (via system monitor) stuff that I think is related to this. For example, I kill *pppd* and *pdflush*. 

Then after I kill them, I try "sudo pppoeconf again. Sometimes, it still doesn't work. Sometimes it does. I can't figure out the pattern.
What's wrong?

---

### Post by flujan on 2006-01-05
How do I apply these patches?

---

