---
title: "duplicate interface"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by dannemil on 2006-11-15
I'm trying to get a static ip connection set up. Each time I try sudo ifup eth0 <ip>, I get an error message

"duplicate interfaces" couldn't read interfaces file "/etc/network/interfaces"

My /etc/network/interfaces file has root permissions and it only has one connection defined for eth0.

Any help would be appreciated.

Jim

---

### Post by marekdef on 2006-11-15
My files look as this

# cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
ls -l /etc/network/interfaces
-rw-r--r-- 1 root root 238 2006-10-21 15:08 /etc/network/interfaces

ifdown eth1
ifup -v eth1
Configuring interface eth1=eth1 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

ifconfig eth1 192.168.0.1 netmask 255.255.255.0                 up

run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntp-server
run-parts: executing /etc/network/if-up.d/ntpdate
Synchronizing clock to ntp.ubuntu.com...

Try to use -v verbose flag,
and please compare your files with mines

---

### Post by dannemil on 2006-11-15
Thanks for the quick reply.

I tried sudo ifup -v eth0

and I still get the same error message. The permissions on the interfaces file are the same as yours with the exception of the root being rwx instead of just rw-

Also the verbose mode doesn't produce any other messages probably because it says it can't read the interfaces file and just stops.

When I do a ifconfig -a

the eth0 shows up with the correct ipaddress and netmask, but still no connectivity, and there is no gateway shown. I can't ping the gateway.

---

