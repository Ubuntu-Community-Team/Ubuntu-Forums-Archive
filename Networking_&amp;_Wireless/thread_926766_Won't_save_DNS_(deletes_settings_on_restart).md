---
title: "Won't save DNS (deletes settings on restart)"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by MatthewHSE on 2008-09-22
For some reason, Ubuntu won't save my DNS settings permanently.  Every time I restart the computer, the DNS gets deleted and I have to add them again before I can go online.

I've searched the forums and found that several other people have had this problem, but the standard solution seems to be to use a static IP, and disable DHCP on the router.  Both of which were part of my original setup that I've been using for years (and have verified now).

What else can I check to get the computer to remember my DNS settings?

Thanks,

Matthew

---

### Post by NoReflex on 2008-09-22
I guess you can create a simple script that just echoes "nameserver..." to /etc/resolv.conf. But why would you want to override your DNS settings - since you are setting them on your router they should be correct.

Best wishes,
NoReflex

---

### Post by kpatz on 2008-09-22
Do you mean your DNS servers, as listed in /etc/resolv.conf?

Add these lines to your /etc/dhcp3/dhclient.conf:

```

supersede domain-name "your_domain_name_here";
supersede domain-name-servers primary_DNS_server_IP_address_here
supersede domain-name-servers secondary_DNS_server_IP_address_here

```

Example:

```

supersede domain-name "foobar.com";
supersede domain-name-servers 192.168.10.1;
supersede domain-name-servers 192.168.10.2;

```

Now, when your DHCP client renews, it will put your desired DNS entries into /etc/resolv.conf, instead of the ones returned by the DHCP server.

---

### Post by MatthewHSE on 2008-09-22
> But why would you want to override your DNS settings - since you are setting them on your router they should be correct.They're not set on the router - I have to set them on every computer individually. The trouble is that Ubuntu keeps deleting the nameservers, and thus can't get online.  My Windows boxes don't do this.

> ```
supersede domain-name "your_domain_name_here";
supersede domain-name-servers primary_DNS_server_IP_address_here
supersede domain-name-servers secondary_DNS_server_IP_address_here
```I'm on a network without a domain - will this still work, or will the domain line have to be changed/removed?

---

### Post by superprash2003 on 2008-09-22
hope this helps [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) ..opendns servers 208.67.222.222 and 208.67.220.220 are used here

---

### Post by kpatz on 2008-09-22
> **MatthewHSE said:**
> I'm on a network without a domain - will this still work, or will the domain line have to be changed/removed?You can leave off the domain line.  Your ISP is assigning you a domain via DHCP anyway, and that isn't important if you aren't using it.

You just want to override the DNS servers.

---

### Post by Iowan on 2008-09-22
Some folks have had success by changing **/etc/dhcp3/dhclient.conf**:```
#prepend domain-name-servers 127.0.0.1;

``` Uncomment the line (delete the "#") and add your preferred servers. Another (optional) step is to delete "domain-name-servers," from the "request" line.

Another suggestion I remember was to change the DNS server list in the router.

---

