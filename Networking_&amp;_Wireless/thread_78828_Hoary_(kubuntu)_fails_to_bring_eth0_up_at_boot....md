---
title: "Hoary (kubuntu) fails to bring eth0 up at boot..."
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by Manetola on 2005-10-19
Hi
just installed Hoary (Kubuntu) on a AMD Athlon 900...
everything just fine for the first couple of days, then system suddenly fails to activate network interface at boot...
going into "kcontrol" as root gives "eth0 down" (with a red cross sign) and any attempt to bring it up manually returns in seconds to a disabled ethernet interface..
the only thing that happened I could think of is that I installed the shorewall firewall (but that did not seem to create any problem at first) and changed the DNS servers in resolv.conf (also through kcontrol...)
any known issues about this?
thnks in advance...
manetola

p.s. by the way, great distro Ubuntu, but why not bundling a gui for configuring services, or a simple firewall configuration tool?

---

### Post by cts on 2005-11-08
5.04 hoary:
[COLOR="Blue"]sudo kcontrol [/COLOR]
 - no such command

we are gettint intermittant "network address conflicts"
I am inclined to blame our router (Belkin) & its DHCP
Question:
Is it true that DCHP Server anf LTSP server are** NOT** started by default???

[COLOR="Blue"]ps -e | grep dhcp
ps -e | grepc ltsp[/COLOR]

both show **nothing**, but I am worried that a conflicting** DHCP server **may be lurking in Hoary under some other name.....

---

