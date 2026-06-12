---
title: "Proper Method to Manage DNS"
date: 2016-08-08
forum: Networking &amp; Wireless
---

### Post by feartheterrapin on 2016-08-08
I like to occasionally change my DNS.  While using Ubuntu 12.04 I had no issue manging DNS preferences through the Network Manager GUI under the IPv4 settings.  Back in May I updated my OS to Ubuntu-Mate 16.04.  I went along managing my DNS like I use to though the Network Manger GUI assuming changes were being made until one day when I visited ipleak.net and noticed any changes I made through Network Manger did not take.

NetworkManger.conf does not indicate any nameservers.  Doing command “$ nmcli -t -f IP4.DNS device show enp2s0” lists the nameservers configured via  Network Manger GUI.  However, ipleak.net indicates I am using the nameservers listed in my resolv.conf file.  Is the resolv.conf file the only way to manage my DNS?  What is the proper way to identify DNS of choice?

---

### Post by feartheterrapin on 2016-08-14
So I deleted resolv.conf, re-booted, and had no domain lookup service.  Network manager had a nameserver configured but was ignored.  I am still confused about the network manger settings.  Why does the ability to change nameservers exist in network manger if they are not usable.  What is the proper/recommended procedure to mange DNS?

---

### Post by feartheterrapin on 2016-08-25
Bump:  Is resolv.conf the only way to manage nameservers?

---

### Post by ventrical on 2016-09-15
I keep it rather simple. I know that this does not answer your question but it always works for me.

---

### Post by Keith_Helms on 2016-09-15
I believe you have to edit the connection(s) in the network manager gui and change them from "DHCP" to "DHCP Addresses Only".   That will allow the DHCP server to assign your system an IP address, but use the DNS servers you enter manually for that connection.

My understanding of resolv.conf is that it gets overwritten at boot time if you have dnsmasq installed, which it is by default.  That usually writes 127.0.0.1 (localhost) into resolv.conf, indicating that the dnsmasq caching DNS server is the first place the system will look for IP addresses.

---

### Post by feartheterrapin on 2016-09-19
> **Keith_Helms said:**
> I believe you have to edit the connection(s) in the network manager gui and change them from "DHCP" to "DHCP Addresses Only".   That will allow the DHCP server to assign your system an IP address, but use the DNS servers you enter manually for that connection.

My understanding of resolv.conf is that it gets overwritten at boot time if you have dnsmasq installed, which it is by default.  That usually writes 127.0.0.1 (localhost) into resolv.conf, indicating that the dnsmasq caching DNS server is the first place the system will look for IP addresses.

I did edit the connections in the network manager gui and confirmed "DHCP Addresses Only".  But the addresses in resolv.conf are the ones being used.  I changed resolv.conf to show "nameserver 127.0.0.1" and I loose DNS.

Going forward I have no issue managing my nameservers by editing resolv.conf, but I am still confused why my configuration does not work like others.  I suspect when I installed the Private Internet Access application, something changed.

---

### Post by Keith_Helms on 2016-09-21
What "Private Internet Access application" did you install?

---

### Post by feartheterrapin on 2016-09-21
> **Keith_Helms said:**
> What "Private Internet Access application" did you install?

Discussion [URL="https://www.privateinternetaccess.com/forum/discussion/1940/pia-vpn-app-linux-beta"]here
[/URL]I don't think it is still beta

Download [here]("https://www.privateinternetaccess.com/installer/download_installer_linux")

---

### Post by feartheterrapin on 2017-02-05
So I finally figured out my issue.  The Private Internet  Access app changes the etc/resolv.conf file to use their servers.  I  think there must have been an untidy shutdown leaving the   etc/resolv.conf file as a file and not a symbolic link.  Not knowing   etc/resolv.conf should be a symbolic link, I went on maintaining my DNS  by modifying  etc/resolv.conf until I learned about resolv.conf being a  symbolic link.

  By entering:

  ```
$ cd /etc
$ rm resolv.conf
$ sudo ln -s /run/resolvconf/resolv.conf
```

I was back as originally configured and able to manage my DNS through  the network manger.  PIA works just fine via both their app and  OPENVPN.

---

