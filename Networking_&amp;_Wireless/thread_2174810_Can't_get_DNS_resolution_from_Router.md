---
title: "Can't get DNS resolution from Router"
date: 2013-09-16
forum: Networking &amp; Wireless
---

### Post by HuaiDan on 2013-09-16
Hello all,
I having a bit of trouble getting name resolution on the internet.
The trouble started after I upgraded from Precise to Quantal yesterday, x86_64 on both distros, currently using kernel 3.5.0-41generic.
My router is a Netgear wndr4000 running dd-wrt, configured to use dnsmasq and openDNS servers (208.67.222.222, 208.67.220.220).
I highly doubt the problem is with the router, as I have two wireless laptops, one running openSUSE 12.3 and the other running Windows 7, both able to surf without any issues. The only other difference here is that the Ubuntu machine is a direct ethernet connection.
I did not have this problem before upgrading to Quantal. The internal router IP is 10.0.0.1.
```
dh@dh-desktop:~$ nmcli dev list iface eth0 | grep IP4
IP4.ADDRESS[1]:                         ip = 10.0.0.3/24, gw = 10.0.0.1
IP4.DNS[1]:                             10.0.0.1

```
```
dh@dh-desktop:~$ ping xkcd.com
ping: unknown host xkcd.com
dh@dh-desktop:~$ ping google.com
ping: unknown host google.com

```
Of course, visiting these websites gives me a "Firefox can't find the server at ...." error.
I do get DNS resolution when I connect via VPN, which uses its own name service.

All other local network functionality is fine. I am able to use SMB service (by IP only) and connect to a NAS device.


I'm stumped. Everything looks fine, but this Ubuntu machine can't get name resolution fron the router.
Thanks for your ideas and suggestions!

P.S.
On the off chance that it was something related to the wired connection, I wired up the Suse laptop to the router on different IP than the wlan connects to, and got DNS. I even tried obscure webpages I never visit, just to make sure it wasn't pulling cached lookups. I'm really beginning to suspect something went afoul with the upgrade.

---

### Post by TheFu on 2013-09-16
Good start on the troubleshooting.  [This link]("http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking") might help (though probably not for you) ... if not you, others.

---

### Post by HuaiDan on 2013-09-16
Thanks, but there's really nothing there that I haven't already tried.
I remembered I had another network adaptor installed in the Ubuntu machine. I created an Auto-Eth1 connection to pull a dhcp address from the router, and then checked to see if it was using the gateway address as DNS, which it was. I got the same result: nothing.
All other devices are getting good name resolution.
I should add that all devices have reserved IP addresses by MAC address, all configured the same way, so no device is getting "special treatment" by the router.

---

### Post by TheFu on 2013-09-16
Yeah, I expected as much.  You've probably checked the MAC address in the DHCP reservation table 10 times already ...   I do the same thing for my portable devices, but for my servers - static IPs set in the **/etc/network/interfaces** file. Have you tried that? 

On to workarounds ... I mean, you are running beta software ... 
You can force a specific DNS server inside the interfaces file too, so if you can ping the DNS you want to use by IP, that should do it.  I'd point to an external DNS, not the internal one.  Of course, you've probably already tried this too. ;)
```

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
  address 192.168.1.20
  gateway 192.168.1.1
  netmask 255.255.255.0
  dns-nameservers 8.8.8.8
#  dns-nameservers 192.168.1.1
  dns-search external-fqdn.com internal-dn.lan
```

---

### Post by HuaiDan on 2013-09-17
> the /etc/network/interfaces file

No, I hadn't tried that. After removing my VPN app (Astrill) which I suspect might have had something to do with the break after the upgrade, it was still broken. I then edited the interfaces file per your lead, but as DHCP rather than static. This fixed the DNS resolution problem, even without a DNS address specified.
```
iface eth0 inet dhcp
```
Now it works, but I don't get any options or a graphical indication of connectivity in Network Manager.

Ideally I'd like to get it working through Network Manager before marking this thread as "solved". Let me try tweaking that this evening, re-creating the connections, re-installing, etc.
The problem does appear to be with Network Manager itself.

P.S.
It appears everything is working now as it should.
I commented out the line in the interfaces file (along with the loopback entry which I soon found out was a mistake), then deleted all connections in Network Manager. After I put the loopback entry back in and rebooted, NM automatically created a DHCP connection for me, which sends lookups to the router gateway address and forwards, I presume, to  the DNS I have listed there.

Thanks for all you help TheFu!

---

