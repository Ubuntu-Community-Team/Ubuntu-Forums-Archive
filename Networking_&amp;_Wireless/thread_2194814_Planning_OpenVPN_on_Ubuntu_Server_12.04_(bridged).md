---
title: "Planning OpenVPN on Ubuntu Server 12.04 (bridged)"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by brad7 on 2013-12-20
I am in the planning stages of implementing OpenVPN server on my Ubuntu 12.04LTS server at home.

I’m been reading this how-to : [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

However I don’t know how this will work since I have bonded network interfaces.  I also have another nic that I can use just for openvpn bridge but don’t know how/if that would work.

here is my /etc/network/interface as it stands now (onboard nic eth 0 is disabled currently)

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet manual
        bond-master bond0

auto eth2
iface eth2 inet manual
        bond-master bond0

auto bond0
iface bond0 inet static
        bond-slaves none
        bond-mode balance-rr
        bond-miimon 100
        address 192.168.13.213
        netmask 255.255.255.0
        network 192.168.13.0
        broadcast 192.168.13.255
        gateway 192.168.13.1
        dns-nameservers 192.168.13.1

Any Thoughts?

---

### Post by TheFu on 2013-12-20
I would start with a simple configuration, get that working, then migrate to your more complex setup after everything non-bonded is working the way you like.

---

### Post by brad7 on 2013-12-20
Well the system is working perfectly ATM and I don't want to break anything.  Maybe I'll just do a VM.  Thanks for your advise!

Brad

---

