---
title: "Assign IPv6 to Interfaces [Feisty]"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by Paris Heng on 2007-09-11
Dear all,

Question:
1.  It is the IPv6 enable in Feisty by **default**?
2.  If i want to use the IPv6, how i do the setting in the configuration files? /etc/network/interfaces

> auto eth0
iface eth0 **inet6**  static
	address ? ? ?
	netmask ? ? ?
	gateway ? ? ?

3. What is the correct way to set the IPv6 to the interfaces?


Please assist.
Ref: [http://ubuntuforums.org/showthread.php?p=3346018#post3346018]("http://ubuntuforums.org/showthread.php?p=3346018#post3346018")

---

### Post by noob12 on 2007-09-11
Yes it's enabled by default.  You might want to read **man interfaces**, particularly the section titled INET6 ADDRESS FAMILY, the static method.

---

### Post by Paris Heng on 2007-09-12
Hi,

Any Tutorial to learn to configure? Thank

---

### Post by noob12 on 2007-09-12
There is this large document [http://tldp.org/HOWTO/Linux+IPv6-HOWTO/](http://tldp.org/HOWTO/Linux+IPv6-HOWTO/) that starts from the basics.   

If you understand the basic concepts and have the address of your IPV6 router and your network information, you can type **man interfaces** you will get a manual page that describes how to use the **/etc/network/interfaces** file to set this up.  In that man page is a section on how to set up an interface statically for IPV6 (INET6).   

If you are not in a network that is already running IPV6 equipment, you probably want to stay with IPV4.

---

### Post by Paris Heng on 2007-09-14
Hi,

Thank for that link.

I trying to use ipv6 in the network configuration for my own home network, but the current ADSL are using ipv4, can the NAT (Network Address Translation) do the translation between the **ISP ipv4** to my design network which is **ipv6**?

> (ipv6) -------- (NAT) ---------- (ipv4)


Please assit

---

