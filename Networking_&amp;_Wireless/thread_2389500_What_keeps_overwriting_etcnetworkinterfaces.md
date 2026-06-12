---
title: "What keeps overwriting /etc/network/interfaces?"
date: 2018-04-17
forum: Networking &amp; Wireless
---

### Post by sandman887 on 2018-04-17
I'm making a custom live CD of a headless Ubuntu 17.10 server. It boots up, and everything seems fine, but some script appears to be overwriting the /etc/network/interfaces file and resetting it to the default configuration. I wanted to find out what the file actually looked like in the squashfs file, to see if it was reset to default during the squashfs creation, so I extracted it, and it is in fact my customized interfaces file. So that means that some script must be overwriting it. The question is, which one?

I deleted everything in my 99-default.link file, and I confirmed by looking up boot messages that it is ignored during boot. I'm still not very knowledgeable on systemd/udev stuff, but I saw on more than one search result on google that nulling that file would allow you to manually configure the network. I have configured it so that it has eth0-3 assigned to the four MAC addresses of the network cards.

I tested this interfaces file on both my Debian Stretch and Ubuntu 17.10 Artful computers, and they both stay the way I configured them, without getting overwritten.

/etc/network/interfaces **(works on both my Debian Stretch and 17.10 Artful computers)**
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).  
#source /etc/network/interfaces.d/*
#^initially uncommented

auto eth0 eth1 eth2 eth3

# eth0		NIC connected to external network
allow-hotplug eth0
iface eth0 inet dhcp


# eth1
allow-hotplug eth1
iface eth1 inet static
   address 172.16.1.1
   netmask 255.255.255.0
   network 172.16.1.0
   broadcast 172.16.1.255
   gateway 172.16.1.1 


# eth2
allow-hotplug eth2
iface eth2 inet static
   address 172.16.2.1
   netmask 255.255.255.0
   network 172.16.2.0
   broadcast 172.16.2.255
   gateway 172.16.2.1

# eth3
allow-hotplug eth3
iface eth3 inet static
   address 172.16.3.1
   network 172.16.3.0
   broadcast 172.16.3.255
   gateway 172.16.3.1 

# The loopback network interface
auto lo
iface lo inet loopback
```

I'm reading about systemd trying to learn it so that I can figure out this problem, but I'd be grateful if someone shares the solution.

Thanks

Edit: I guess I should mention that the live Ubuntu CD boots up with isolinux.

---

### Post by TheFu on 2018-04-19
17.10 moved to **netplan** for managing network settings. Think it uses a yaml file for configuration now. Sorry, I don't know anything more about it.

BTW, support for 17.10 ends in June, so I would strongly, strongly, suggest moving to 18.04 when it is released in a week or 2. That gets 5 yrs of support, not 9 months which is all non-LTS releases get.

Or you could move back to 16.04 which will have support until 2021 if you can't wait.

---

### Post by chili555 on 2018-04-19
Here you go! [https://askubuntu.com/questions/977833/cant-change-ubuntu-17-10-to-use-a-static-ip/977838#977838](https://askubuntu.com/questions/977833/cant-change-ubuntu-17-10-to-use-a-static-ip/977838#977838)

---

### Post by sandman887 on 2018-04-28
> **chili555 said:**
> Here you go! [https://askubuntu.com/questions/977833/cant-change-ubuntu-17-10-to-use-a-static-ip/977838#977838](https://askubuntu.com/questions/977833/cant-change-ubuntu-17-10-to-use-a-static-ip/977838#977838)

Sorry I didn't check back right away. Thank you for your link :D That helps me!

---

