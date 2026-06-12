---
title: "trouble with squid-deb-proxy-client on new install 16.04"
date: 2016-08-02
forum: Networking &amp; Wireless
---

### Post by wildwood on 2016-08-02
I am doing a series of upgrades to get all our systems here onto 16.04 and want to use a proxy to reduce usage of our limited bandwidth connection for this process. I've set up a squid-deb-proxy, which works perfectly with my 14.04 machine, but when I try with the newly installed 16.04 system it ignores the proxy and fetches direct everything, UNLESS I first start a Wireshark(1) capture on the ethernet port! then everything works fine :)

If I run /usr/share/squid-deb-proxy-client/apt-avahi-discover from terminal it returns nothing, but I note that if I run wireshark(2) on another machine the request is sent and an answer is given. The request and answer are the same before and during the wireshark(1) capture on the problem machine, but after starting it the apt-avahi-discover starts working and returning the proxy server correctly. It continues to work for about a minute after I stop that wireshark(1) and then I start to get errors in terminal, and the other wireshark(2) starts showing different messages too.

I tried setting the SQUID_DEB_PROXY_CLIENT_DEBUG environment variable to stop suppression of avahi logging to syslog, but no syslog output appears.

these are the wireshark(2) output as screenshots:
1: before starting wireshark(1)
[ATTACH=CONFIG]270541[/ATTACH]
2: after starting wireshark(1)
[ATTACH=CONFIG]270539[/ATTACH]
3: after stopping wireshark(1)
[ATTACH=CONFIG]270540[/ATTACH]

the error given is:
Failed to resolve service 'Squid deb proxy on raspberrypi' of type '_apt_proxy._tcp' in domain 'local': Timeout reached

it appears that the packets meant to be caught by avahi in the client machine are not being seen unless wireshark is running, since they are being sent but the client acting as if not. I checked, and they do contain the relevant information (port, IPv6, IPv4) for the requested service.

My next play is to try using a wifi hub to see if I can see all the packets when it's not working - currently I only see the broadcast packets due to ethernet switching, and when I start wireshark(1) on the client it stops not working ;)

***** SOLUTION FOUND *****

The issue is with a cheap no-brand USB-Ethernet adapter got from ebay. When using a different (less cheap) one (the one that is usually used with this laptop since it's internal ethernet failed) everything is working fine. I can only assume the cheap adapter is incorrectly ignoring broadcast packets unless it is in promiscuous mode for wireshark(1).

---

