---
title: "Can't connect network"
date: 2014-04-08
forum: Networking &amp; Wireless
---

### Post by satimis on 2014-04-08
Hi all,

Ubuntu 12.04 64bit

Cable connection - (FTTH) Fibre Optic Network
ISP -> PC

/etc/network/interfaces```

    auto lo
    iface lo inet loopback

    # The primary network interface
    auto eth0
    iface eth0 inet static
         address xxx.xxx.xxx.xxx
         dns-nameservers xxx.xxx.xxx.xxx
         dns-nameservers xxx.xxx.xxx.xxx
         netmask xxx.xxx.xxx.xxx
         broadcast xxx.xxx.xxx.xxx
         gateway xxx.xxx.xxx.xxx

```

Unable to connect network

I must delete```

dns-nameservers xxx.xxx.xxx.xxx
dns-nameservers xxx.xxx.xxx.xxx

```

and put them on /etc/resolv.conf

Then I can connect network and browse Internt.  But on reboot /etc/resolve.conf is rewritten deleting all content.

Please advise how to fix the problem?  Thanks

Rgds
satimis

---

### Post by steeldriver on 2014-04-08
Is this a desktop (with GUI) or true server (CLI)?

What appears in the /etc/resolv.conf file when it gets overwritten (your chosen DNS servers? other DNS server(s)? only the loopback IP?)

---

### Post by satimis on 2014-04-08
> **steeldriver said:**
> Is this a desktop (with GUI) or true server (CLI)?

desktop

> 
What appears in the /etc/resolv.conf file when it gets overwritten (your chosen DNS servers? other DNS server(s)? only the loopback IP?)
Only an empty file.

I used ISP's DNS 

Thanks

Rgds
satimis

---

### Post by steeldriver on 2014-04-08
If you are using a desktop installation I'd generally recommend setting your network using the GUI network-manager instead of via /etc/network/interfaces (the two services don't always 'play nice' together)

[ATTACH=CONFIG]251827[/ATTACH]

However if you want to proceed with your way, the 2 first things I'd try are:

 1. TBH I'm not 100% sure that multiple dns-nameservers lines are allowed (I've never tried it) - you might want to try putting both nameserver IPs on one line (separated by whitespace)

```

dns-nameservers xxx.xxx.xxx.xxx  yyy.yyy.yyy.yyy

```


2. reconfiguring the resolvconf service

```
sudo dpkg-reconfigure resolvconf
```

It will present you with a question about preparing /etc/resolv.conf for  dynamic  updates - answer "Yes". It may also present you with another  question about temporarily appending your  existing config to the  dynamic one - I suggest answering "No" to that one.

---

### Post by satimis on 2014-04-08
> **steeldriver said:**
> If you are using a desktop installation I'd generally recommend setting your network using the GUI network-manager instead of via /etc/network/interfaces (the two services don't always 'play nice' together)

[ATTACH=CONFIG]251827[/ATTACH]

However if you want to proceed with your way, the 2 first things I'd try are:

 1. TBH I'm not 100% sure that multiple dns-nameservers lines are allowed (I've never tried it) - you might want to try putting both nameserver IPs on one line (separated by whitespace)

```

dns-nameservers xxx.xxx.xxx.xxx  yyy.yyy.yyy.yyy

```


It works for me.  Thanks

Rgds
satimis

---

