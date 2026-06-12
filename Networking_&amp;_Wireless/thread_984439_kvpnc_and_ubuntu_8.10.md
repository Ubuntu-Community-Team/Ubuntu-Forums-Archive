---
title: "kvpnc and ubuntu 8.10"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by mbeccaria on 2008-11-16
I am having troubles in continuing to use kvpnc to connect to my company's VPN
I have upgraded to ubuntu 8.10.
When using the existing kvpnc profile with the kvpnc 0.9.0 (the one in the official channel) I have the problem of the script-security (defaulted to 1, it does not allow to have hook scripts for DNS dynamic change).

I have tried with kvpnc 0.9.1rc2 but still unsuccessfull:
if I run it from my account, it stops and claims that it cannot open the tun/tap device due to a permission denied (13).
If I run it from root account, it claims that the /etc/resolv.conf is not a symbolic link and the DNS is not set.

Is there anybody in the forum that at the very end was able to use VPN (vs openvpn) using kvpnc ??

Any help would be appreciated

---

### Post by shanix on 2008-11-16
Have you tried vpnc-connect ?

---

### Post by mbeccaria on 2008-11-17
> **shanix said:**
> Have you tried vpnc-connect ?

My understanding is that I need a client for an OpenVPN server. vpnc-connect seems applicable to Cisco concentrator and not to openvpn server. Am I wrong ??

---

### Post by tpurch on 2009-01-16
> **mbeccaria said:**
> I am having troubles in continuing to use kvpnc to connect to my company's VPN
I have upgraded to ubuntu 8.10.
When using the existing kvpnc profile with the kvpnc 0.9.0 (the one in the official channel) I have the problem of the script-security (defaulted to 1, it does not allow to have hook scripts for DNS dynamic change).

I have tried with kvpnc 0.9.1rc2 but still unsuccessfull:
if I run it from my account, it stops and claims that it cannot open the tun/tap device due to a permission denied (13).
If I run it from root account, it claims that the /etc/resolv.conf is not a symbolic link and the DNS is not set.

Is there anybody in the forum that at the very end was able to use VPN (vs openvpn) using kvpnc ??

Any help would be appreciated

I had the same problem with /etc/resolv.conf error.  have you checked if /etc/resolv.conf is a symbolic link to /etc/resolvconf/run/resolv.conf.  if its not you need to delete your resolv.conf file in /etc and create a symbolic link.

---

