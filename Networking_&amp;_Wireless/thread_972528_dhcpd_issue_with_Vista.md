---
title: "dhcpd issue with Vista"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by Keymaster on 2008-11-05
I'm running a router using 8.04.1 server and dhcpd3.  The dhcpd config is set to have all hosts go to a dns server (this server has false entries to block specific sites)  dhcpd.conf has static entries for certain machines that tell them to use the proper dns servers for unrestricted access.  The static entries are for 2 vista machines (1 is 32bit home premium) and 2 8.04.1 desktops.  One machine is having an issue where sometimes it registers using the proper dns servers for unrestricted access, but sometimes it gets the restricted dns server.  The machine in question is an ASUS G50v laptop running vista ultimate 64bit on wireless N.  every other machine doesn't have this issue.  What could be wrong?  Thanks

---

### Post by Keymaster on 2008-11-05
Update: The other Vista computer (Vista Home Premium 32bit) also has this issue.  I'd really like to get this issue sorted soon.  Thanks

---

### Post by jimcooncat on 2008-11-06
You should post your dhcpd config so we can check to be sure it's set up for what you want to do.

I don't recall what Vista has for tools, but other Windows versions have ipconfig, similar to ifconfig on Linux. Posting the output of that when it gets the bad dns might be helpful too.

And are you sure (really sure) you don't have another dhcp server running on your subnet? That's messed me up a few times when I've forgotten about a Linksys box.

---

### Post by Keymaster on 2008-11-06
This is my network setup:
Ubuntu Router (running dhcpd shorewall and ssh server)
ISA Firewall (win2k3) running a dns server (this is the dns to be used by default)
The concept is any machines on my network that don't have a static IP in dhcpd.conf use the ISA IP as a dns server, and router, but my static entries have their own DNS option to use the ISPs DNS Servers.  Basically every one of my computers use the main router, but guest laptops (ie: house guests) use the ISA server as dns, and router to prevent them from using torrent sites, limewire, myspace etc while staying with us.  Only vista machines seem to be affected by this configuration.  They always get the correct gateway, but sometimes they get the default dns server, and sometimes they get the ISP dns servers I specified for them.

Config:
```

server-identifier router;
authoritative;

option time-offset -18000;

# Primary DHCP
subnet 172.25.0.0 netmask 255.255.255.0 {
	option netbios-name-servers 172.25.0.3;
	authoritative;
	option routers 172.25.0.3;
        option domain-name-servers 172.25.0.3;
	option subnet-mask 255.255.255.0;
	option broadcast-address 172.25.0.255;
	range dynamic-bootp 172.25.0.101 172.25.0.200;
	default-lease-time 43200;
	max-lease-time 43200;
	}

# Family Computer
host billybob {
	option routers 172.25.0.1;
	option domain-name-servers 167.206.254.1, 167.206.254.2, 167.206.7.3, 167.206.1.30, 167.206.1.103, 167.206.112.3, 167.206.112.4, 167.206.112.138, 167.206.7.4;
	hardware ethernet ##:##:##:##:##:##;
	fixed-address 172.25.0.20;	}
#  brother laptop (Wireless)
host sephiroth {
	option routers 172.25.0.1;
	option domain-name-servers 167.206.254.1, 167.206.254.2, 167.206.7.3, 167.206.1.30, 167.206.1.103, 167.206.112.3, 167.206.112.4, 167.206.112.138, 167.206.7.4;
	hardware ethernet ##:##:##:##:##:##;
	fixed-address 172.25.0.21;
	}
# Nintendo Wii Console (Wireless)
host Wii {
	option routers 172.25.0.1;
	option domain-name-servers 167.206.254.1, 167.206.254.2, 167.206.7.3, 167.206.1.30, 167.206.1.103, 167.206.112.3, 167.206.112.4, 167.206.112.138, 167.206.7.4;
	hardware ethernet ##:##:##:##:##:##;
	fixed-address 172.25.0.22;
	}
# XBox 360
host xbox360 {
	option routers 172.25.0.1;
	option domain-name-servers 167.206.254.1, 167.206.254.2, 167.206.7.3, 167.206.1.30, 167.206.1.103, 167.206.112.3, 167.206.112.4, 167.206.112.138, 167.206.7.4;
	hardware ethernet ##:##:##:##:##:##;
	fixed-address 172.25.0.23;
	}
# My Laptop (Wireless)
host keymaster {
	option routers 172.25.0.1;
        option domain-name-servers 167.206.254.1, 167.206.254.2, 167.206.7.3, 167.206.1.30, 167.206.1.103, 167.206.112.3, 167.206.112.4, 167.206.112.138, 167.206.7.4;
	hardware ethernet ##:##:##:##:##:##;
	fixed-address 172.25.0.24;
	}

```

If anyone can help me get vista working off the correct dns each time, I'd greatly appreciate it, and may even provide some free web hosting if I can afford to ;)

PS: The MACs are blocked out (##:##:##:##:##:##) just because I will be providing web hosting to several people, and they will have access to my network via VPN, and I don't need them knowing too much. (Yes I am paranoid)

---

### Post by superprash2003 on 2008-11-06
cant you use static ips.. and manually issue the DNS for the vista machine.

---

### Post by Keymaster on 2008-11-06
I would but the two vista nodes are laptops, and travel all over the country sometimes.  The primary users of the laptops are not very computer savvy, and would never figure out how to adjust the IP settings when they leave my network for a public wifi (ie: airport terminal)  There has to be a way to do it via dhcpd.  Only vista has a problem with it.  The video game consoles, and the ubuntu, and XP machines have no issues with this.

---

### Post by Keymaster on 2008-11-07
I found a temporary solution.  I am using Win2k3 server DHCP on my network for the time being, but if anyone can figure out what is causing this please, let me know.  I'm leaving the thread as unsolved. (because it is)

---

