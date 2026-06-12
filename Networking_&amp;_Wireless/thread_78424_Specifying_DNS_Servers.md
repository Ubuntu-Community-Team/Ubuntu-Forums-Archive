---
title: "Specifying DNS Servers"
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by orev on 2005-10-18
My ISP sends out incorrect DNS server addresses, and when using Hoary I was able to use the process below to make the DNS servers not change from my settings in the networking gui.

> One way to do it without reconfiguring DHCP server is to disable resolv.conf rewrite. dhclient3 runs script /etc/dhcp3/dhclient-script after obtaining a lease. One of the things script does is modification to resolv.conf. You could simply comment out this part of code:
- open /etc/dhcp3/dhclient-script in your favorite editor (as root)

- find 2 occurences of "make_resolv_conf" and comment them out. WARNING!!! the first "make_resolv_conf() {" in the beginning of the file is the actual procedure definition. Leave it alone. There are 2 calls to this procedure on lines 194 and 243.
Add # in front of them so they read "# make_resolv_conf"
- save the file

However, when I tried this approach in Breezy, my networking did not work for some reason.

I would like to specify the DNS servers so they do not change, as they continue to reset to incorrect addresses every 20-30 minutes.

I took a look @ the /etc/network/interfaces file, but I do not really understand what changes to make here, and if they would help.

10000 thanks.

---

### Post by adwait on 2005-10-18
Try installing resolvconf
```
sudo apt-get install resolvconf
```
Enter the correct DNS servers at /etc/resolvconf/resolv.conf.d/original

---

### Post by Skid on 2005-10-18
Or editing /etc/resolv.conf and making it read-only?

---

### Post by mlomker on 2005-10-18
> Try installing resolvconf

I agree.  You can specify the settings in your /etc/network/interfaces file like this:

```

iface eth0 inet static
  dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
  dns-search whatever.com 

```

---

### Post by fheinsen on 2005-10-18
Hi -- I've had the same DNS problem with cheap routers when using DHCP.  These two solutions work for me:
 
1. Go to Applications -> Accesories -> Terminal and type "sudo install resolvconf pump dnsmasq" (see [http://www.ubuntuforums.org/showthread.php?t=5690]("http://www.ubuntuforums.org/showthread.php?t=5690"))

2. Follow the instructions here: [https://wiki.ubuntu.com/StaticDnsWit...ight=%28dns%29]("https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28dns%29")

---

