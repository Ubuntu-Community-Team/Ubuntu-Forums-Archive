---
title: "KVpnc"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by komyg on 2007-10-29
Hi I'm trying to use KVpnc to connect to a VPN network. 

If I had Windows I would use Checkpoint VPN1 client to connect to this network, but since I am using Kubuntu 7.04 I need another VPN client, so I am using KVnpc.

I think that  this network uses Microsoft pptp because it asks for username and password to connect, but I am not sure of that.

Still I cannot make KVpnc connect.

Anyone has a suggestion?

Thanks,
Komyg

---

### Post by Tex-Twil on 2008-03-14
Hello,
I'm also having some troubles with Kvpnc. If I try to connect via the command line to my openvpn server, it works but yhen I try KVPNC with the same configuration it fails. Sometimes I get this error:

> error: OpenvpnManagementHandler: Got no greeting within 3 seconds from management interface, retrying.

I have KVPNC v0.9.0 compiled from SVN

Any ideas ?
Tex

---

### Post by rgara on 2008-04-01
Exact same problem here. I can connect using the compiled openVPN software at the command line. I imported the conf file into KVpnc and when I try to connect I get:

info: Trying to connect to server "xx.xx.xxx.xxx" with ... 
debug: "openvpn" started.
error: OpenvpnManagementHandler: Got no greeting within 3 seconds from management interface, retrying.
info: Send private key password...
success: Successful connect try canceled.


And it never connects.

---

### Post by helmut_hed on 2008-06-09
Hi all,

I just discovered that if I change the name of my profile to something that does not include parentheses this problem goes away.  In other words, I had this:

XXX-YY(ZZ)

as my profile name.  When I changed it to this:

XXX-YY

everything was OK and the "Got no greeting within 3 seconds..." messages go away.

Jeff

---

