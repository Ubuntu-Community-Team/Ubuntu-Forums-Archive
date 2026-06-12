---
title: "Can I use resolv.conf to direct traffic to an internal ip address?"
date: 2017-09-03
forum: Networking &amp; Wireless
---

### Post by Robert_Boutin on 2017-09-03
Hi, I have a machine running Ubuntu 16.04 virtual servers with a block of static public ip addresses.  I am running a web server (192.168.1.110), and email server (192.168.1.111), a cloud server (192.168.1.112), and an OpenVPN server (192.168.1.135).

When I connect to my network through my OpenVPN client, I am unable to connect to mail.mydomain.com or share.mydomain.com (my cloud server).  I connect fine when I am not connected to the VPN.  My understanding is this is a NAT loopback issue and I'm not sure I want to risk breaking my router config trying to fix it.

I was told I could set up a "split horizon" DNS server that would consider the source of a DNS request and return an internal ip address if the address came from within my network.  In theory this should solve my problem but this is another area where I worry my skills aren't where they need to be to implement.

My question is, since my only problem is reaching servers on my internal network while connected to the VPN, can I use resolv.conf (or some other appropriate file) to direct traffic to the few internal devices I need to connect to?  Specifically, when I am connected to my VPN, I want:

mydomain.com connects to 192.168.1.110 without exiting my network
mail.mydomain.com connects to 192.168.111 without exiting
share.mydomain.com connects to 192.168.1.112 without exiting

Is it possible to do this?  Thanks as always.

---

### Post by SeijiSensei on 2017-09-03
I use a private DNS server on my local network to resolve names within that network.  While there are ways to set up "views" in BIND, I've found using a separate server is just as easy if not easier.

---

### Post by Mobile Data Solutions on 2018-01-04
> **Robert_Boutin said:**
> When I connect to my network through my OpenVPN client, I am unable to connect to mail.mydomain.com or share.mydomain.com (my cloud server).  I connect fine when I am not connected to the VPN.  My understanding is this is a NAT loopback issue and I'm not sure I want to risk breaking my router config trying to fix it.

I was told I could set up a "split horizon" DNS server that would consider the source of a DNS request and return an internal ip address if the address came from within my network.  In theory this should solve my problem but this is another area where I worry my skills aren't where they need to be to implement.

My question is, since my only problem is reaching servers on my internal network while connected to the VPN, can I use resolv.conf (or some other appropriate file) to direct traffic to the few internal devices I need to connect to?  Specifically, when I am connected to my VPN, I want:

Sounds as if your VPN connection is bypassing your local DNS resolution. Presuming the local DNS resolution occurs at a gateway router, this is normal. Your VPN connection is getting passed straight-thru your local router because when you connect to a VPN, from a practical perspective you are connecting to a local gateway host. You are then effectively asking the VPN's gateway router to perform the FQDN resolution. Since it doesn't see your local servers (they are not local to it), your attempt fails.

When you turn off the VPN, you are getting routed to the local gateway router for DNS resolution, and it works.

In a typical configuration, OpenVPN is able to manipulate the list of servers for DNS resolution while you're connected to the VPN. Even if you create a server to act as a local DNS resolver, by the time your connection gets to the DNS server list, you are on the VPN and so that approach still won't work. You have to intercept the DNS request prior to the VPN connection if you want your connection redirected to the local server.

To solve:

Disconnect from your VPN. Verify you can connect to your local servers, and run

```
cat /etc/resolv.conf
```

Look at the last line. It should be something like

```
search <local route name>
```

e.g., ```
search local
```

Something with "search" at the beginning of the line is what you are looking for.

Presuming that is the case:

1. Examine your /etc/openvpn/openvpn.conf file

2. Presuming you have a standard OpenVPN client installation, there should be two lines at or near the bottom like this:

```
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf
```

3. Open up /etc/openvpn/update-resolv-conf for editing

```
nano /etc/openvpn/update-resolv-conf
```

4. Find this section:

[HTML]#
     foreign_option_1='dhcp_option DNS <dns server ipv4>'
     foreign_option_2='dhcp_option DNS <dns server ipv4>'
     foreign_option_3='dhcp_option DNS <dns server ipv4>'
#[/HTML]

Yours may look a bit different.

You want to add another line. You want the last of those option lines to be a search instruction to your local DNS server. That could be a dedicated server or your gateway router. Like this:

```
....
     foreign_option_3='dhcp_option DNS <dns server ipv4>'
     foreign_option_4='dhcp_option DOMAIN <FQDN of local DNS resolving server>'
#

```

Make sure you increment the number so each line has a unique "foreign_option_<value>".

After the word "DOMAIN" type what you saw in your resolv.conf output when you were not connected to the VPN. If what you saw was "local", you can try that here but when you test it may not work. If it doesn't, repeat this process (after testing) and change the name after "DOMAIN" to the root name of FQDN or your local DNS resolver. For example, if your FQDN of the DNS resolver is "mydnsresolver.company-name" then here you'd type "DOMAIN company-name" in the appropriate position in the file as described above. I hope that's clear. The point is you want to tell OpenVPN's resolver where to search for the local server.

Now, stop and restart OpenVPN or (preferably, to be sure) reboot your server and try it again. You should now be able to connect to a local server when your VPN is up.

---

