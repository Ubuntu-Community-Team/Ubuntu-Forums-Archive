---
title: "dnsmasq and host file"
date: 2015-11-10
forum: Networking &amp; Wireless
---

### Post by ngms27 on 2015-11-10
I'm running Mate 15.10 on a Raspberry Pi 2 and wish to use the Pi as a Ad Blocker. To date I've got everything working other than dnsmasq wont read /etc/host or another file I give it.

Is there a way to make dnsmasq pick up an hosts file? This is running via Network Manager. I've tried various tweaks through google but none seem to work

---

### Post by SeijiSensei on 2015-11-10
I don't think dnsmasq uses the hosts file at all; it's basically a proxy to your DNS servers.

The standard /etc/nsswitch.conf file has this line
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns
```
which looks at /etc/hosts ("files") ahead of DNS resolution.  Is that what you have?

---

### Post by ngms27 on 2015-11-11
This is indeed the configuration but it doesn't ever read anything from /etc/hosts

dnsmasq is running with the no-hosts switch and it seems to be hard coded

---

### Post by SeijiSensei on 2015-11-11
That's pretty weird.  On this 14.04 Kubuntu machine, I see dnsmasq running with  "no-hosts," too.  I ran a test by adding an arbitrary hostname to /etc/hosts that points to a server I maintain. Even though dnsmasq has "no-hosts" enabled, I can still ping the address with the name I added.

I do make one customization to resolvconf.  I edit /etc/resolvconf/resolv.conf.d/head to add a couple of my own nameservers and a domain search directive:  
```

nameserver 10.10.10.10
nameserver 10.10.10.11
search example.com

```
All these lines then appear ahead of the default entry for 127.0.1.1.  I don't know why that would affect whether /etc/hosts is consulted though.

One piece I read talked about defeating the no-hosts option in Ubuntu 12.04: [http://askubuntu.com/questions/117899/configure-networkmanagers-dnsmasq-to-use-etc-hosts](http://askubuntu.com/questions/117899/configure-networkmanagers-dnsmasq-to-use-etc-hosts)
You might take a look at the solutions there.

---

### Post by Lars Noodén on 2015-11-11
> **ngms27 said:**
> This is indeed the configuration but it doesn't ever read anything from /etc/hosts

dnsmasq is running with the no-hosts switch and it seems to be hard coded

Where / how is it getting launched?

What about the -H or --addn-hosts=<file> option?   Can that be added?

---

### Post by papibe on 2015-11-11
Hi ngms27

Could you post your dnsmasq config files? The main /etc/dnsmasq.conf and anything in /etc/dnsmasq.d

BTW, you can block sites directly on the config files. For instance, to block Facebook:
```
# Block Facebook
address=/facebook.com/127.0.0.1
```
or
```
# Block Facebook
address=/facebook.com/0.0.0.0
```
Regards.

---

### Post by Lars Noodén on 2015-11-11
> **papibe said:**
> The main /etc/dnsmasq.conf and anything in /etc/dnsmasq.d

Or look in /var/run/NetworkManager/dnsmasq.conf and /etc/NetworkManager/dnsmasq.d

---

### Post by papibe on 2015-11-11
> **Lars Noodén said:**
> Or look in /var/run/NetworkManager/dnsmasq.conf and /etc/NetworkManager/dnsmasq.d
Ohh! good point Lars.

I'm not sure if the default NetworkManager plugin for DNSMasq would do what the OP wants. As I understand it, you wound need to install the proper dnsmasq package (the examples I gave are for the dnsmasq package).

Regards.

---

