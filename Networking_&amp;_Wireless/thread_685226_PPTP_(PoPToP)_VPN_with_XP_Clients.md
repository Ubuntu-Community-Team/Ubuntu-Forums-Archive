---
title: "PPTP (PoPToP) VPN with XP Clients"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by Audiosears on 2008-02-02
Hey all, hope someone out there can give me a pointer or two - I've gone over plenty of material online, but must be missing something somewhere...

Trying to run PoPToP via Gutsy 7.10 server using the MS VPN client that comes with XP to connect remotely.  The LAN runs on DHCP on 192.168.1.1 on a D-Link DGL-4300 gateway that is forwarding port 1723 to the server, 192.168.1.9.  It also has PPTP pass-through for the GRE protocol turned on.

I have DNS servers running on 192.168.1.9-10, and the gateway will also auto-specify 192.168.1.10, as well as one of our ISP's DNS servers on a public IP.  192.168.1.10 is our authoritative nameserver, but will only resolve our domain's entries for non-local IP's.  That DNS server maps our public IP of 64.246.146.34 to the LAN, and I have a subdomain set up for it to map to that IP.

On the server side, I have 192.168.1.9 as the only local address specified (I might also add that the Gutsy server is also running Samba and is our master browser), and clients get 192.168.1.175-199, which is outside our DHCP range of 192.168.1.20-100.  I am also using MS-CHAPv2, requiring authentication, MPPE and encrypted passwords.

On the client side, I have tried a wide range of options, but the default options seem to work best.  So far I have noticed the following:

- using a network OTHER than 192.168.1.x had no effect compared to being on the same subnet.

- No difference trying to connect from inside the LAN or outside.

Any Thoughts?  Any help or suggestions are always welcome, and thanks in advance!

---

### Post by Audiosears on 2008-02-02
HAHA!  I did in fact get it working (to a point).  The missing links were in manual TCP/IP definitions for the connection.  By manually specifying the DNS server, WINS server (also the Gutsy server), Gateway address, and unchecking the 'use default gateway on remote network', I connected and can now at least manipulate the Samba shares on the server as normal.  I can also browse the network fine, but cannot access or see shares on the other machines, although I can see the machines themselves.

I also still have the issue of the lag between logging out and not being able to connect again for about 15 mins.  I have yet to try multiple connections at once, but this is still a breakthrough...

Any thoughts on my remaining issues?

---

### Post by Audiosears on 2008-02-11
<bump>

Still having same issues, but after reading other posts, starting up a WINS server DOES INDEED actually make the connection not only fast, but reliable as well.

I can still see networked machines on the company LAN, but not their shared devices or mappings.  Also, there is the issue of not being able to reconnect to the VPN for about 10-15 mins after disconnecting.

---

### Post by 1jackjack on 2008-03-17
I have setup a pptpd vpn server on my ubuntu box at home, and from vista on my laptop, out of the house, can connect to it, and access files on the server, but not on any of the other computers on the network...
 
Did you ever resolve this?

Thanks,
Jack

---

### Post by farahbod on 2008-03-24
Audiosears:
Did you check your firewall rules?


1jackjack:
It seems you have routing problems or firewall blocks traffic.

---

### Post by jcostom on 2008-03-24
Check:

1. IP Forwarding.  Look in /etc/sysctl.conf for more info.

2. Proxy arp for IP addrs assigned.  Be sure the ppp options file referenced by the pptpd.conf file includes the "proxyarp" directive.

---

### Post by Audiosears on 2008-03-24
No firewall rule problems on the Ubuntu box, but not sure about IP forwarding - Will check on that...

---

### Post by drewrockshard on 2008-04-21
Guys,

I had this problem myself.  I enabled the IP Forwarding in sysctl.conf, and that did the trick.

Regards,
Drew

---

