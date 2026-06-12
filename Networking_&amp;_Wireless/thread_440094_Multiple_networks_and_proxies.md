---
title: "Multiple networks and proxies"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by wolf08 on 2007-05-11
I have a question related to proxy settings.

My setup is as follows:

A "Home" network, that has no proxy and has dhcp for an IP address.
A "School" network that has a squid proxy (with authentication) that uses dhcp, and ascii wep encryption (Soon it will be wpa). This school network also uses mac authentication (I can't get on unless I have  a preregistered mac address).

I would like for the gnome proxy to be automatically set when I connect to the school network, and deselected when I connect to my home (or any other) network. Is there any way to do this? Any way to do it through a gui? Thanks in advance!

A no gui solution is fine for me (I run gentoo servers, and am fluent in many command line operations), but other ubuntu users at my school would like to use the same solution (and they are very gui oriented). Therefore, if at all possible, either a gui solution or a command line solution that does not require dropping into a shell every time I want to switch networks would be awesome.

---

### Post by docsmooth on 2007-05-11
there are "post-up" and "pre-down" options in /etc/network/interfaces which runs a script after brining a network up.  If I were doing this, I'd write a small bash script to detect the network connected, then configure proxy accordingly.  Then use the pre-down to unconfigure any proxy set.  It's not elegant, but you can easily distribute the script and a patch for /etc/network/interfaces

/etc/network/interfaces:
auto eth1
iface eth1 inet dhcp
post-up /opt/proxy-script/setproxy.sh
pre-down /opt/proxy-script/unsetproxy.sh

/opt/proxy-script/setproxy.sh - something like:
if [ $(iwconfig eth1 |grep -o school-essid) ]; then
 i don't know how to set the proxy here, sorry
fi

Doc SmooTH

---

### Post by wolf08 on 2007-05-11
> **docsmooth said:**
> there are "post-up" and "pre-down" options in /etc/network/interfaces which runs a script after brining a network up.  If I were doing this, I'd write a small bash script to detect the network connected, then configure proxy accordingly.  Then use the pre-down to unconfigure any proxy set.  It's not elegant, but you can easily distribute the script and a patch for /etc/network/interfaces

/etc/network/interfaces:
auto eth1
iface eth1 inet dhcp
post-up /opt/proxy-script/setproxy.sh
pre-down /opt/proxy-script/unsetproxy.sh

/opt/proxy-script/setproxy.sh - something like:
if [ $(iwconfig eth1 |grep -o school-essid) ]; then
 i don't know how to set the proxy here, sorry
fi

Doc SmooTH

Good idea! I'm unsure about setting the proxy as well.... 

export http_proxy="proxy_info" doesn't seem to work globally.... Gah!

---

