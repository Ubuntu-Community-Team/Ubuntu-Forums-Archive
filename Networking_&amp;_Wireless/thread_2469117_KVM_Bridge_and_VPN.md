---
title: "KVM Bridge and VPN"
date: 2021-11-20
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2021-11-20
This is related to another thread I have re setting up a KVM bridge - I do want to complicate (for me!) that thread as I'm in enough trouble as it is.  I currently use Surfshark VPN on my host machine and it works fine.  I'm having trouble with some sites (e.g. ebay.co.uk, google.co.uk) that at times object to me connecting via a vpn and lock me out of my account.  To get round this I have created an icon on my Desktop that closes the VPN connect and re-connects using the standard Ethernet i/f when I want to connect to these sites. My question is - if I get bridge working for my kvm machines/host machine will I still be able to use vpn as my outgoing connection?

---

### Post by TheFu on 2021-11-20
yes. It is possible.

---

### Post by Quarkrad on 2021-11-24
I'm now attempting to use a vpn connection having setup my bridge.  So far I haven't found a site that helps me to understand how to do this - however, I keep reading that for vpn configuration it is better to use Network Manager.  A few pages I've come across, that claim to cover bridge/vpn connectivity, don't go into any detail but repeat using Network Manager for vpn.  @TheFu has helped me set up a Bridge using Netplan but so far I have found very little on how to configure Netplan to use a Bridge and a vpn for its outgoing connection.  I thought it might be as easy as substituting my ethernet i/f eno1 in the netplan script for a vpn i/f - but I guess there needs to be another file somewhere that describes the vpn interface.  Any pointers much appreciated.  (My understanding is that on 20.04 one needs to use Netplan for this type of setup (kvm, host, bridge,vpn)).

---

### Post by TheFu on 2021-11-24
I don't use network-manager. Haven't since around 2011 when it cause issues on a non-trivial network. That includes for a simply laptop with 1 connection at a time (usually wired).

A VPN needs a working network BEFORE it can create a tunnel, so the bridge needs to be up and working first.  Then I just use a little openvpn script to bring up a connection to a paid VPN provider.  I don't run it all the time, but the vpn doesn't care if there is a bridge or non-bridge connection. It doesn't know. All it knows is that there is an interface name which it uses.
My script actually looks through /etc/openvpn/AES256/ for .ovpn files and picks one based on input.  Then it runs:
```
/usr/bin/sudo /usr/sbin/openvpn "$OVPN_DIR/$SEARCH" &
```
That would be 
```
/usr/bin/sudo /usr/sbin/openvpn  /etc/openvpn/AES256/us_silicon_valley.ovpn &
```
The .ovpn files were provided by the VPN service.  I added 1 line for convenience, 
```
auth-user-pass /etc/openvpn/login.cf
```
This way, the connection credentials aren't something I need to remember. Only root can access that file.
```
-rw-------   1 root root    21 May  4  2021 login.cf
```
My sudoers config allows running openvpn with an argument in that specific directly without a password, for my account. A few other things get the NOPASSWD option too.

By default, many VPNs provide only 128-bit AES, so setting up 256-bit was an extra effort. I also use a 4Kb cert, which they provided rather than the 2Kb cert.

I run my own VPNs to connect back here when I'm out and about.  Have both openvpn and wireguard setup.  For those connections, I have a dedicated VM with a dedicated NIC assigned through PCI passthru. I may move the VPN server into a container, but that is one of those - *it can be done, but it is probably a terrible idea* - things.
Lots of people put the VPN end-point on their routers.  I don't do that and consider having too much extra complex software running on routers a security failure.  Just because something "can" be done, that doesn't mean it is a good idea.
I would not run a _VPN server_ on my KVM host machine. Sure, it can be done, but I don't think it is smart. I do run a VPN client on a KVM host, from time to time. That host doesn't support any inbound services on the internet, only outbound stuff.

---

