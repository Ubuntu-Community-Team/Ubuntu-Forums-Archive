---
title: "Wireless network drops my IP address"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by dpmccoy on 2007-02-06
I switched from a wired to a wireless network this past January in Kubuntu 6.10.  I use a Netgear WG311v3 PCI wireless card on my system, and it works beautifully under Ndiswrapper.  Here's my problem: my wife has a Sony VAIO laptop with a Centrino processor.  When she connects to the wireless network (we use a Linksys WRT54G router), I lose my IP address on my Linux system.  This doesn't happen under Windows XP.  To get my IP address back, I simply "sudo ifdown wlan0 && sudo ifup wlan0", and I'm back in business.  I am running Samba as well.  She can't access my shares until I "sudo /etc/init.d/samba restart".  
  This seems like an odd problem.  Has anyone else had this happen?  I know that Samba isn't the problem because it happens whether Samba is running or not.  The problem also occurs under Gnome.  Any suggestions?
  My /etc/hosts file is as follows (my computer is david-desktop):

```

127.0.0.1 localhost
192.168.1.100 david-desktop
# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

```

My /etc/network/interfaces file is as follows:

```

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid {omitted from post}
wireless-key {omitted from post}

```

Please let me know if I need to post any more of my config.  Thanks.

---

### Post by spd106 on 2007-02-06
You have a static address in the hosts file, but you are using DHCP to get an address from the router. This won't work very well, as chances are they won't be the same. I suggest that you remove the line from the hosts file or change the interfaces file to the same static address, then add a default route address.

The second way might solve your ip address problem, but if you want to connect to other wifi networks it will have to be switched back to DHCP.

NB It's not a great idea to tell the world your ssid/encryption key.

---

### Post by dpmccoy on 2007-02-06
> **spd106 said:**
> You have a static address in the hosts file, but you are using DHCP to get an address from the router. This won't work very well, as chances are they won't be the same. I suggest that you remove the line from the hosts file or change the interfaces file to the same static address, then add a default route address.

The second way might solve your ip address problem, but if you want to connect to other wifi networks it will have to be switched back to DHCP.

NB It's not a great idea to tell the world your ssid/encryption key.

I thought my problem was fixed, until I rebooted my wife's laptop.  I did your first option.  When her laptop connects, my address drops.

Any other thoughts?

---

### Post by spd106 on 2007-02-06
Does the xp machine steal your IP address or get a different one?

Have you tried installing [Network Manager]("https://wiki.ubuntu.com/WifiDocs/NetworkManager")?

---

### Post by dpmccoy on 2007-02-06
> **spd106 said:**
> Does the xp machine steal your IP address or get a different one?

Have you tried installing [Network Manager]("https://wiki.ubuntu.com/WifiDocs/NetworkManager")?
Her computer (which I'm on now) gets a different one. My system almost always picks 192.168.1.100, while hers grabs 192.168.1.101.  
Is the Network Manager you're referring to the same one that sits in the "applet tray" in Gnome?

Please forgive me if I sound like a n00b...I've been using Linux for several years, but always on a wired network. I appreciate any help!

---

### Post by spd106 on 2007-02-06
There are two gnome tray applets, yes it's confusing for everyone. The network-admin capplet just does WEP, Network Manager does WPA. NM has a kde applet as well, though I'm not a kde user so I don't no the specifics. NM will monitor the connection and should try to grab an IP address if it get lost.

Have you checked the logs for any suspicious errors? The syslog might have something or maybe dmesg. It's very rare for this to happen, I've only heard of it happening with some early drivers, updating the firmware/drivers of the cards and AP sometimes helps.

You might want to try tcpdump or maybe wireshark (universe repo) to catch what's going on.

---

### Post by dpmccoy on 2007-02-06
> **spd106 said:**
> There are two gnome tray applets, yes it's confusing for everyone. The network-admin capplet just does WEP, Network Manager does WPA. NM has a kde applet as well, though I'm not a kde user so I don't no the specifics. NM will monitor the connection and should try to grab an IP address if it get lost.

Have you checked the logs for any suspicious errors? The syslog might have something or maybe dmesg. It's very rare for this to happen, I've only heard of it happening with some early drivers, updating the firmware/drivers of the cards and AP sometimes helps.

You might want to try tcpdump or maybe wireshark (universe repo) to catch what's going on.

Thanks for the reply.  Curiously, I checked both "messages" and "syslog" and noticed that the following happened when my IP address dropped:

```

Feb  6 19:35:40 david-desktop kernel: [17180719.304000] bridge-wlan0: is a Wireless Adapter
Feb  6 19:35:56 david-desktop gconfd (david-14269): GConf server is not in use, shutting down.
Feb  6 19:35:56 david-desktop gconfd (david-14269): Exiting
Feb  6 19:35:58 david-desktop gconfd (david-14650): starting (version 2.16.0), pid 14650 user 'david'
Feb  6 19:35:58 david-desktop gconfd (david-14650): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb  6 19:35:58 david-desktop gconfd (david-14650): Resolved address "xml:readwrite:/home/david/.gconf" to a writable configuration source at position 1
Feb  6 19:35:58 david-desktop gconfd (david-14650): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Feb  6 19:35:58 david-desktop gconfd (david-14650): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Feb  6 19:35:58 david-desktop gconfd (david-14650): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4


```

Any thoughts on this?  Thanks.

---

